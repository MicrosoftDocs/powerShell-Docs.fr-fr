---
ms.date: 02/28/2020
keywords: dsc,powershell,configuration,installation
title: Ressources DSC
ms.openlocfilehash: 863898d910cc3c75c3e5977a5b6b0657ba7ed512
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278242"
---
# <a name="dsc-resources"></a><span data-ttu-id="e191f-103">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="e191f-103">DSC Resources</span></span>

> <span data-ttu-id="e191f-104">S’applique à la version 4.0 de Windows PowerShell et aux versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e191f-104">Applies to Windows PowerShell 4.0 and up.</span></span>

## <a name="overview"></a><span data-ttu-id="e191f-105">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="e191f-105">Overview</span></span>

<span data-ttu-id="e191f-106">Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="e191f-106">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="e191f-107">Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e191f-107">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="e191f-108">Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="e191f-108">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="e191f-109">Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.</span><span class="sxs-lookup"><span data-stu-id="e191f-109">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="e191f-110">Chaque ressource comporte un \*schéma qui détermine la syntaxe nécessaire pour utiliser la ressource dans une [configuration](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="e191f-110">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span>
<span data-ttu-id="e191f-111">Le schéma d’une ressource peut être défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="e191f-111">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="e191f-112">Fichier **'Schema.Mof'**  : La plupart des ressources définissent leur _schéma_ dans un fichier « Schema.MOF » à l’aide de [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="e191f-112">**'Schema.Mof'** file: Most resources define their _schema_ in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="e191f-113">Fichier **'\<Nom de la ressource\>.schema.psm1'**  : Les [ressources composites](../configurations/compositeConfigs.md) définissent leur *schéma* dans un fichier '<ResourceName>.schema.psm1' à l’aide d’un [bloc de paramètres](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="e191f-113">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="e191f-114">Fichier **'\<Nom de la ressource\>.psm1'**  : Les ressources DSC basées sur la classe définissent leur _schéma_ dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="e191f-114">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their _schema_ in the class definition.</span></span> <span data-ttu-id="e191f-115">Les éléments de syntaxe sont signalés en tant que propriétés de classe.</span><span class="sxs-lookup"><span data-stu-id="e191f-115">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="e191f-116">Pour plus d’informations, consultez [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="e191f-116">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="e191f-117">Pour récupérer la syntaxe d’une ressource DSC, utilisez l’applet de commande [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) avec le paramètre `-Syntax`.</span><span class="sxs-lookup"><span data-stu-id="e191f-117">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="e191f-118">Cette méthode est similaire à l’utilisation de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) avec le paramètre `-Syntax` pour obtenir la syntaxe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e191f-118">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="e191f-119">Le résultat affichera le modèle utilisé pour un bloc de ressources correspondant à la ressource que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="e191f-119">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="e191f-120">Le résultat devrait être similaire à ce qui suit, même si la syntaxe de la ressource risque de change à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="e191f-120">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="e191f-121">Comme dans la syntaxe de l’applet de commande, les _clés_ affichées entre crochets sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="e191f-121">Like cmdlet syntax, the _keys_ seen in square brackets, are optional.</span></span> <span data-ttu-id="e191f-122">Les types spécifient le type de données attendu par chaque clé.</span><span class="sxs-lookup"><span data-stu-id="e191f-122">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="e191f-123">La clé **Ensure** (garantir) est facultative car les valeurs par défaut sont définies sur « Present ».</span><span class="sxs-lookup"><span data-stu-id="e191f-123">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="e191f-124">Dans une configuration, un bloc de ressources **Service** peut ressembler à ceci pour **garantir** que le service Spooler est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e191f-124">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="e191f-125">Avant d’utiliser une ressource dans une configuration, vous devez l’importer à l’aide d’[Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="e191f-125">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="e191f-126">Les configurations peuvent contenir plusieurs instances du même type de ressource.</span><span class="sxs-lookup"><span data-stu-id="e191f-126">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="e191f-127">Chaque instance doit afficher un nom unique.</span><span class="sxs-lookup"><span data-stu-id="e191f-127">Each instance must be uniquely named.</span></span> <span data-ttu-id="e191f-128">Dans l’exemple suivant, un second bloc de ressources **Service** est ajouté pour configurer le service « DHCP ».</span><span class="sxs-lookup"><span data-stu-id="e191f-128">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="e191f-129">À compter de PowerShell 5.0, IntelliSense a été ajouté pour DSC.</span><span class="sxs-lookup"><span data-stu-id="e191f-129">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="e191f-130">Cette nouvelle fonctionnalité permet d’utiliser les touches <kbd>Tab</kbd> et <kbd>Ctrl</kbd>+<kbd>Espace</kbd> pour l’autocomplétion des noms de clés.</span><span class="sxs-lookup"><span data-stu-id="e191f-130">This new feature allows you to use <kbd>TAB</kbd> and <kbd>Ctr</kbd>+<kbd>Space</kbd> to auto-complete key names.</span></span>

![Saisie semi-automatique des ressources via la touche Tab](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a><span data-ttu-id="e191f-132">Types de ressources</span><span class="sxs-lookup"><span data-stu-id="e191f-132">Types of resources</span></span>

<span data-ttu-id="e191f-133">Windows est fourni avec des ressources intégrées et Linux possède des ressources propres au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="e191f-133">Windows comes with built in resources and Linux has OS specific resources.</span></span> <span data-ttu-id="e191f-134">Il existe des ressources pour les [dépendances entre les nœuds](../configurations/crossNodeDependencies.md), des ressources de gestion des packages, ainsi que des ressources [appartenant à la communauté et gérées par la communauté](https://github.com/dsccommunity).</span><span class="sxs-lookup"><span data-stu-id="e191f-134">There are resources for [cross-node dependencies](../configurations/crossNodeDependencies.md), package management resources, as well as[community owned and maintained resources](https://github.com/dsccommunity).</span></span> <span data-ttu-id="e191f-135">Vous pouvez suivre les étapes ci-dessus pour déterminer la syntaxe de ces ressources et savoir comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="e191f-135">You can use the above steps to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="e191f-136">Les pages qui utilisent ces ressources ont été archivées sous **Référence**.</span><span class="sxs-lookup"><span data-stu-id="e191f-136">The pages that serve these resources have been archived under **Reference**.</span></span>

### <a name="windows-built-in-resources"></a><span data-ttu-id="e191f-137">Ressources intégrées Windows</span><span class="sxs-lookup"><span data-stu-id="e191f-137">Windows built-in resources</span></span>

- [<span data-ttu-id="e191f-138">Ressource Archive</span><span class="sxs-lookup"><span data-stu-id="e191f-138">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
- [<span data-ttu-id="e191f-139">Ressource Environment</span><span class="sxs-lookup"><span data-stu-id="e191f-139">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
- [<span data-ttu-id="e191f-140">Ressource File</span><span class="sxs-lookup"><span data-stu-id="e191f-140">File Resource</span></span>](../reference/resources/windows/fileResource.md)
- [<span data-ttu-id="e191f-141">Ressource Group</span><span class="sxs-lookup"><span data-stu-id="e191f-141">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
- [<span data-ttu-id="e191f-142">Ressource GroupSet</span><span class="sxs-lookup"><span data-stu-id="e191f-142">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
- [<span data-ttu-id="e191f-143">Ressource Log</span><span class="sxs-lookup"><span data-stu-id="e191f-143">Log Resource</span></span>](../reference/resources/windows/logResource.md)
- [<span data-ttu-id="e191f-144">Ressource Package</span><span class="sxs-lookup"><span data-stu-id="e191f-144">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
- [<span data-ttu-id="e191f-145">Ressource ProcessSet</span><span class="sxs-lookup"><span data-stu-id="e191f-145">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
- [<span data-ttu-id="e191f-146">Ressources Registry</span><span class="sxs-lookup"><span data-stu-id="e191f-146">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
- [<span data-ttu-id="e191f-147">Ressource Script</span><span class="sxs-lookup"><span data-stu-id="e191f-147">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
- [<span data-ttu-id="e191f-148">Ressource Service</span><span class="sxs-lookup"><span data-stu-id="e191f-148">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
- [<span data-ttu-id="e191f-149">Ressource ServiceSet</span><span class="sxs-lookup"><span data-stu-id="e191f-149">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
- [<span data-ttu-id="e191f-150">Ressource User</span><span class="sxs-lookup"><span data-stu-id="e191f-150">User Resource</span></span>](../reference/resources/windows/userResource.md)
- [<span data-ttu-id="e191f-151">Ressource WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="e191f-151">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
- [<span data-ttu-id="e191f-152">Ressource WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="e191f-152">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
- [<span data-ttu-id="e191f-153">Ressource WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="e191f-153">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [<span data-ttu-id="e191f-154">Ressource WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="e191f-154">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [<span data-ttu-id="e191f-155">Ressource WindowsPackageCabResource</span><span class="sxs-lookup"><span data-stu-id="e191f-155">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
- [<span data-ttu-id="e191f-156">Ressource WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="e191f-156">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a><span data-ttu-id="e191f-157">Ressources de dépendance entre les nœuds</span><span class="sxs-lookup"><span data-stu-id="e191f-157">Cross-Node dependency resources</span></span>

- [<span data-ttu-id="e191f-158">Ressource WaitForAll</span><span class="sxs-lookup"><span data-stu-id="e191f-158">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
- [<span data-ttu-id="e191f-159">Ressource WaitForSome</span><span class="sxs-lookup"><span data-stu-id="e191f-159">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
- [<span data-ttu-id="e191f-160">Ressource WaitForAny</span><span class="sxs-lookup"><span data-stu-id="e191f-160">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a><span data-ttu-id="e191f-161">Ressources Package Management</span><span class="sxs-lookup"><span data-stu-id="e191f-161">Package Management resources</span></span>

- [<span data-ttu-id="e191f-162">Ressource PackageManagement</span><span class="sxs-lookup"><span data-stu-id="e191f-162">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [<span data-ttu-id="e191f-163">Ressource PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="e191f-163">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a><span data-ttu-id="e191f-164">Ressources Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-164">Linux resources</span></span>

- [<span data-ttu-id="e191f-165">Ressource Archive Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-165">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
- [<span data-ttu-id="e191f-166">Ressource Environment Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-166">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
- [<span data-ttu-id="e191f-167">Ressources FileLine Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-167">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
- [<span data-ttu-id="e191f-168">Ressource File Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-168">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
- [<span data-ttu-id="e191f-169">Ressource Group Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-169">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
- [<span data-ttu-id="e191f-170">Ressource Package Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-170">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
- [<span data-ttu-id="e191f-171">Ressource Script Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-171">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
- [<span data-ttu-id="e191f-172">Ressource Service Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-172">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
- [<span data-ttu-id="e191f-173">Ressource SshAuthorizedKeys Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-173">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [<span data-ttu-id="e191f-174">Ressource User Linux</span><span class="sxs-lookup"><span data-stu-id="e191f-174">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
