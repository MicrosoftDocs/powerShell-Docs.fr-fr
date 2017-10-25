---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Options relatives aux informations d’identification dans les données de configuration"
ms.openlocfilehash: ec4eeb8e519158b2bf929b949e381cdba54f8928
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2017
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="b8ff8-103">Options relatives aux informations d’identification dans les données de configuration</span><span class="sxs-lookup"><span data-stu-id="b8ff8-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="b8ff8-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b8ff8-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="b8ff8-105">Mots de passe en texte brut et utilisateurs de domaine</span><span class="sxs-lookup"><span data-stu-id="b8ff8-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="b8ff8-106">Les configurations DSC qui contiennent des informations d’identification non chiffrées génèrent un message d’erreur concernant les mots de passe en texte brut.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-106">DSC configurations containing a credential without encryption will generate an error messages about plain text passwords.</span></span>
<span data-ttu-id="b8ff8-107">En outre, DSC génère un avertissement lorsque des informations d’identification de domaine sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="b8ff8-108">Pour empêcher ces messages d’erreur et d’avertissement, utilisez les mots clés de données de configuration DSC :</span><span class="sxs-lookup"><span data-stu-id="b8ff8-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="b8ff8-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="b8ff8-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="b8ff8-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="b8ff8-110">**PsDscAllowDomainUser**</span></span>

><span data-ttu-id="b8ff8-111">**Remarque :** l’utilisation de mots de passe en texte brut n’est pas sécurisée.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-111">**Note:** Using plaintext passwords is not secure.</span></span> <span data-ttu-id="b8ff8-112">Il est recommandé de sécuriser les informations d’identification à l’aide des techniques décrites plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>

<span data-ttu-id="b8ff8-113">Voici un exemple de transmission d’informations d’identification en texte brut :</span><span class="sxs-lookup"><span data-stu-id="b8ff8-113">The following is an example of passing plain text credentials:</span></span>

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

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="b8ff8-114">Gestion des informations d’identification dans DSC</span><span class="sxs-lookup"><span data-stu-id="b8ff8-114">Handling Credentials in DSC</span></span>

<span data-ttu-id="b8ff8-115">Par défaut, les ressources de configuration DSC sont exécutées en tant que `Local System`.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-115">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="b8ff8-116">Toutefois, certaines ressources nécessitent des informations d’identification, par exemple quand la ressource `Package` doit installer des logiciels sous un compte d’utilisateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-116">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="b8ff8-117">Avant, les ressources utilisaient un nom de propriété `Credential` codé en dur pour gérer cette situation.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-117">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="b8ff8-118">Avec WMF 5.0, la propriété `PsDscRunAsCredential` est ajoutée automatiquement à toutes les ressources.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-118">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="b8ff8-119">Pour plus d’informations sur l’utilisation de `PsDscRunAsCredential`, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="b8ff8-119">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="b8ff8-120">Les ressources récentes et les ressources personnalisées peuvent utiliser cette propriété automatique au lieu de créer leur propre propriété d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-120">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

<span data-ttu-id="b8ff8-121">*Notez que certaines ressources sont conçues pour utiliser plusieurs informations d’identification pour une raison donnée, et qu’elles ont leurs propres propriétés d’informations d’identification.*</span><span class="sxs-lookup"><span data-stu-id="b8ff8-121">*Note that the design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.*</span></span>

<span data-ttu-id="b8ff8-122">Pour trouver les propriétés d’informations d’identification disponibles dans une ressource, utilisez `Get-DscResource -Name ResourceName -Syntax` ou Intellisense dans l’environnement ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="b8ff8-122">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="b8ff8-123">Cet exemple utilise une ressource [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) du module de ressource DSC `PSDesiredStateConfiguration` intégré.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-123">This example uses a [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="b8ff8-124">Elle peut créer des groupes locaux et ajouter ou supprimer des membres.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-124">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="b8ff8-125">Elle accepte à la fois la propriété `Credential` et la propriété automatique `PsDscRunAsCredential`.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-125">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="b8ff8-126">Toutefois, la ressource utilise uniquement la propriété `Credential`.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-126">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="b8ff8-127">Pour plus d’informations sur la propriété `PsDscRunAsCredential`, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="b8ff8-127">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="b8ff8-128">Exemple : Propriété d’informations d’identification de la ressource Group</span><span class="sxs-lookup"><span data-stu-id="b8ff8-128">Example: The Group resource Credential property</span></span>

<span data-ttu-id="b8ff8-129">DSC s’exécute sous `Local System`. Il dispose donc déjà des autorisations pour modifier les utilisateurs et les groupes locaux.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-129">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="b8ff8-130">Si le membre ajouté est un compte local, aucune information d’identification n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-130">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="b8ff8-131">Si la ressource `Group` ajoute un compte de domaine au groupe local, des informations d’identification seront nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-131">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="b8ff8-132">Les requêtes anonymes envoyées à Active Directory ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-132">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="b8ff8-133">La propriété `Credential` de la ressource `Group` correspond au compte de domaine utilisé pour interroger Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-133">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="b8ff8-134">Dans la majorité des cas, il peut s’agir d’un compte d’utilisateur générique, car par défaut, les utilisateurs peuvent *lire* la plupart des objets dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-134">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="b8ff8-135">Exemple de configuration</span><span class="sxs-lookup"><span data-stu-id="b8ff8-135">Example Configuration</span></span>

<span data-ttu-id="b8ff8-136">L’exemple de code suivant utilise DSC pour ajouter un utilisateur de domaine à un groupe local :</span><span class="sxs-lookup"><span data-stu-id="b8ff8-136">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="b8ff8-137">Ce code génère à la fois un message d’erreur et un message d’avertissement :</span><span class="sxs-lookup"><span data-stu-id="b8ff8-137">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="b8ff8-138">Cet exemple comprend deux problèmes :</span><span class="sxs-lookup"><span data-stu-id="b8ff8-138">This example has two issues:</span></span>
1.  <span data-ttu-id="b8ff8-139">L’erreur explique que les mots de passe en texte brut ne sont pas recommandés</span><span class="sxs-lookup"><span data-stu-id="b8ff8-139">An error explains that plain text passwords are not recommended</span></span>
2.  <span data-ttu-id="b8ff8-140">L’avertissement recommande de ne pas utiliser d’informations d’identification de domaine</span><span class="sxs-lookup"><span data-stu-id="b8ff8-140">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="b8ff8-141">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="b8ff8-141">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="b8ff8-142">Le premier message d’erreur comprend une URL vers de la documentation.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-142">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="b8ff8-143">Ce lien explique comment chiffrer des mots de passe avec une structure [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) et un certificat.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-143">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="b8ff8-144">Pour plus d’informations sur les certificats et sur DSC, [lisez cet article de blog](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="b8ff8-144">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="b8ff8-145">Pour forcer un mot de passe en texte brut, la ressource nécessite que le mot clé `PsDscAllowPlainTextPassword` se trouve dans la section des données de configuration comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b8ff8-145">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

<span data-ttu-id="b8ff8-146">*Notez que `NodeName` n’est pas équivalent à un astérisque et qu’un nom de nœud doit être fourni obligatoirement.*</span><span class="sxs-lookup"><span data-stu-id="b8ff8-146">*Note that `NodeName` cannot equal asterisk, a specific node name is mandatory.*</span></span>

<span data-ttu-id="b8ff8-147">**Microsoft recommande d’éviter les mots de passe en texte brut en raison de l’important risque de sécurité qu’ils présentent.**</span><span class="sxs-lookup"><span data-stu-id="b8ff8-147">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="b8ff8-148">Informations d’identification de domaine</span><span class="sxs-lookup"><span data-stu-id="b8ff8-148">Domain Credentials</span></span>

<span data-ttu-id="b8ff8-149">Si vous exécutez à nouveau l’exemple de script de configuration (avec ou sans chiffrement), vous obtiendrez toujours l’avertissement selon lequel l’utilisation d’informations d’identification de compte de domaine n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-149">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="b8ff8-150">L’utilisation d’un compte local élimine les risques d’exposition des informations d’identification de domaine qui pourraient être utilisées sur d’autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-150">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="b8ff8-151">**Quand vous utilisez des informations d’identification avec des ressources DSC, préférez un compte local à un compte de domaine quand cela est possible.**</span><span class="sxs-lookup"><span data-stu-id="b8ff8-151">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="b8ff8-152">Si la propriété `Username` des informations d’identification comprend un « \' » ou un « @ », DSC la traite comme un compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-152">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="b8ff8-153">Il existe une exception pour « localhost », « 127.0.0.1 » et « :: 1 » dans la partie du nom d’utilisateur consacrée au domaine.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-153">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="b8ff8-154">PsDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="b8ff8-154">PSDscAllowDomainUser</span></span>

<span data-ttu-id="b8ff8-155">Dans l’exemple de ressource `Group` DSC ci-dessus, le fait d’interroger un domaine Active Directory *nécessite* un compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-155">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="b8ff8-156">Dans ce cas, ajoutez la propriété `PSDscAllowDomainUser` au bloc `ConfigurationData` comme suit :</span><span class="sxs-lookup"><span data-stu-id="b8ff8-156">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="b8ff8-157">Le script de configuration va maintenant générer le fichier MOF sans avertissement ni erreur.</span><span class="sxs-lookup"><span data-stu-id="b8ff8-157">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>

