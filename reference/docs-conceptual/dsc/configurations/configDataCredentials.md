---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Options relatives aux informations d’identification dans les données de configuration
ms.openlocfilehash: aac27f1ff4b4287b53745fa3b946fb3de84771c2
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870555"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="6c07c-103">Options relatives aux informations d’identification dans les données de configuration</span><span class="sxs-lookup"><span data-stu-id="6c07c-103">Credentials Options in Configuration Data</span></span>

> <span data-ttu-id="6c07c-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6c07c-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="6c07c-105">Mots de passe en texte brut et utilisateurs de domaine</span><span class="sxs-lookup"><span data-stu-id="6c07c-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="6c07c-106">Les configurations DSC qui contiennent des informations d’identification non chiffrées génèrent un message d’erreur concernant les mots de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="6c07c-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span> <span data-ttu-id="6c07c-107">En outre, DSC génère un avertissement lorsque des informations d’identification de domaine sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="6c07c-107">Also, DSC will generate a warning when using domain credentials.</span></span> <span data-ttu-id="6c07c-108">Pour empêcher ces messages d’erreur et d’avertissement, utilisez les mots clés de données de configuration DSC :</span><span class="sxs-lookup"><span data-stu-id="6c07c-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="6c07c-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="6c07c-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="6c07c-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="6c07c-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="6c07c-111">Le stockage/la transmission des mots de passe en texte clair non chiffrés ne sont généralement pas sécurisés.</span><span class="sxs-lookup"><span data-stu-id="6c07c-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="6c07c-112">Il est recommandé de sécuriser les informations d’identification à l’aide des techniques décrites plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6c07c-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span> <span data-ttu-id="6c07c-113">Le service Azure Automation DSC vous permet de centraliser la gestion des informations d’identification en les compilant dans des configurations et en les stockant en lieu sûr.</span><span class="sxs-lookup"><span data-stu-id="6c07c-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span> <span data-ttu-id="6c07c-114">Pour plus d’informations, consultez : [Compilation des Configurations DSC / Ressources d’informations d’identification](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="6c07c-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="6c07c-115">Gestion des informations d’identification dans DSC</span><span class="sxs-lookup"><span data-stu-id="6c07c-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="6c07c-116">Par défaut, les ressources de configuration DSC sont exécutées en tant que `Local System`.</span><span class="sxs-lookup"><span data-stu-id="6c07c-116">DSC configuration resources run as `Local System` by default.</span></span> <span data-ttu-id="6c07c-117">Toutefois, certaines ressources nécessitent des informations d’identification, par exemple quand la ressource `Package` doit installer des logiciels sous un compte d’utilisateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="6c07c-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="6c07c-118">Avant, les ressources utilisaient un nom de propriété `Credential` codé en dur pour gérer cette situation.</span><span class="sxs-lookup"><span data-stu-id="6c07c-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span> <span data-ttu-id="6c07c-119">Avec WMF 5.0, la propriété `PsDscRunAsCredential` est ajoutée automatiquement à toutes les ressources.</span><span class="sxs-lookup"><span data-stu-id="6c07c-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="6c07c-120">Pour plus d’informations sur l’utilisation de `PsDscRunAsCredential`, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="6c07c-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span> <span data-ttu-id="6c07c-121">Les ressources récentes et les ressources personnalisées peuvent utiliser cette propriété automatique au lieu de créer leur propre propriété d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="6c07c-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="6c07c-122">Certaines ressources sont conçues pour utiliser plusieurs informations d’identification pour une raison donnée et ont leurs propres propriétés d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="6c07c-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="6c07c-123">Pour trouver les propriétés d’informations d’identification disponibles dans une ressource, utilisez `Get-DscResource -Name ResourceName -Syntax` ou Intellisense dans l’environnement ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="6c07c-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
Get-DscResource -Name Group -Syntax
```

```Output
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

<span data-ttu-id="6c07c-124">Cet exemple utilise une ressource [Group](../resources/resources.md) du module de ressource DSC `PSDesiredStateConfiguration` intégré.</span><span class="sxs-lookup"><span data-stu-id="6c07c-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span> <span data-ttu-id="6c07c-125">Elle peut créer des groupes locaux et ajouter ou supprimer des membres.</span><span class="sxs-lookup"><span data-stu-id="6c07c-125">It can create local groups and add or remove members.</span></span> <span data-ttu-id="6c07c-126">Elle accepte à la fois la propriété `Credential` et la propriété automatique `PsDscRunAsCredential`.</span><span class="sxs-lookup"><span data-stu-id="6c07c-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span> <span data-ttu-id="6c07c-127">Toutefois, la ressource utilise uniquement la propriété `Credential`.</span><span class="sxs-lookup"><span data-stu-id="6c07c-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="6c07c-128">Pour plus d’informations sur la propriété `PsDscRunAsCredential`, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="6c07c-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="6c07c-129">Exemple : propriété d’informations d’identification de la ressource Group</span><span class="sxs-lookup"><span data-stu-id="6c07c-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="6c07c-130">DSC s’exécute sous `Local System`. Il dispose donc déjà des autorisations pour modifier les utilisateurs et les groupes locaux.</span><span class="sxs-lookup"><span data-stu-id="6c07c-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span> <span data-ttu-id="6c07c-131">Si le membre ajouté est un compte local, aucune information d’identification n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6c07c-131">If the member added is a local account, then no credential is necessary.</span></span> <span data-ttu-id="6c07c-132">Si la ressource `Group` ajoute un compte de domaine au groupe local, des informations d’identification seront nécessaires.</span><span class="sxs-lookup"><span data-stu-id="6c07c-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="6c07c-133">Les requêtes anonymes envoyées à Active Directory ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="6c07c-133">Anonymous queries to Active Directory are not allowed.</span></span> <span data-ttu-id="6c07c-134">La propriété `Credential` de la ressource `Group` correspond au compte de domaine utilisé pour interroger Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6c07c-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span> <span data-ttu-id="6c07c-135">Dans la majorité des cas, il peut s’agir d’un compte d’utilisateur générique, car par défaut, les utilisateurs peuvent *lire* la plupart des objets dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6c07c-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="6c07c-136">Exemple de configuration</span><span class="sxs-lookup"><span data-stu-id="6c07c-136">Example Configuration</span></span>

<span data-ttu-id="6c07c-137">L’exemple de code suivant utilise DSC pour ajouter un utilisateur de domaine à un groupe local :</span><span class="sxs-lookup"><span data-stu-id="6c07c-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="6c07c-138">Ce code génère à la fois un message d’erreur et un message d’avertissement :</span><span class="sxs-lookup"><span data-stu-id="6c07c-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="6c07c-139">Cet exemple comprend deux problèmes :</span><span class="sxs-lookup"><span data-stu-id="6c07c-139">This example has two issues:</span></span>

1. <span data-ttu-id="6c07c-140">L’erreur explique que les mots de passe en texte brut ne sont pas recommandés</span><span class="sxs-lookup"><span data-stu-id="6c07c-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="6c07c-141">L’avertissement recommande de ne pas utiliser d’informations d’identification de domaine</span><span class="sxs-lookup"><span data-stu-id="6c07c-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="6c07c-142">Les indicateurs **PSDSCAllowPlainTextPassword** et **PSDSCAllowDomainUser** suppriment l’erreur et l’avertissement informant l’utilisateur du risque encouru.</span><span class="sxs-lookup"><span data-stu-id="6c07c-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="6c07c-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="6c07c-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="6c07c-144">Le premier message d’erreur comprend une URL vers de la documentation.</span><span class="sxs-lookup"><span data-stu-id="6c07c-144">The first error message has a URL with documentation.</span></span> <span data-ttu-id="6c07c-145">Ce lien explique comment chiffrer des mots de passe avec une structure [ConfigurationData](./configData.md) et un certificat.</span><span class="sxs-lookup"><span data-stu-id="6c07c-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span> <span data-ttu-id="6c07c-146">Pour plus d’informations sur les certificats et sur DSC, [lisez cet article de blog](https://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="6c07c-146">For more information on certificates and DSC [read this post](https://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="6c07c-147">Pour forcer un mot de passe en texte brut, la ressource nécessite que le mot clé `PsDscAllowPlainTextPassword` se trouve dans la section des données de configuration comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6c07c-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="6c07c-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="6c07c-148">localhost.mof</span></span>

<span data-ttu-id="6c07c-149">L’indicateur **PSDSCAllowPlainTextPassword** exige que l’utilisateur connaisse les risques liés au stockage de mots de passe en texte brut dans un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="6c07c-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="6c07c-150">Dans le fichier MOF généré, même si un objet **PSCredential** contenant une valeur **SecureString** a été utilisé, les mots de passe continueront d’apparaître en tant que texte brut.</span><span class="sxs-lookup"><span data-stu-id="6c07c-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="6c07c-151">C’est la seule fois où les informations d’identification sont exposées.</span><span class="sxs-lookup"><span data-stu-id="6c07c-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="6c07c-152">Ce fichier MOF offre à tout le monde un accès au compte Administrateur.</span><span class="sxs-lookup"><span data-stu-id="6c07c-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="6c07c-153">Informations d’identification en transit et au repos</span><span class="sxs-lookup"><span data-stu-id="6c07c-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="6c07c-154">L’indicateur **PSDscAllowPlainTextPassword** permet la compilation de fichiers MOF contenant les mots de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="6c07c-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span> <span data-ttu-id="6c07c-155">Prenez des précautions lorsque vous stockez des fichiers MOF contenant des mots de passe de texte clair.</span><span class="sxs-lookup"><span data-stu-id="6c07c-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="6c07c-156">Lorsque le fichier MOF est transmis à un nœud en mode **Push**, WinRM chiffre la communication pour protéger le mot de passe de texte en clair, sauf si vous remplacez la valeur par défaut par le paramètre **AllowUnencrypted**.</span><span class="sxs-lookup"><span data-stu-id="6c07c-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="6c07c-157">Le chiffrement du fichier MOF avec un certificat protège le fichier MOF au repos avant qu’il soit appliqué à un nœud.</span><span class="sxs-lookup"><span data-stu-id="6c07c-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="6c07c-158">En mode **Pull**, vous pouvez configurer un serveur Pull Windows afin d’utiliser HTTPS pour chiffrer le trafic à l’aide du protocole spécifié dans Internet Information Server.</span><span class="sxs-lookup"><span data-stu-id="6c07c-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="6c07c-159">Pour plus d’informations, consultez les articles [Configuration d’un client Pull DSC](../pull-server/pullclient.md) et [Sécurisation des fichiers MOF avec des certificats](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="6c07c-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="6c07c-160">Dans le service [Azure Automation State Configuration](/azure/automation/automation-dsc-overview), le trafic Pull est toujours chiffré.</span><span class="sxs-lookup"><span data-stu-id="6c07c-160">In the [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="6c07c-161">Sur le nœud, les fichiers MOF sont chiffrés au repos à compter de PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="6c07c-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="6c07c-162">Dans PowerShell 4.0, les fichiers MOF ne sont pas chiffrés au repos, sauf s’ils sont chiffrés avec un certificat lorsqu’ils sont envoyés (Push) au nœud ou extraits (Pull) de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="6c07c-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="6c07c-163">**Microsoft recommande d’éviter les mots de passe en texte brut en raison de l’important risque de sécurité qu’ils présentent.**</span><span class="sxs-lookup"><span data-stu-id="6c07c-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="6c07c-164">Informations d'identification du domaine</span><span class="sxs-lookup"><span data-stu-id="6c07c-164">Domain Credentials</span></span>

<span data-ttu-id="6c07c-165">Si vous exécutez à nouveau l’exemple de script de configuration (avec ou sans chiffrement), vous obtiendrez toujours l’avertissement selon lequel l’utilisation d’informations d’identification de compte de domaine n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="6c07c-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span> <span data-ttu-id="6c07c-166">L’utilisation d’un compte local élimine les risques d’exposition des informations d’identification de domaine qui pourraient être utilisées sur d’autres serveurs.</span><span class="sxs-lookup"><span data-stu-id="6c07c-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="6c07c-167">**Quand vous utilisez des informations d’identification avec des ressources DSC, préférez un compte local à un compte de domaine quand cela est possible.**</span><span class="sxs-lookup"><span data-stu-id="6c07c-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="6c07c-168">Si la propriété `Username` des informations d’identification comprend un « \\ » ou un « \@ », DSC la traite comme un compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="6c07c-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span> <span data-ttu-id="6c07c-169">Il existe une exception pour « localhost », « 127.0.0.1 » et « :: 1 » dans la partie du nom d’utilisateur consacrée au domaine.</span><span class="sxs-lookup"><span data-stu-id="6c07c-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="6c07c-170">PsDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="6c07c-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="6c07c-171">Dans l’exemple de ressource `Group` DSC ci-dessus, le fait d’interroger un domaine Active Directory *nécessite* un compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="6c07c-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span> <span data-ttu-id="6c07c-172">Dans ce cas, ajoutez la propriété `PSDscAllowDomainUser` au bloc `ConfigurationData` comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c07c-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="6c07c-173">Le script de configuration va maintenant générer le fichier MOF sans avertissement ni erreur.</span><span class="sxs-lookup"><span data-stu-id="6c07c-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
