---
ms.date: 07/23/2020
keywords: dsc,powershell,configuration,installation
title: Ressources DSC
description: Les ressources DSC fournissent les éléments de base d’une configuration DSC. Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell utilisées par le Gestionnaire de configuration local (LCM) pour appliquer la configuration.
ms.openlocfilehash: 33268c68638bb581e0b2235a53aee9d186dff6be
ms.sourcegitcommit: 0f003644684422e425a59b7361121e05ac772e15
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98771796"
---
# <a name="dsc-resources"></a><span data-ttu-id="ac725-105">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="ac725-105">DSC Resources</span></span>

> <span data-ttu-id="ac725-106">S’applique à la version 4.0 de Windows PowerShell et aux versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="ac725-106">Applies to Windows PowerShell 4.0 and up.</span></span>

## <a name="overview"></a><span data-ttu-id="ac725-107">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="ac725-107">Overview</span></span>

<span data-ttu-id="ac725-108">Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="ac725-108">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="ac725-109">Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ac725-109">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="ac725-110">Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="ac725-110">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="ac725-111">Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.</span><span class="sxs-lookup"><span data-stu-id="ac725-111">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="ac725-112">Chaque ressource comporte un \*schéma qui détermine la syntaxe nécessaire pour utiliser la ressource dans une [configuration](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="ac725-112">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="ac725-113">Le schéma d’une ressource peut être défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="ac725-113">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="ac725-114">Fichier `Schema.Mof` : La plupart des ressources définissent leur _schéma_ dans un fichier `schema.mof` à l’aide de [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="ac725-114">`Schema.Mof` file: Most resources define their _schema_ in a `schema.mof` file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="ac725-115">Fichier `<Resource Name>.schema.psm1` : Les [ressources composites](../configurations/compositeConfigs.md) définissent leur _schéma_ dans un fichier `<ResourceName>.schema.psm1` à l’aide d’un [bloc de paramètres](/powershell/module/microsoft.powershell.core/about/about_functions#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="ac725-115">`<Resource Name>.schema.psm1` file: [Composite Resources](../configurations/compositeConfigs.md) define their _schema_ in a `<ResourceName>.schema.psm1` file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions#functions-with-parameters).</span></span>
- <span data-ttu-id="ac725-116">Fichier `<Resource Name>.psm1` : Les ressources DSC basées sur la classe définissent leur _schéma_ dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="ac725-116">`<Resource Name>.psm1` file: Class based DSC resources define their _schema_ in the class definition.</span></span> <span data-ttu-id="ac725-117">Les éléments de syntaxe sont signalés en tant que propriétés de classe.</span><span class="sxs-lookup"><span data-stu-id="ac725-117">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="ac725-118">Pour plus d’informations, consultez [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="ac725-118">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="ac725-119">Pour récupérer la syntaxe d’une ressource DSC, utilisez l’applet de commande [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) avec le paramètre **Syntax**.</span><span class="sxs-lookup"><span data-stu-id="ac725-119">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the **Syntax** parameter.</span></span> <span data-ttu-id="ac725-120">Cette méthode est similaire à l’utilisation de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) avec le paramètre **Syntax** pour obtenir la syntaxe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ac725-120">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the **Syntax** parameter to get cmdlet syntax.</span></span> <span data-ttu-id="ac725-121">Le résultat affichera le modèle utilisé pour un bloc de ressources correspondant à la ressource que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="ac725-121">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="ac725-122">Le résultat devrait être similaire à ce qui suit, même si la syntaxe de la ressource risque de change à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="ac725-122">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="ac725-123">Comme dans la syntaxe de l’applet de commande, les _clés_ affichées entre crochets sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="ac725-123">Like cmdlet syntax, the _keys_ seen in square brackets, are optional.</span></span> <span data-ttu-id="ac725-124">Les types spécifient le type de données attendu par chaque clé.</span><span class="sxs-lookup"><span data-stu-id="ac725-124">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="ac725-125">La clé **Ensure** (garantir) est facultative car les valeurs par défaut sont définies sur « Present ».</span><span class="sxs-lookup"><span data-stu-id="ac725-125">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

> [!NOTE]
> <span data-ttu-id="ac725-126">Dans les versions de PowerShell inférieures à 7.0, `Get-DscResource` ne trouve pas les ressources DSC basées sur une classe.</span><span class="sxs-lookup"><span data-stu-id="ac725-126">In PowerShell versions below 7.0, `Get-DscResource` does not find Class based DSC resources.</span></span>

<span data-ttu-id="ac725-127">Dans une configuration, un bloc de ressources **Service** peut ressembler à ceci pour **garantir** que le service Spooler est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ac725-127">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="ac725-128">Avant d’utiliser une ressource dans une configuration, vous devez l’importer à l’aide d’[Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="ac725-128">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the
    # resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as l
        # ong as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="ac725-129">Les configurations peuvent contenir plusieurs instances du même type de ressource.</span><span class="sxs-lookup"><span data-stu-id="ac725-129">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="ac725-130">Chaque instance doit afficher un nom unique.</span><span class="sxs-lookup"><span data-stu-id="ac725-130">Each instance must be uniquely named.</span></span> <span data-ttu-id="ac725-131">Dans l’exemple suivant, un second bloc de ressources **Service** est ajouté pour configurer le service « DHCP ».</span><span class="sxs-lookup"><span data-stu-id="ac725-131">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the
    # resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as
        # long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service
        # resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="ac725-132">À compter de PowerShell 5.0, IntelliSense a été ajouté pour DSC.</span><span class="sxs-lookup"><span data-stu-id="ac725-132">Beginning in PowerShell 5.0, IntelliSense was added for DSC.</span></span> <span data-ttu-id="ac725-133">Cette nouvelle fonctionnalité permet d’utiliser les touches <kbd>Tab</kbd> et <kbd>Ctrl</kbd>+<kbd>Espace</kbd> pour l’autocomplétion des noms de clés.</span><span class="sxs-lookup"><span data-stu-id="ac725-133">This new feature allows you to use <kbd>TAB</kbd> and <kbd>Ctr</kbd>+<kbd>Space</kbd> to auto-complete key names.</span></span>

![Ressource IntelliSense qui utilise la complétion avec la touche Tab](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a><span data-ttu-id="ac725-135">Types de ressources</span><span class="sxs-lookup"><span data-stu-id="ac725-135">Types of resources</span></span>

<span data-ttu-id="ac725-136">Windows est fourni avec des ressources intégrées et Linux possède des ressources propres au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="ac725-136">Windows comes with built in resources and Linux has OS specific resources.</span></span> <span data-ttu-id="ac725-137">Il existe des ressources pour les [dépendances inter-nœuds](../configurations/crossNodeDependencies.md), des ressources de gestion des packages, ainsi que des [ressources détenues et gérées par la communauté](https://github.com/dsccommunity).</span><span class="sxs-lookup"><span data-stu-id="ac725-137">There are resources for [cross-node dependencies](../configurations/crossNodeDependencies.md), package management resources, as well as [community owned and maintained resources](https://github.com/dsccommunity).</span></span> <span data-ttu-id="ac725-138">Vous pouvez suivre les étapes ci-dessus pour déterminer la syntaxe de ces ressources et savoir comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="ac725-138">You can use the above steps to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="ac725-139">Les pages qui utilisent ces ressources ont été archivées sous **Référence**.</span><span class="sxs-lookup"><span data-stu-id="ac725-139">The pages that serve these resources have been archived under **Reference**.</span></span>

### <a name="windows-built-in-resources"></a><span data-ttu-id="ac725-140">Ressources intégrées Windows</span><span class="sxs-lookup"><span data-stu-id="ac725-140">Windows built-in resources</span></span>

- [<span data-ttu-id="ac725-141">Ressource Archive</span><span class="sxs-lookup"><span data-stu-id="ac725-141">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
- [<span data-ttu-id="ac725-142">Ressource Environment</span><span class="sxs-lookup"><span data-stu-id="ac725-142">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
- [<span data-ttu-id="ac725-143">Ressource File</span><span class="sxs-lookup"><span data-stu-id="ac725-143">File Resource</span></span>](../reference/resources/windows/fileResource.md)
- [<span data-ttu-id="ac725-144">Ressource Group</span><span class="sxs-lookup"><span data-stu-id="ac725-144">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
- [<span data-ttu-id="ac725-145">Ressource GroupSet</span><span class="sxs-lookup"><span data-stu-id="ac725-145">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
- [<span data-ttu-id="ac725-146">Ressource Log</span><span class="sxs-lookup"><span data-stu-id="ac725-146">Log Resource</span></span>](../reference/resources/windows/logResource.md)
- [<span data-ttu-id="ac725-147">Ressource Package</span><span class="sxs-lookup"><span data-stu-id="ac725-147">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
- [<span data-ttu-id="ac725-148">Ressource ProcessSet</span><span class="sxs-lookup"><span data-stu-id="ac725-148">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
- [<span data-ttu-id="ac725-149">Ressources Registry</span><span class="sxs-lookup"><span data-stu-id="ac725-149">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
- [<span data-ttu-id="ac725-150">Ressource Script</span><span class="sxs-lookup"><span data-stu-id="ac725-150">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
- [<span data-ttu-id="ac725-151">Ressource Service</span><span class="sxs-lookup"><span data-stu-id="ac725-151">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
- [<span data-ttu-id="ac725-152">Ressource ServiceSet</span><span class="sxs-lookup"><span data-stu-id="ac725-152">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
- [<span data-ttu-id="ac725-153">Ressource User</span><span class="sxs-lookup"><span data-stu-id="ac725-153">User Resource</span></span>](../reference/resources/windows/userResource.md)
- [<span data-ttu-id="ac725-154">Ressource WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="ac725-154">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
- [<span data-ttu-id="ac725-155">Ressource WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="ac725-155">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
- [<span data-ttu-id="ac725-156">Ressource WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="ac725-156">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [<span data-ttu-id="ac725-157">Ressource WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="ac725-157">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [<span data-ttu-id="ac725-158">Ressource WindowsPackageCabResource</span><span class="sxs-lookup"><span data-stu-id="ac725-158">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
- [<span data-ttu-id="ac725-159">Ressource WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="ac725-159">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a><span data-ttu-id="ac725-160">Ressources de dépendance entre les nœuds</span><span class="sxs-lookup"><span data-stu-id="ac725-160">Cross-Node dependency resources</span></span>

- [<span data-ttu-id="ac725-161">Ressource WaitForAll</span><span class="sxs-lookup"><span data-stu-id="ac725-161">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
- [<span data-ttu-id="ac725-162">Ressource WaitForSome</span><span class="sxs-lookup"><span data-stu-id="ac725-162">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
- [<span data-ttu-id="ac725-163">Ressource WaitForAny</span><span class="sxs-lookup"><span data-stu-id="ac725-163">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a><span data-ttu-id="ac725-164">Ressources Package Management</span><span class="sxs-lookup"><span data-stu-id="ac725-164">Package Management resources</span></span>

- [<span data-ttu-id="ac725-165">Ressource PackageManagement</span><span class="sxs-lookup"><span data-stu-id="ac725-165">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [<span data-ttu-id="ac725-166">Ressource PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="ac725-166">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a><span data-ttu-id="ac725-167">Ressources Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-167">Linux resources</span></span>

- [<span data-ttu-id="ac725-168">Ressource Archive Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-168">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
- [<span data-ttu-id="ac725-169">Ressource Environment Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-169">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
- [<span data-ttu-id="ac725-170">Ressources FileLine Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-170">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
- [<span data-ttu-id="ac725-171">Ressource File Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-171">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
- [<span data-ttu-id="ac725-172">Ressource Group Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-172">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
- [<span data-ttu-id="ac725-173">Ressource Package Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-173">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
- [<span data-ttu-id="ac725-174">Ressource Script Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-174">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
- [<span data-ttu-id="ac725-175">Ressource Service Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-175">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
- [<span data-ttu-id="ac725-176">Ressource SshAuthorizedKeys Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-176">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [<span data-ttu-id="ac725-177">Ressource User Linux</span><span class="sxs-lookup"><span data-stu-id="ac725-177">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
