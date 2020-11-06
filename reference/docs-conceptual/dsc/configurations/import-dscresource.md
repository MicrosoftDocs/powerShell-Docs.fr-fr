---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,installation
title: Utilisation d’Import-DSCResource
description: Import-DSCResource est un mot clé dynamique, qui peut être utilisé uniquement dans un bloc de script de configuration. Il est utilisé pour importer les modules de ressources nécessaires dans votre configuration.
ms.openlocfilehash: f6dcad2c56848ec25eb79332c96fe6b0d438fe95
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658518"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="c10e8-105">Utilisation d’Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="c10e8-105">Using Import-DSCResource</span></span>

<span data-ttu-id="c10e8-106">`Import-DSCResource` est un mot clé dynamique, qui ne peut être utilisé qu’à l’intérieur d’un bloc de script de configuration pour importer toutes les ressources nécessaires dans votre configuration.</span><span class="sxs-lookup"><span data-stu-id="c10e8-106">`Import-DSCResource` is a dynamic keyword, which can only be used inside a Configuration script block to import any resources needed in your Configuration.</span></span> <span data-ttu-id="c10e8-107">Les ressources sous `$PSHOME` sont importées automatiquement, mais il est toujours préférable d’importer explicitement toutes les ressources utilisées dans votre [configuration](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c10e8-107">Resources under `$PSHOME` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="c10e8-108">La syntaxe pour `Import-DSCResource` est indiquée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c10e8-108">The syntax for `Import-DSCResource` is shown below.</span></span> <span data-ttu-id="c10e8-109">Lorsque vous spécifiez des modules par nom, il est nécessaire de répertorier chacun de ces modules sur une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="c10e8-109">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|    <span data-ttu-id="c10e8-110">Paramètre</span><span class="sxs-lookup"><span data-stu-id="c10e8-110">Parameter</span></span>     |                                                                                                                      <span data-ttu-id="c10e8-111">Description</span><span class="sxs-lookup"><span data-stu-id="c10e8-111">Description</span></span>                                                                                                                      |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-Name`          | <span data-ttu-id="c10e8-112">Les noms des ressources DSC que vous devez importer.</span><span class="sxs-lookup"><span data-stu-id="c10e8-112">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="c10e8-113">Si le nom du module est spécifié, la commande recherche ces ressources DSC dans ce module ; sinon, la commande recherche les ressources DSC dans tous leurs chemins d’accès.</span><span class="sxs-lookup"><span data-stu-id="c10e8-113">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="c10e8-114">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c10e8-114">Wildcards are supported.</span></span> |
| `-ModuleName`    | <span data-ttu-id="c10e8-115">Le nom du module, ou une spécification de module.</span><span class="sxs-lookup"><span data-stu-id="c10e8-115">The module name, or module specification.</span></span>  <span data-ttu-id="c10e8-116">Si vous spécifiez les ressources à importer à partir d’un module, la commande tente d’importer uniquement ces ressources.</span><span class="sxs-lookup"><span data-stu-id="c10e8-116">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="c10e8-117">Si vous spécifiez uniquement le module, la commande importe toutes les ressources DSC dans le module.</span><span class="sxs-lookup"><span data-stu-id="c10e8-117">If you specify the module only, the command imports all the DSC resources in the module.</span></span>            |
| `-ModuleVersion` | <span data-ttu-id="c10e8-118">À compter de PowerShell 5.0, vous pouvez spécifier la version d’un module qu’une configuration doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="c10e8-118">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span></span> <span data-ttu-id="c10e8-119">Pour plus d’informations, consultez [Importer une version spécifique d’une ressource installée](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="c10e8-119">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span></span>                                                    |

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="c10e8-120">Exemple : Utiliser Import-DSCResource au sein d’une configuration</span><span class="sxs-lookup"><span data-stu-id="c10e8-120">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> <span data-ttu-id="c10e8-121">La spécification de plusieurs valeurs pour les noms de ressources et les noms de modules dans la même commande n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="c10e8-121">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span>
> <span data-ttu-id="c10e8-122">Un comportement non déterminant permet de choisir quelle ressource charger à partir de quel module, au cas où une même ressource existe dans plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="c10e8-122">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="c10e8-123">La commande ci-dessous génère une erreur pendant la compilation.</span><span class="sxs-lookup"><span data-stu-id="c10e8-123">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="c10e8-124">Éléments à prendre en compte lorsque vous utilisez uniquement le paramètre Name :</span><span class="sxs-lookup"><span data-stu-id="c10e8-124">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="c10e8-125">Cette opération nécessite beaucoup de ressources, en fonction du nombre de modules installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c10e8-125">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="c10e8-126">Elle charge la première ressource trouvée avec le nom donné.</span><span class="sxs-lookup"><span data-stu-id="c10e8-126">It will load the first resource found with the given name.</span></span> <span data-ttu-id="c10e8-127">Si plusieurs ressources installées portent le même nom, elle risque de charger la mauvaise ressource.</span><span class="sxs-lookup"><span data-stu-id="c10e8-127">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="c10e8-128">Il est recommandé de spécifier `–ModuleName` avec le paramètre `-Name`, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c10e8-128">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="c10e8-129">Cette méthode offre les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="c10e8-129">This usage has the following benefits:</span></span>

- <span data-ttu-id="c10e8-130">Elle réduit l’impact sur les performances en limitant l’étendue de la recherche pour la ressource spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c10e8-130">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="c10e8-131">Elle précise explicitement le module qui définit la ressource, en garantissant le chargement de la ressource adéquate.</span><span class="sxs-lookup"><span data-stu-id="c10e8-131">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="c10e8-132">Dans PowerShell 5.0, les ressources DSC peuvent avoir plusieurs versions et celles-ci peuvent être installées sur un ordinateur côte à côte.</span><span class="sxs-lookup"><span data-stu-id="c10e8-132">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="c10e8-133">L’implémentation inclut plusieurs versions d’un module de ressource qui sont contenues dans le même dossier de module.</span><span class="sxs-lookup"><span data-stu-id="c10e8-133">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span> <span data-ttu-id="c10e8-134">Pour plus d’informations, consultez [Utilisation de ressources avec plusieurs versions](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="c10e8-134">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="c10e8-135">IntelliSense avec Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="c10e8-135">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="c10e8-136">Lorsque vous créez la configuration DSC dans ISE, PowerShell fournit à IntelliSence les ressources et les propriétés des ressources.</span><span class="sxs-lookup"><span data-stu-id="c10e8-136">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="c10e8-137">Les définitions de ressources dans le chemin d’accès du module `$pshome` sont automatiquement chargées.</span><span class="sxs-lookup"><span data-stu-id="c10e8-137">Resource definitions under the `$pshome` module path are loaded automatically.</span></span>
<span data-ttu-id="c10e8-138">Lorsque vous importez des ressources à l’aide du mot clé `Import-DSCResource`, les définitions de ressources spécifiées sont ajoutées, et IntelliSense est développé pour inclure le schéma de la ressource importée.</span><span class="sxs-lookup"><span data-stu-id="c10e8-138">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![IntelliSense dans l’ISE d’une ressource DSC](media/import-dscresource/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="c10e8-140">À compter de PowerShell 5.0, la saisie semi-automatique via la touche Tab a été ajoutée à ISE pour les ressources DSC et leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="c10e8-140">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="c10e8-141">Pour plus d’informations, consultez [Ressources](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="c10e8-141">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="c10e8-142">Lors de la compilation de la configuration, PowerShell utilise les définitions de ressources importées pour valider tous les blocs de ressources dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c10e8-142">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span> <span data-ttu-id="c10e8-143">Chaque bloc de ressources est validé à l’aide de la définition de schéma de la ressource, selon les règles suivantes.</span><span class="sxs-lookup"><span data-stu-id="c10e8-143">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="c10e8-144">Seules les propriétés définies dans le schéma sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="c10e8-144">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="c10e8-145">Les types de données pour chaque propriété sont corrects.</span><span class="sxs-lookup"><span data-stu-id="c10e8-145">The data types for each property are correct.</span></span>
- <span data-ttu-id="c10e8-146">Les propriétés de clés sont spécifiées.</span><span class="sxs-lookup"><span data-stu-id="c10e8-146">Keys properties are specified.</span></span>
- <span data-ttu-id="c10e8-147">Aucune propriété en lecture seule n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c10e8-147">No read-only property is used.</span></span>
- <span data-ttu-id="c10e8-148">La validation des valeurs est mappée à des types.</span><span class="sxs-lookup"><span data-stu-id="c10e8-148">Validation on value maps types.</span></span>

<span data-ttu-id="c10e8-149">Considérez la configuration suivante :</span><span class="sxs-lookup"><span data-stu-id="c10e8-149">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

<span data-ttu-id="c10e8-150">La compilation de cette configuration entraîne une erreur.</span><span class="sxs-lookup"><span data-stu-id="c10e8-150">Compiling this Configuration results in an error.</span></span>

```Output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or
valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values:
Present, Absent.
```

<span data-ttu-id="c10e8-151">IntelliSense et le schéma de validation vous permettent de détecter plus d’erreurs lors de l’analyse et de la compilation, évitant des complications au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c10e8-151">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="c10e8-152">Chaque ressource DSC peut avoir un nom et une propriété **FriendlyName** définie par le schéma de la ressource.</span><span class="sxs-lookup"><span data-stu-id="c10e8-152">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="c10e8-153">Voici les deux premières lignes du fichier « MSFT_ServiceResource.shema.mof ».</span><span class="sxs-lookup"><span data-stu-id="c10e8-153">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
>
> <span data-ttu-id="c10e8-154">Lorsque vous utilisez cette ressource dans une configuration, vous pouvez spécifier **MSFT_ServiceResource** ou **Service**.</span><span class="sxs-lookup"><span data-stu-id="c10e8-154">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="c10e8-155">Différences entre PowerShell v4 et PowerShell v5</span><span class="sxs-lookup"><span data-stu-id="c10e8-155">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="c10e8-156">Plusieurs différences apparaissent lors de la création de configurations dans Visual Studio PowerShell 4.0. PowerShell 5.0 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="c10e8-156">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="c10e8-157">Cette section met en évidence les différences pertinentes pour cet article.</span><span class="sxs-lookup"><span data-stu-id="c10e8-157">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="c10e8-158">Plusieurs versions de ressources</span><span class="sxs-lookup"><span data-stu-id="c10e8-158">Multiple Resource Versions</span></span>

<span data-ttu-id="c10e8-159">L’installation et l’utilisation de plusieurs versions de ressources côte à côte n’étaient pas prises en charge dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="c10e8-159">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="c10e8-160">Si vous rencontrez des problèmes d’importation de ressources dans votre configuration, assurez-vous d’utiliser uniquement une version de la ressource installée.</span><span class="sxs-lookup"><span data-stu-id="c10e8-160">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="c10e8-161">Dans l’image ci-dessous, deux versions du module **xPSDesiredStateConfiguration** sont installées.</span><span class="sxs-lookup"><span data-stu-id="c10e8-161">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Plusieurs versions de ressources installées dans le dossier](media/import-dscresource/multiple-resource-versions-broken.png)

<span data-ttu-id="c10e8-163">Copiez le contenu de votre version de module souhaitée dans le niveau supérieur du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="c10e8-163">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Copier la version souhaitée dans le répertoire du module de niveau supérieur](media/import-dscresource/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="c10e8-165">Emplacement de la ressource</span><span class="sxs-lookup"><span data-stu-id="c10e8-165">Resource location</span></span>

<span data-ttu-id="c10e8-166">Lorsque vous créez et compilez des configurations, vos ressources peuvent être stockées dans un répertoire spécifié par [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="c10e8-166">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span></span>
<span data-ttu-id="c10e8-167">Dans PowerShell 4.0, le LCM nécessite le stockage de tous les modules de ressources DSC sous "Program Files\WindowsPowerShell\Modules" ou `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="c10e8-167">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="c10e8-168">À compter de PowerShell 5.0, cette exigence a été supprimée, et les modules de ressources peuvent être stockés dans un répertoire spécifié par `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="c10e8-168">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

### <a name="moduleversion-added"></a><span data-ttu-id="c10e8-169">ModuleVersion ajouté</span><span class="sxs-lookup"><span data-stu-id="c10e8-169">ModuleVersion added</span></span>

<span data-ttu-id="c10e8-170">À compter de PowerShell 5.0, le paramètre `-ModuleVersion` vous permet de spécifier la version d’un module que votre configuration doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="c10e8-170">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="c10e8-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c10e8-171">See also</span></span>

- [<span data-ttu-id="c10e8-172">Ressources</span><span class="sxs-lookup"><span data-stu-id="c10e8-172">Resources</span></span>](../resources/resources.md)
