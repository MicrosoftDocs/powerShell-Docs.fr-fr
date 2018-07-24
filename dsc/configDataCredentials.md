---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Options relatives aux informations d’identification dans les données de configuration
ms.openlocfilehash: 12bb8d8ce5fc4685e583e74d411b098320ac4fd4
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093675"
---
# <a name="credentials-options-in-configuration-data"></a>Options relatives aux informations d’identification dans les données de configuration
>S’applique à : Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Mots de passe en texte brut et utilisateurs de domaine

Les configurations DSC qui contiennent des informations d’identification non chiffrées génèrent un message d’erreur concernant les mots de passe en texte clair.
En outre, DSC génère un avertissement lorsque des informations d’identification de domaine sont utilisées.
Pour empêcher ces messages d’erreur et d’avertissement, utilisez les mots clés de données de configuration DSC :
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

> [!NOTE]
> Le stockage/la transmission des mots de passe en texte clair non chiffrés ne sont généralement pas sécurisés. Il est recommandé de sécuriser les informations d’identification à l’aide des techniques décrites plus loin dans cette rubrique.
> Le service Azure Automation DSC vous permet de centraliser la gestion des informations d’identification en les compilant dans des configurations et en les stockant en lieu sûr.
> Pour plus d’informations, consultez : [Compilation des Configurations DSC / Ressources d’informations d’identification](/azure/automation/automation-dsc-compile#credential-assets)

Voici un exemple de transmission d’informations d’identification en texte brut :

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
        @{
            # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="*"
            PSDscAllowPlainTextPassword = $true
        },
        #however, each node still needs to be explicitly defined for "*" to have meaning
        @{
            NodeName = "TestMachine1"
        },
        #we can also use a property to define node-specific passwords, although this is no more secure
        @{
            NodeName = "TestMachine2";
            UserName = "User2"
            LocalPassword = "ThisIsYetAnotherPlaintextPassword"
        }
        )
}
configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a>Gestion des informations d’identification dans DSC

Par défaut, les ressources de configuration DSC sont exécutées en tant que `Local System`.
Toutefois, certaines ressources nécessitent des informations d’identification, par exemple quand la ressource `Package` doit installer des logiciels sous un compte d’utilisateur spécifique.

Avant, les ressources utilisaient un nom de propriété `Credential` codé en dur pour gérer cette situation.
Avec WMF 5.0, la propriété `PsDscRunAsCredential` est ajoutée automatiquement à toutes les ressources.
Pour plus d’informations sur l’utilisation de `PsDscRunAsCredential`, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).
Les ressources récentes et les ressources personnalisées peuvent utiliser cette propriété automatique au lieu de créer leur propre propriété d’informations d’identification.

> [!NOTE]
> Certaines ressources sont conçues pour utiliser plusieurs informations d’identification pour une raison donnée et ont leurs propres propriétés d’informations d’identification.

Pour trouver les propriétés d’informations d’identification disponibles dans une ressource, utilisez `Get-DscResource -Name ResourceName -Syntax` ou Intellisense dans l’environnement ISE (`CTRL+SPACE`).

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Cet exemple utilise une ressource [Group](https://msdn.microsoft.com/powershell/dsc/groupresource) du module de ressource DSC `PSDesiredStateConfiguration` intégré.
Elle peut créer des groupes locaux et ajouter ou supprimer des membres.
Elle accepte à la fois la propriété `Credential` et la propriété automatique `PsDscRunAsCredential`.
Toutefois, la ressource utilise uniquement la propriété `Credential`.

Pour plus d’informations sur la propriété `PsDscRunAsCredential`, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Exemple : Propriété d’informations d’identification de la ressource Group

DSC s’exécute sous `Local System`. Il dispose donc déjà des autorisations pour modifier les utilisateurs et les groupes locaux.
Si le membre ajouté est un compte local, aucune information d’identification n’est nécessaire.
Si la ressource `Group` ajoute un compte de domaine au groupe local, des informations d’identification seront nécessaires.

Les requêtes anonymes envoyées à Active Directory ne sont pas autorisées.
La propriété `Credential` de la ressource `Group` correspond au compte de domaine utilisé pour interroger Active Directory.
Dans la majorité des cas, il peut s’agir d’un compte d’utilisateur générique, car par défaut, les utilisateurs peuvent *lire* la plupart des objets dans Active Directory.

## <a name="example-configuration"></a>Exemple de configuration

L’exemple de code suivant utilise DSC pour ajouter un utilisateur de domaine à un groupe local :

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

Ce code génère à la fois un message d’erreur et un message d’avertissement :

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

Cet exemple comprend deux problèmes :
1. L’erreur explique que les mots de passe en texte brut ne sont pas recommandés
2. L’avertissement recommande de ne pas utiliser d’informations d’identification de domaine

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

Le premier message d’erreur comprend une URL vers de la documentation.
Ce lien explique comment chiffrer des mots de passe avec une structure [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) et un certificat.
Pour plus d’informations sur les certificats et sur DSC, [lisez cet article de blog](http://aka.ms/certs4dsc).

Pour forcer un mot de passe en texte brut, la ressource nécessite que le mot clé `PsDscAllowPlainTextPassword` se trouve dans la section des données de configuration comme dans l’exemple suivant :

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

> [!NOTE]
> `NodeName` n’est pas équivalent à un astérisque et un nom de nœud doit être fourni obligatoirement.

**Microsoft recommande d’éviter les mots de passe en texte brut en raison de l’important risque de sécurité qu’ils présentent.**

## <a name="domain-credentials"></a>Informations d’identification de domaine

Si vous exécutez à nouveau l’exemple de script de configuration (avec ou sans chiffrement), vous obtiendrez toujours l’avertissement selon lequel l’utilisation d’informations d’identification de compte de domaine n’est pas recommandée.
L’utilisation d’un compte local élimine les risques d’exposition des informations d’identification de domaine qui pourraient être utilisées sur d’autres serveurs.

**Quand vous utilisez des informations d’identification avec des ressources DSC, préférez un compte local à un compte de domaine quand cela est possible.**

Si la propriété `Username` des informations d’identification comprend un « \' » ou un « @ », DSC la traite comme un compte de domaine.
Il existe une exception pour « localhost », « 127.0.0.1 » et « :: 1 » dans la partie du nom d’utilisateur consacrée au domaine.

## <a name="psdscallowdomainuser"></a>PsDscAllowDomainUser

Dans l’exemple de ressource `Group` DSC ci-dessus, le fait d’interroger un domaine Active Directory *nécessite* un compte de domaine.
Dans ce cas, ajoutez la propriété `PSDscAllowDomainUser` au bloc `ConfigurationData` comme suit :

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

Le script de configuration va maintenant générer le fichier MOF sans avertissement ni erreur.
