---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Ressources DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076620"
---
# <a name="dsc-resources"></a><span data-ttu-id="9324d-103">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="9324d-103">DSC Resources</span></span>

><span data-ttu-id="9324d-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9324d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9324d-105">Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="9324d-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="9324d-106">Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9324d-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="9324d-107">Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="9324d-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="9324d-108">Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.</span><span class="sxs-lookup"><span data-stu-id="9324d-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="9324d-109">Chaque ressource comporte un \*schéma qui détermine la syntaxe nécessaire pour utiliser la ressource dans une [configuration](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="9324d-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="9324d-110">Le schéma d’une ressource peut être défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="9324d-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="9324d-111">Fichier **'Schema.Mof'**  : La plupart des ressources définissent leur *schéma* dans un fichier « Schema.MOF » à l’aide de [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="9324d-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="9324d-112">Fichier **'\<Nom de la ressource\>.schema.psm1'**  : Les [ressources composites](../configurations/compositeConfigs.md) définissent leur *schéma* dans un fichier '<ResourceName>.schema.psm1' à l’aide d’un [bloc de paramètres](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="9324d-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="9324d-113">Fichier **'\<Nom de la ressource\>.psm1'**  : Les ressources DSC basées sur la classe définissent leur *schéma* dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="9324d-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="9324d-114">Les éléments de syntaxe sont signalés en tant que propriétés de classe.</span><span class="sxs-lookup"><span data-stu-id="9324d-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="9324d-115">Pour plus d’informations, consultez [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="9324d-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="9324d-116">Pour récupérer la syntaxe d’une ressource DSC, utilisez l’applet de commande [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) avec le paramètre `-Syntax`.</span><span class="sxs-lookup"><span data-stu-id="9324d-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="9324d-117">Cette méthode est similaire à l’utilisation de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) avec le paramètre `-Syntax` pour obtenir la syntaxe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9324d-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="9324d-118">Le résultat affichera le modèle utilisé pour un bloc de ressources correspondant à la ressource que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="9324d-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="9324d-119">Le résultat devrait être similaire à ce qui suit, même si la syntaxe de la ressource risque de change à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="9324d-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="9324d-120">Comme dans la syntaxe de l’applet de commande, les *clés* affichées entre crochets sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="9324d-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="9324d-121">Les types spécifient le type de données attendu par chaque clé.</span><span class="sxs-lookup"><span data-stu-id="9324d-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="9324d-122">La clé **Ensure** (garantir) est facultative car les valeurs par défaut sont définies sur « Present ».</span><span class="sxs-lookup"><span data-stu-id="9324d-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="9324d-123">Dans une configuration, un bloc de ressources **Service** peut ressembler à ceci pour **garantir** que le service Spooler est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9324d-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="9324d-124">Avant d’utiliser une ressource dans une configuration, vous devez l’importer à l’aide d’[Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="9324d-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="9324d-125">Les configurations peuvent contenir plusieurs instances du même type de ressource.</span><span class="sxs-lookup"><span data-stu-id="9324d-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="9324d-126">Chaque instance doit afficher un nom unique.</span><span class="sxs-lookup"><span data-stu-id="9324d-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="9324d-127">Dans l’exemple suivant, un second bloc de ressources **Service** est ajouté pour configurer le service « DHCP ».</span><span class="sxs-lookup"><span data-stu-id="9324d-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="9324d-128">À compter de PowerShell 5.0, IntelliSense a été ajouté pour DSC.</span><span class="sxs-lookup"><span data-stu-id="9324d-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="9324d-129">Cette nouvelle fonctionnalité vous permet d’utiliser les touches \<Tab\> et \<Ctrl+Eespace\> pour la saisie automatique des noms de clés.</span><span class="sxs-lookup"><span data-stu-id="9324d-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Saisie semi-automatique des ressources via la touche Tab](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="9324d-131">Ressources intégrées</span><span class="sxs-lookup"><span data-stu-id="9324d-131">Built-in resources</span></span>

<span data-ttu-id="9324d-132">En plus des ressources de la Communauté, il existe des ressources intégrées pour Windows, pour Linux, et des ressources pour les dépendances entre les nœuds.</span><span class="sxs-lookup"><span data-stu-id="9324d-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="9324d-133">Vous pouvez utiliser les étapes ci-dessus pour déterminer la syntaxe de ces ressources et comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="9324d-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="9324d-134">Les pages qui utilisent ces ressources ont été archivées sous **Référence**.</span><span class="sxs-lookup"><span data-stu-id="9324d-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="9324d-135">Ressources intégrées Windows</span><span class="sxs-lookup"><span data-stu-id="9324d-135">Windows built-in resources</span></span>

* [<span data-ttu-id="9324d-136">Ressource Archive</span><span class="sxs-lookup"><span data-stu-id="9324d-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="9324d-137">Ressource Environment</span><span class="sxs-lookup"><span data-stu-id="9324d-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="9324d-138">Ressource File</span><span class="sxs-lookup"><span data-stu-id="9324d-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="9324d-139">Ressource Group</span><span class="sxs-lookup"><span data-stu-id="9324d-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="9324d-140">Ressource GroupSet</span><span class="sxs-lookup"><span data-stu-id="9324d-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="9324d-141">Ressource Log</span><span class="sxs-lookup"><span data-stu-id="9324d-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="9324d-142">Ressource Package</span><span class="sxs-lookup"><span data-stu-id="9324d-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="9324d-143">Ressource ProcessSet</span><span class="sxs-lookup"><span data-stu-id="9324d-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="9324d-144">Ressources Registry</span><span class="sxs-lookup"><span data-stu-id="9324d-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="9324d-145">Ressource Script</span><span class="sxs-lookup"><span data-stu-id="9324d-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="9324d-146">Ressource Service</span><span class="sxs-lookup"><span data-stu-id="9324d-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="9324d-147">Ressource ServiceSet</span><span class="sxs-lookup"><span data-stu-id="9324d-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="9324d-148">Ressource User</span><span class="sxs-lookup"><span data-stu-id="9324d-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="9324d-149">Ressource WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="9324d-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="9324d-150">Ressource WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="9324d-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="9324d-151">Ressource WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="9324d-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="9324d-152">Ressource WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="9324d-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="9324d-153">Ressource WindowsPackageCabResource</span><span class="sxs-lookup"><span data-stu-id="9324d-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="9324d-154">Ressource WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="9324d-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="9324d-155">Ressources de [dépendances entre les nœuds](../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="9324d-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="9324d-156">Ressource WaitForAll</span><span class="sxs-lookup"><span data-stu-id="9324d-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="9324d-157">Ressource WaitForSome</span><span class="sxs-lookup"><span data-stu-id="9324d-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="9324d-158">Ressource WaitForAny</span><span class="sxs-lookup"><span data-stu-id="9324d-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="9324d-159">Ressources Package Management</span><span class="sxs-lookup"><span data-stu-id="9324d-159">Package Management resources</span></span>

* [<span data-ttu-id="9324d-160">Ressource PackageManagement</span><span class="sxs-lookup"><span data-stu-id="9324d-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="9324d-161">Ressource PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="9324d-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="9324d-162">Ressources Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-162">Linux resources</span></span>

* [<span data-ttu-id="9324d-163">Ressource Archive Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="9324d-164">Ressource Environment Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="9324d-165">Ressources FileLine Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="9324d-166">Ressource File Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="9324d-167">Ressource Group Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="9324d-168">Ressource Package Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="9324d-169">Ressource Script Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="9324d-170">Ressource Service Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="9324d-171">Ressource SshAuthorizedKeys Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="9324d-172">Ressource User Linux</span><span class="sxs-lookup"><span data-stu-id="9324d-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
