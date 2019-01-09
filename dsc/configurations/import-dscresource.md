---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Utilisation d’Import-DSCResource
ms.openlocfilehash: 6bc3c1aa1d34a05e3188666da825322235c0672e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401593"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="35718-103">Utilisation d’Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="35718-103">Using Import-DSCResource</span></span>

<span data-ttu-id="35718-104">`Import-DScResource` est un mot clé dynamique, ce qui peut être utilisé uniquement dans un bloc de script de Configuration.</span><span class="sxs-lookup"><span data-stu-id="35718-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="35718-105">Le `Import-DSCResource` mot clé pour importer toutes les ressources nécessaires dans votre Configuration.</span><span class="sxs-lookup"><span data-stu-id="35718-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="35718-106">Ressources sous `$phsome` sont importés automatiquement, mais il est toujours considéré comme bonne pratique consiste à importer explicitement toutes les ressources utilisées dans votre [Configuration](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="35718-106">Resources under `$phsome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="35718-107">La syntaxe pour `Import-DSCResource` est indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="35718-107">The syntax for `Import-DSCResource` is shown below.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>]
```

|<span data-ttu-id="35718-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="35718-108">Parameter</span></span>  |<span data-ttu-id="35718-109">Description</span><span class="sxs-lookup"><span data-stu-id="35718-109">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="35718-110">Les noms des ressources DSC que vous devez importer.</span><span class="sxs-lookup"><span data-stu-id="35718-110">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="35718-111">Si le nom du module est spécifié, la commande recherche ces ressources DSC dans ce module ; Sinon, la commande recherche les ressources DSC dans tous les chemins d’accès de ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="35718-111">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="35718-112">Les caractères génériques sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="35718-112">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="35718-113">L’ou les noms de module conteneur, ou le module/des spécifications.</span><span class="sxs-lookup"><span data-stu-id="35718-113">The container module name(s), or module specification(s).</span></span>  <span data-ttu-id="35718-114">Si vous spécifiez les ressources à importer à partir d’un module, la commande tente d’importer uniquement les ressources.</span><span class="sxs-lookup"><span data-stu-id="35718-114">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="35718-115">Si vous spécifiez uniquement le module, la commande importe toutes les ressources DSC dans le module.</span><span class="sxs-lookup"><span data-stu-id="35718-115">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

<span data-ttu-id="35718-116">Vous pouvez utiliser des caractères génériques avec la `-Name` paramètre lors de l’utilisation `Import-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="35718-116">You can use wildcards with the `-Name` parameter when using `Import-DSCResource`.</span></span>

```powershell
Import-DscResource -Name * -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="35718-117">Exemple : Utilisez Import-DSCResource au sein d’une configuration</span><span class="sxs-lookup"><span data-stu-id="35718-117">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName MS_DSC1 -name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    Import-DSCResource -Name File, TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
...
```

> [!NOTE]
> <span data-ttu-id="35718-118">Spécification de plusieurs valeurs pour les noms de ressources et les noms de modules dans la même commande ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="35718-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="35718-119">Il peut avoir un comportement non déterminant sur quelle ressource à charger à partir de quel module au cas où même ressource existe dans plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="35718-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="35718-120">Commande ci-dessous entraîne erreur pendant la compilation.</span><span class="sxs-lookup"><span data-stu-id="35718-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="35718-121">Éléments à prendre en compte lorsque vous utilisez uniquement le paramètre Name :</span><span class="sxs-lookup"><span data-stu-id="35718-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="35718-122">C’est une opération gourmande en ressources en fonction du nombre de modules installés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="35718-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="35718-123">Il charge la première ressource trouvée avec le nom donné.</span><span class="sxs-lookup"><span data-stu-id="35718-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="35718-124">Dans le cas où il existe plusieurs ressources avec le même nom installé, il peut charger la ressource incorrecte.</span><span class="sxs-lookup"><span data-stu-id="35718-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="35718-125">L’utilisation recommandée consiste à spécifier `–ModuleName` avec la `-Name` paramètre, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="35718-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="35718-126">Cette utilisation présente les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="35718-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="35718-127">Elle réduit l’impact sur les performances en limitant l’étendue de recherche pour la ressource spécifiée.</span><span class="sxs-lookup"><span data-stu-id="35718-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="35718-128">Elle définit explicitement le module de définition de la ressource, en garantissant que la ressource correcte est chargée.</span><span class="sxs-lookup"><span data-stu-id="35718-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="35718-129">Dans PowerShell 5.0, les ressources DSC peuvent avoir plusieurs versions et celles-ci peuvent être installées sur un ordinateur côte à côte.</span><span class="sxs-lookup"><span data-stu-id="35718-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="35718-130">L’implémentation inclut plusieurs versions d’un module de ressource qui sont contenues dans le même dossier de module.</span><span class="sxs-lookup"><span data-stu-id="35718-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="35718-131">Pour plus d’informations, consultez [Utilisation de ressources avec plusieurs versions](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="35718-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="35718-132">IntelliSense avec Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="35718-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="35718-133">Lorsque vous créez la configuration DSC dans ISE, PowerShell fournit IntelliSence pour les ressources et les propriétés de ressource.</span><span class="sxs-lookup"><span data-stu-id="35718-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="35718-134">Définitions de ressource sous la `$pshome` chemin d’accès du module sont chargés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="35718-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="35718-135">Lorsque vous importez des ressources à l’aide de la `Import-DSCResource` mot clé, les définitions de ressources spécifié sont ajoutées et Intellisense est développé pour inclure le schéma de la ressource importée.</span><span class="sxs-lookup"><span data-stu-id="35718-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Intellisense de ressources](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="35718-137">À compter de PowerShell 5.0, la saisie semi-automatique par tabulation a été ajoutée à l’environnement ISE pour les ressources DSC et leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="35718-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="35718-138">Pour plus d’informations, consultez [ressources](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="35718-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="35718-139">Lors de la compilation de la Configuration, PowerShell utilise les définitions de ressource importée pour valider tous les blocs de ressources dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="35718-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="35718-140">Chaque bloc de ressources est validé, à l’aide de la définition de schéma de la ressource pour les règles suivantes.</span><span class="sxs-lookup"><span data-stu-id="35718-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="35718-141">Seules les propriétés définies dans le schéma sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="35718-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="35718-142">Les types de données pour chaque propriété sont corrects.</span><span class="sxs-lookup"><span data-stu-id="35718-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="35718-143">Propriétés de clés sont spécifiées.</span><span class="sxs-lookup"><span data-stu-id="35718-143">Keys properties are specified.</span></span>
- <span data-ttu-id="35718-144">Aucune propriété en lecture seule n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="35718-144">No read-only property is used.</span></span>
- <span data-ttu-id="35718-145">Mappe les types de validation de valeur.</span><span class="sxs-lookup"><span data-stu-id="35718-145">Validation on value maps types.</span></span>

<span data-ttu-id="35718-146">Prenez en compte la configuration suivante :</span><span class="sxs-lookup"><span data-stu-id="35718-146">Consider the following configuration:</span></span>

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="35718-147">Résultats de cette Configuration dans une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="35718-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="35718-148">IntelliSense et le schéma de validation permettent d’intercepter les erreurs plus au moment de l’analyse et de compilation, éviter les complications au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="35718-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="35718-149">Chaque ressource DSC peut avoir un nom et un **FriendlyName** défini par le schéma de la ressource.</span><span class="sxs-lookup"><span data-stu-id="35718-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="35718-150">Voici les deux premières lignes de « MSFT_ServiceResource.shema.mof ».</span><span class="sxs-lookup"><span data-stu-id="35718-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="35718-151">Lorsque vous utilisez cette ressource dans une Configuration, vous pouvez spécifier **MSFT_ServiceResource** ou **Service**.</span><span class="sxs-lookup"><span data-stu-id="35718-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="35718-152">Différences de v4 et v5 PowerShell</span><span class="sxs-lookup"><span data-stu-id="35718-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="35718-153">Il existe plusieurs différences que vous voyez lors de la création de Configurations dans Visual Studio PowerShell 4.0. PowerShell 5.0 et versions ultérieur.</span><span class="sxs-lookup"><span data-stu-id="35718-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="35718-154">Cette section met en évidence les différences que vous consultez pertinents pour cet article.</span><span class="sxs-lookup"><span data-stu-id="35718-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="35718-155">Plusieurs Versions de ressources</span><span class="sxs-lookup"><span data-stu-id="35718-155">Multiple Resource Versions</span></span>

<span data-ttu-id="35718-156">Installation et l’utilisation de plusieurs versions de ressources côte à côte n’était pas pris en charge dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="35718-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="35718-157">Si vous remarquez des problèmes d’importation de ressources dans votre Configuration, assurez-vous que vous avez uniquement une version de la ressource installée.</span><span class="sxs-lookup"><span data-stu-id="35718-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="35718-158">Dans l’image ci-dessous, deux versions de la **xPSDesiredStateConfiguration** module sont installés.</span><span class="sxs-lookup"><span data-stu-id="35718-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Plusieurs Versions des ressources fixées](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="35718-160">Copiez le contenu de votre version du module souhaité dans le niveau supérieur du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="35718-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Plusieurs Versions des ressources fixées](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="35718-162">Emplacement de la ressource</span><span class="sxs-lookup"><span data-stu-id="35718-162">Resource location</span></span>

<span data-ttu-id="35718-163">Lorsque vous créez et compilation de Configurations, vos ressources peuvent être stockées dans un répertoire spécifié par votre [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="35718-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="35718-164">Dans PowerShell 4.0, le LCM nécessite tous les modules de ressources DSC soient stockées sous « Programme Files\WindowsPowerShell\Modules » ou `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="35718-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="35718-165">À compter de PowerShell 5.0, cette exigence a été supprimée, et les modules de ressources peuvent être stockées dans un répertoire spécifié par `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="35718-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="35718-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35718-166">See also</span></span>

- [<span data-ttu-id="35718-167">Ressources</span><span class="sxs-lookup"><span data-stu-id="35718-167">Resources</span></span>](../resources/resources.md)
