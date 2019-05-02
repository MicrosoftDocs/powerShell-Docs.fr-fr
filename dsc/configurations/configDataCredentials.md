---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Options relatives aux informations d’identification dans les données de configuration
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080150"
---
# <a name="credentials-options-in-configuration-data"></a>Options relatives aux informations d’identification dans les données de configuration

>S’applique à : Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Mots de passe en texte brut et utilisateurs de domaine

Les configurations DSC qui contiennent des informations d’identification non chiffrées génèrent un message d’erreur concernant les mots de passe en texte clair.
En outre, DSC génère un avertissement lorsque des informations d’identification de domaine sont utilisées.
Pour empêcher ces messages d’erreur et d’avertissement, utilisez les mots clés de données de configuration DSC :

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Le stockage/la transmission des mots de passe en texte clair non chiffrés ne sont généralement pas sécurisés. Il est recommandé de sécuriser les informations d’identification à l’aide des techniques décrites plus loin dans cette rubrique.
> Le service Azure Automation DSC vous permet de centraliser la gestion des informations d’identification en les compilant dans des configurations et en les stockant en lieu sûr.
> Pour plus d’informations, consultez : [Compilation des Configurations DSC / Ressources d’informations d’identification](/azure/automation/automation-dsc-compile#credential-assets)

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

Cet exemple utilise une ressource [Group](../resources/resources.md) du module de ressource DSC `PSDesiredStateConfiguration` intégré.
Elle peut créer des groupes locaux et ajouter ou supprimer des membres.
Elle accepte à la fois la propriété `Credential` et la propriété automatique `PsDscRunAsCredential`.
Toutefois, la ressource utilise uniquement la propriété `Credential`.

Pour plus d’informations sur la propriété `PsDscRunAsCredential`, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Exemple : propriété d’informations d’identification de la ressource Group

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
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

Cet exemple comprend deux problèmes :

1. L’erreur explique que les mots de passe en texte brut ne sont pas recommandés
2. L’avertissement recommande de ne pas utiliser d’informations d’identification de domaine

Les indicateurs **PSDSCAllowPlainTextPassword** et **PSDSCAllowDomainUser** suppriment l’erreur et l’avertissement informant l’utilisateur du risque encouru.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Le premier message d’erreur comprend une URL vers de la documentation.
Ce lien explique comment chiffrer des mots de passe avec une structure [ConfigurationData](./configData.md) et un certificat.
Pour plus d’informations sur les certificats et sur DSC, [lisez cet article de blog](http://aka.ms/certs4dsc).

Pour forcer un mot de passe en texte brut, la ressource nécessite que le mot clé `PsDscAllowPlainTextPassword` se trouve dans la section des données de configuration comme dans l’exemple suivant :

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
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

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

L’indicateur **PSDSCAllowPlainTextPassword** exige que l’utilisateur connaisse les risques liés au stockage de mots de passe en texte brut dans un fichier MOF. Dans le fichier MOF généré, même si un objet **PSCredential** contenant une valeur **SecureString** a été utilisé, les mots de passe continueront d’apparaître en tant que texte brut. C’est la seule fois où les informations d’identification sont exposées. Ce fichier MOF offre à tout le monde un accès au compte Administrateur.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Informations d’identification en transit et au repos

- L’indicateur **PSDscAllowPlainTextPassword** permet la compilation de fichiers MOF contenant les mots de passe en texte clair.
  Prenez des précautions lorsque vous stockez des fichiers MOF contenant des mots de passe de texte clair.
- Lorsque le fichier MOF est transmis à un nœud en mode **Push**, WinRM chiffre la communication pour protéger le mot de passe de texte en clair, sauf si vous remplacez la valeur par défaut par le paramètre **AllowUnencrypted**.
  - Le chiffrement du fichier MOF avec un certificat protège le fichier MOF au repos avant qu’il soit appliqué à un nœud.
- En mode **Pull**, vous pouvez configurer un serveur Pull Windows afin d’utiliser HTTPS pour chiffrer le trafic à l’aide du protocole spécifié dans Internet Information Server. Pour plus d’informations, consultez les articles [Configuration d’un client Pull DSC](../pull-server/pullclient.md) et [Sécurisation des fichiers MOF avec des certificats](../pull-server/secureMOF.md).
  - Dans le service [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview), le trafic Pull est toujours chiffré.
- Sur le nœud, les fichiers MOF sont chiffrés au repos à compter de PowerShell 5.0.
  - Dans PowerShell 4.0, les fichiers MOF ne sont pas chiffrés au repos, sauf s’ils sont chiffrés avec un certificat lorsqu’ils sont envoyés (Push) au nœud ou extraits (Pull) de celui-ci.

**Microsoft recommande d’éviter les mots de passe en texte brut en raison de l’important risque de sécurité qu’ils présentent.**

## <a name="domain-credentials"></a>Informations d’identification de domaine

Si vous exécutez à nouveau l’exemple de script de configuration (avec ou sans chiffrement), vous obtiendrez toujours l’avertissement selon lequel l’utilisation d’informations d’identification de compte de domaine n’est pas recommandée.
L’utilisation d’un compte local élimine les risques d’exposition des informations d’identification de domaine qui pourraient être utilisées sur d’autres serveurs.

**Quand vous utilisez des informations d’identification avec des ressources DSC, préférez un compte local à un compte de domaine quand cela est possible.**

Si la propriété `Username` des informations d’identification comprend un « \\ » ou un « \@ », DSC la traite comme un compte de domaine.
Il existe une exception pour « localhost », « 127.0.0.1 » et « :: 1 » dans la partie du nom d’utilisateur consacrée au domaine.

## <a name="psdscallowdomainuser"></a>PsDscAllowDomainUser

Dans l’exemple de ressource `Group` DSC ci-dessus, le fait d’interroger un domaine Active Directory *nécessite* un compte de domaine.
Dans ce cas, ajoutez la propriété `PSDscAllowDomainUser` au bloc `ConfigurationData` comme suit :

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Le script de configuration va maintenant générer le fichier MOF sans avertissement ni erreur.
