---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Options relatives aux informations d’identification dans les données de configuration
ms.openlocfilehash: 10cf3456fcc7104b7dd779db30aebace54ba087a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046639"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="b02bd-103">Options relatives aux informations d’identification dans les données de configuration</span><span class="sxs-lookup"><span data-stu-id="b02bd-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="b02bd-104">S'applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b02bd-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="b02bd-105">Mots de passe en texte brut et utilisateurs de domaine</span><span class="sxs-lookup"><span data-stu-id="b02bd-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="b02bd-106">Les configurations DSC qui contiennent des informations d’identification non chiffrées génèrent un message d’erreur concernant les mots de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="b02bd-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="b02bd-107">En outre, DSC génère un avertissement lorsque des informations d’identification de domaine sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="b02bd-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="b02bd-108">Pour empêcher ces messages d’erreur et d’avertissement, utilisez les mots clés de données de configuration DSC :</span><span class="sxs-lookup"><span data-stu-id="b02bd-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="b02bd-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="b02bd-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="b02bd-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="b02bd-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="b02bd-111">Le stockage/la transmission des mots de passe en texte clair non chiffrés ne sont généralement pas sécurisés.</span><span class="sxs-lookup"><span data-stu-id="b02bd-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="b02bd-112">Il est recommandé de sécuriser les informations d’identification à l’aide des techniques décrites plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b02bd-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="b02bd-113">Le service Azure Automation DSC vous permet de centraliser la gestion des informations d’identification en les compilant dans des configurations et en les stockant en lieu sûr.</span><span class="sxs-lookup"><span data-stu-id="b02bd-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="b02bd-114">Pour plus d'informations, consultez : [Compilation des Configurations DSC / ressources des informations d’identification](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="b02bd-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="b02bd-115">Voici un exemple de transmission d’informations d’identification en texte brut :</span><span class="sxs-lookup"><span data-stu-id="b02bd-115">The following is an example of passing plain text credentials:</span></span>

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
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $promptedCreds
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }
}

# We declared the ConfigurationData in a local variable, but we need to pass it
# in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData

# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

<span data-ttu-id="b02bd-116">Il s’agit d’un extrait à partir du fichier « .mof » généré par la configuration pour « TestMachine1 ».</span><span class="sxs-lookup"><span data-stu-id="b02bd-116">This is an excerpt from the ".mof" file generated by the configuration for "TestMachine1".</span></span> <span data-ttu-id="b02bd-117">Le `System.Security.SecureString` utilisé dans la configuration a été convertie en texte brut et stockée dans le fichier « .mof » comme un `MSF_Credential`.</span><span class="sxs-lookup"><span data-stu-id="b02bd-117">The `System.Security.SecureString` used in the configuration was converted to plain text and stored in the ".mof" file as a `MSF_Credential`.</span></span> <span data-ttu-id="b02bd-118">Un `SecureString` est chiffré avec le profil des utilisateurs en cours.</span><span class="sxs-lookup"><span data-stu-id="b02bd-118">A `SecureString` is encrypted with the current users profile.</span></span> <span data-ttu-id="b02bd-119">Cela fonctionne bien avec toutes les formes de gestion à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b02bd-119">This works well with all forms of PowerShell remote management.</span></span> <span data-ttu-id="b02bd-120">Un fichier « .mof » est conçu pour être un mécanisme de configuration autonome de secours.</span><span class="sxs-lookup"><span data-stu-id="b02bd-120">A ".mof" file is designed to be a stand alone configuration mechanism.</span></span> <span data-ttu-id="b02bd-121">À compter de PowerShell 5.0, les fichiers « .mof » sur un nœud sont chiffrés au repos, mais pas en transit vers le nœud.</span><span class="sxs-lookup"><span data-stu-id="b02bd-121">Beginning in PowerShell 5.0, ".mof" files on a Node are encrypted at rest, but not in transit to the Node.</span></span> <span data-ttu-id="b02bd-122">Cela signifie que les mots de passe dans un fichier « .mof » sont exposés en texte clair lorsque vous les appliquez à un nœud.</span><span class="sxs-lookup"><span data-stu-id="b02bd-122">This means that passwords in a ".mof" file are exposed as clear text when you apply them to a Node.</span></span> <span data-ttu-id="b02bd-123">Pour chiffrer les informations d’identification, vous devez utiliser un **serveur collecteur**.</span><span class="sxs-lookup"><span data-stu-id="b02bd-123">To encrypt credentials, you need to use a **Pull Server**.</span></span> <span data-ttu-id="b02bd-124">Pour plus d’informations, consultez [fichiers MOF de sécurisation des certificats](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="b02bd-124">For more information, see [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="b02bd-125">Gestion des informations d’identification dans DSC</span><span class="sxs-lookup"><span data-stu-id="b02bd-125">Handling Credentials in DSC</span></span>

<span data-ttu-id="b02bd-126">Par défaut, les ressources de configuration DSC sont exécutées en tant que `Local System`.</span><span class="sxs-lookup"><span data-stu-id="b02bd-126">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="b02bd-127">Toutefois, certaines ressources nécessitent des informations d’identification, par exemple quand la ressource `Package` doit installer des logiciels sous un compte d’utilisateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="b02bd-127">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="b02bd-128">Avant, les ressources utilisaient un nom de propriété `Credential` codé en dur pour gérer cette situation.</span><span class="sxs-lookup"><span data-stu-id="b02bd-128">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="b02bd-129">Avec WMF 5.0, la propriété `PsDscRunAsCredential` est ajoutée automatiquement à toutes les ressources.</span><span class="sxs-lookup"><span data-stu-id="b02bd-129">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="b02bd-130">Pour plus d’informations sur l’utilisation de `PsDscRunAsCredential`, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="b02bd-130">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="b02bd-131">Les ressources récentes et les ressources personnalisées peuvent utiliser cette propriété automatique au lieu de créer leur propre propriété d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="b02bd-131">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="b02bd-132">Certaines ressources sont conçues pour utiliser plusieurs informations d’identification pour une raison donnée et ont leurs propres propriétés d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="b02bd-132">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="b02bd-133">Pour trouver les propriétés d’informations d’identification disponibles dans une ressource, utilisez `Get-DscResource -Name ResourceName -Syntax` ou Intellisense dans l’environnement ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="b02bd-133">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="b02bd-134">Cet exemple utilise une ressource [Group](../resources/resources.md) du module de ressource DSC `PSDesiredStateConfiguration` intégré.</span><span class="sxs-lookup"><span data-stu-id="b02bd-134">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="b02bd-135">Elle peut créer des groupes locaux et ajouter ou supprimer des membres.</span><span class="sxs-lookup"><span data-stu-id="b02bd-135">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="b02bd-136">Elle accepte à la fois la propriété `Credential` et la propriété automatique `PsDscRunAsCredential`.</span><span class="sxs-lookup"><span data-stu-id="b02bd-136">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="b02bd-137">Toutefois, la ressource utilise uniquement la propriété `Credential`.</span><span class="sxs-lookup"><span data-stu-id="b02bd-137">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="b02bd-138">Pour plus d’informations sur la propriété `PsDscRunAsCredential`, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="b02bd-138">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="b02bd-139">Exemple : La propriété des informations d’identification de ressource de groupe</span><span class="sxs-lookup"><span data-stu-id="b02bd-139">Example: The Group resource Credential property</span></span>

<span data-ttu-id="b02bd-140">DSC s’exécute sous `Local System`. Il dispose donc déjà des autorisations pour modifier les utilisateurs et les groupes locaux.</span><span class="sxs-lookup"><span data-stu-id="b02bd-140">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="b02bd-141">Si le membre ajouté est un compte local, aucune information d’identification n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b02bd-141">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="b02bd-142">Si la ressource `Group` ajoute un compte de domaine au groupe local, des informations d’identification seront nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b02bd-142">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="b02bd-143">Les requêtes anonymes envoyées à Active Directory ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="b02bd-143">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="b02bd-144">La propriété `Credential` de la ressource `Group` correspond au compte de domaine utilisé pour interroger Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b02bd-144">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="b02bd-145">Dans la majorité des cas, il peut s’agir d’un compte d’utilisateur générique, car par défaut, les utilisateurs peuvent *lire* la plupart des objets dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b02bd-145">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="b02bd-146">Exemple de configuration</span><span class="sxs-lookup"><span data-stu-id="b02bd-146">Example Configuration</span></span>

<span data-ttu-id="b02bd-147">L’exemple de code suivant utilise DSC pour ajouter un utilisateur de domaine à un groupe local :</span><span class="sxs-lookup"><span data-stu-id="b02bd-147">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="b02bd-148">Ce code génère à la fois un message d’erreur et un message d’avertissement :</span><span class="sxs-lookup"><span data-stu-id="b02bd-148">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="b02bd-149">Cet exemple comprend deux problèmes :</span><span class="sxs-lookup"><span data-stu-id="b02bd-149">This example has two issues:</span></span>
1. <span data-ttu-id="b02bd-150">L’erreur explique que les mots de passe en texte brut ne sont pas recommandés</span><span class="sxs-lookup"><span data-stu-id="b02bd-150">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="b02bd-151">L’avertissement recommande de ne pas utiliser d’informations d’identification de domaine</span><span class="sxs-lookup"><span data-stu-id="b02bd-151">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="b02bd-152">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="b02bd-152">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="b02bd-153">Le premier message d’erreur comprend une URL vers de la documentation.</span><span class="sxs-lookup"><span data-stu-id="b02bd-153">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="b02bd-154">Ce lien explique comment chiffrer des mots de passe avec une structure [ConfigurationData](./configData.md) et un certificat.</span><span class="sxs-lookup"><span data-stu-id="b02bd-154">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="b02bd-155">Pour plus d’informations sur les certificats et sur DSC, [lisez cet article de blog](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="b02bd-155">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="b02bd-156">Pour forcer un mot de passe en texte brut, la ressource nécessite que le mot clé `PsDscAllowPlainTextPassword` se trouve dans la section des données de configuration comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b02bd-156">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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
> <span data-ttu-id="b02bd-157">`NodeName` n’est pas équivalent à un astérisque et un nom de nœud doit être fourni obligatoirement.</span><span class="sxs-lookup"><span data-stu-id="b02bd-157">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="b02bd-158">**Microsoft recommande d’éviter les mots de passe en texte brut en raison de l’important risque de sécurité qu’ils présentent.**</span><span class="sxs-lookup"><span data-stu-id="b02bd-158">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="b02bd-159">Informations d’identification de domaine</span><span class="sxs-lookup"><span data-stu-id="b02bd-159">Domain Credentials</span></span>

<span data-ttu-id="b02bd-160">Si vous exécutez à nouveau l’exemple de script de configuration (avec ou sans chiffrement), vous obtiendrez toujours l’avertissement selon lequel l’utilisation d’informations d’identification de compte de domaine n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="b02bd-160">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="b02bd-161">L’utilisation d’un compte local élimine les risques d’exposition des informations d’identification de domaine qui pourraient être utilisées sur d’autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="b02bd-161">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="b02bd-162">**Quand vous utilisez des informations d’identification avec des ressources DSC, préférez un compte local à un compte de domaine quand cela est possible.**</span><span class="sxs-lookup"><span data-stu-id="b02bd-162">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="b02bd-163">Si la propriété `Username` des informations d’identification comprend un « \' » ou un « @ », DSC la traite comme un compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="b02bd-163">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="b02bd-164">Il existe une exception pour « localhost », « 127.0.0.1 » et « :: 1 » dans la partie du nom d’utilisateur consacrée au domaine.</span><span class="sxs-lookup"><span data-stu-id="b02bd-164">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="b02bd-165">PsDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="b02bd-165">PSDscAllowDomainUser</span></span>

<span data-ttu-id="b02bd-166">Dans l’exemple de ressource `Group` DSC ci-dessus, le fait d’interroger un domaine Active Directory *nécessite* un compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="b02bd-166">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="b02bd-167">Dans ce cas, ajoutez la propriété `PSDscAllowDomainUser` au bloc `ConfigurationData` comme suit :</span><span class="sxs-lookup"><span data-stu-id="b02bd-167">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="b02bd-168">Le script de configuration va maintenant générer le fichier MOF sans avertissement ni erreur.</span><span class="sxs-lookup"><span data-stu-id="b02bd-168">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
