---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Ressources DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046689"
---
# <a name="dsc-resources"></a><span data-ttu-id="bee63-103">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="bee63-103">DSC Resources</span></span>

><span data-ttu-id="bee63-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bee63-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bee63-105">Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="bee63-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="bee63-106">Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="bee63-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="bee63-107">Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="bee63-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="bee63-108">Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.</span><span class="sxs-lookup"><span data-stu-id="bee63-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="bee63-109">Chaque ressource a un \* schéma qui détermine la syntaxe nécessaire pour utiliser la ressource dans un [Configuration](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="bee63-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="bee63-110">Un schéma d’une ressource peut être défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="bee63-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="bee63-111">**« Schema.MOF »** fichier : La plupart des ressources définir leurs *schéma* dans un « Schema.MOF' fichier, à l’aide [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="bee63-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="bee63-112">**«\<Nom de la ressource\>. schema.psm1'** fichier : [Ressources composites](../configurations/compositeConfigs.md) définir leurs *schéma* dans un «<ResourceName>. schema.psm1' à l’aide de fichiers un [bloc de paramètres de](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="bee63-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="bee63-113">**«\<Nom de la ressource\>.psm1'** fichier : Classe les ressources DSC en définissent leurs *schéma* dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="bee63-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="bee63-114">Éléments de syntaxe sont signalées en tant que propriétés de classe.</span><span class="sxs-lookup"><span data-stu-id="bee63-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="bee63-115">Pour plus d’informations, consultez [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="bee63-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="bee63-116">Pour récupérer la syntaxe pour une ressource DSC, utilisez le [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) applet de commande avec le `-Syntax` paramètre.</span><span class="sxs-lookup"><span data-stu-id="bee63-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="bee63-117">Cette utilisation est similaire à l’utilisation de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) avec le `-Syntax` pour obtenir la syntaxe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bee63-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="bee63-118">La sortie que vous voyez affiche le modèle utilisé pour un bloc de ressources pour la ressource que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="bee63-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="bee63-119">La sortie que vous voyez doit être similaire à la sortie ci-dessous, bien que la syntaxe de la ressource pourrait changer à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="bee63-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="bee63-120">Comme la syntaxe de l’applet de commande, le *clés* vu dans les crochets, sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="bee63-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="bee63-121">Les types de spécifient le type de données qu'attend de chaque clé.</span><span class="sxs-lookup"><span data-stu-id="bee63-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="bee63-122">Le **Vérifiez** clé est facultative, car les valeurs par défaut sur « Present ».</span><span class="sxs-lookup"><span data-stu-id="bee63-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="bee63-123">À l’intérieur d’une Configuration, un **Service** bloc de ressources peut ressembler à ceci pour **Vérifiez** que le service spouleur est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bee63-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="bee63-124">Avant d’utiliser une ressource dans une Configuration, vous devez l’importer à l’aide de [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="bee63-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="bee63-125">Les configurations peuvent contenir plusieurs instances du même type de ressource.</span><span class="sxs-lookup"><span data-stu-id="bee63-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="bee63-126">Chaque instance doit être nommé de manière unique.</span><span class="sxs-lookup"><span data-stu-id="bee63-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="bee63-127">Dans l’exemple suivant, une seconde **Service** bloc de ressources est ajouté pour configurer le service « DHCP ».</span><span class="sxs-lookup"><span data-stu-id="bee63-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="bee63-128">À compter de PowerShell 5.0, intellisense a été ajoutée pour DSC.</span><span class="sxs-lookup"><span data-stu-id="bee63-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="bee63-129">Cette nouvelle fonctionnalité vous permet d’utiliser \<onglet\> et \<Ctrl + espace\> à compléter automatiquement les noms de clé.</span><span class="sxs-lookup"><span data-stu-id="bee63-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Saisie semi-automatique par tabulation ressource](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="bee63-131">Ressources intégrées</span><span class="sxs-lookup"><span data-stu-id="bee63-131">Built-in resources</span></span>

<span data-ttu-id="bee63-132">En plus de ressources de la Communauté, il existe des ressources intégrées pour Windows, les ressources pour Linux et les ressources pour les dépendances entre nœuds.</span><span class="sxs-lookup"><span data-stu-id="bee63-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="bee63-133">Vous pouvez utiliser les étapes ci-dessus pour déterminer la syntaxe de ces ressources et comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="bee63-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="bee63-134">Les pages qui utilise ces ressources ont été archivés sous **référence**.</span><span class="sxs-lookup"><span data-stu-id="bee63-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="bee63-135">Ressources intégrées Windows</span><span class="sxs-lookup"><span data-stu-id="bee63-135">Windows built-in resources</span></span>

* [<span data-ttu-id="bee63-136">Ressource Archive</span><span class="sxs-lookup"><span data-stu-id="bee63-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="bee63-137">Ressource Environment</span><span class="sxs-lookup"><span data-stu-id="bee63-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="bee63-138">Ressource File</span><span class="sxs-lookup"><span data-stu-id="bee63-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="bee63-139">Ressource Group</span><span class="sxs-lookup"><span data-stu-id="bee63-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="bee63-140">Ressource GroupSet</span><span class="sxs-lookup"><span data-stu-id="bee63-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="bee63-141">Ressource Log</span><span class="sxs-lookup"><span data-stu-id="bee63-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="bee63-142">Ressource Package</span><span class="sxs-lookup"><span data-stu-id="bee63-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="bee63-143">Ressource ProcessSet</span><span class="sxs-lookup"><span data-stu-id="bee63-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="bee63-144">Ressources Registry</span><span class="sxs-lookup"><span data-stu-id="bee63-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="bee63-145">Ressource Script</span><span class="sxs-lookup"><span data-stu-id="bee63-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="bee63-146">Ressource Service</span><span class="sxs-lookup"><span data-stu-id="bee63-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="bee63-147">Ressource ServiceSet</span><span class="sxs-lookup"><span data-stu-id="bee63-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="bee63-148">Ressource User</span><span class="sxs-lookup"><span data-stu-id="bee63-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="bee63-149">Ressource WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="bee63-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="bee63-150">Ressource WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="bee63-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="bee63-151">Ressource WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="bee63-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="bee63-152">Ressource WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="bee63-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="bee63-153">Ressources de WindowsPackageCabResource</span><span class="sxs-lookup"><span data-stu-id="bee63-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="bee63-154">Ressource WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="bee63-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="bee63-155">[Les dépendances entre nœuds](../configurations/crossNodeDependencies.md) ressources</span><span class="sxs-lookup"><span data-stu-id="bee63-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="bee63-156">WaitForAll ressource</span><span class="sxs-lookup"><span data-stu-id="bee63-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="bee63-157">WaitForSome ressource</span><span class="sxs-lookup"><span data-stu-id="bee63-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="bee63-158">WaitForAny ressource</span><span class="sxs-lookup"><span data-stu-id="bee63-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="bee63-159">Ressources de gestion de package</span><span class="sxs-lookup"><span data-stu-id="bee63-159">Package Management resources</span></span>

* [<span data-ttu-id="bee63-160">Ressources de PackageManagement</span><span class="sxs-lookup"><span data-stu-id="bee63-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="bee63-161">Ressources de PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="bee63-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="bee63-162">Ressources de Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-162">Linux resources</span></span>

* [<span data-ttu-id="bee63-163">Ressource Archive de Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="bee63-164">Ressource de l’environnement Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="bee63-165">Ressources de FileLine Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="bee63-166">Ressources de fichier Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="bee63-167">Ressource de groupe Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="bee63-168">Ressource de Package Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="bee63-169">Ressource de Script de Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="bee63-170">Ressource de Service de Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="bee63-171">Ressources de SshAuthorizedKeys Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="bee63-172">Ressources d’utilisateur Linux</span><span class="sxs-lookup"><span data-stu-id="bee63-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
