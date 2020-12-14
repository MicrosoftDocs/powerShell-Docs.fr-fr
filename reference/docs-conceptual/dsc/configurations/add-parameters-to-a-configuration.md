---
ms.date: 12/12/2018
keywords: dsc,powershell,ressource,galerie,configuration
title: Ajouter des paramètres à une configuration
description: Les configurations DSC peuvent être paramétrées pour offrir des configurations plus dynamiques selon les données entrées par l’utilisateur.
ms.openlocfilehash: 72f3cf9efb5d99170e71992bed86a20a57132250
ms.sourcegitcommit: 62282bb9c36fea3b4290b9263c1cd8e9ac216e29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96470330"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="d4fdf-104">Ajouter des paramètres à une configuration</span><span class="sxs-lookup"><span data-stu-id="d4fdf-104">Add Parameters to a Configuration</span></span>

<span data-ttu-id="d4fdf-105">Comme les fonctions, les [configurations](configurations.md) peuvent être paramétrées pour offrir des configurations plus dynamiques selon les données entrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-105">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="d4fdf-106">Les étapes sont similaires à celles décrites dans la section [Fonctions avec paramètres](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="d4fdf-106">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="d4fdf-107">Cet exemple commence avec une configuration de base qui définit le service « Spooler » sur « Running » (En cours d’exécution).</span><span class="sxs-lookup"><span data-stu-id="d4fdf-107">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="d4fdf-108">Paramètres de configuration intégrés</span><span class="sxs-lookup"><span data-stu-id="d4fdf-108">Built-in Configuration parameters</span></span>

<span data-ttu-id="d4fdf-109">Mais contrairement à une fonction, l’attribut [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) n’ajoute aucune fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-109">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="d4fdf-110">Outre les [paramètres communs](/powershell/module/microsoft.powershell.core/about/about_commonparameters), les configurations peuvent également utiliser les paramètres intégrés suivants, sans que vous ayez à les définir.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-110">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|        <span data-ttu-id="d4fdf-111">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d4fdf-111">Parameter</span></span>        |                                         <span data-ttu-id="d4fdf-112">Description</span><span class="sxs-lookup"><span data-stu-id="d4fdf-112">Description</span></span>                                          |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| `-InstanceName`         | <span data-ttu-id="d4fdf-113">Permet de définir des [configurations composites](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="d4fdf-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-DependsOn`            | <span data-ttu-id="d4fdf-114">Permet de définir des [configurations composites](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="d4fdf-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-PSDSCRunAsCredential` | <span data-ttu-id="d4fdf-115">Permet de définir des [configurations composites](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="d4fdf-115">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-ConfigurationData`    | <span data-ttu-id="d4fdf-116">Permet de transmettre des [données de configuration](configData.md) structurées à utiliser dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-116">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span> |
| `-OutputPath`           | <span data-ttu-id="d4fdf-117">Permet de spécifier l’emplacement où votre fichier « \<computername\>.mof » sera compilé</span><span class="sxs-lookup"><span data-stu-id="d4fdf-117">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>                      |

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="d4fdf-118">Ajout de vos propres paramètres à des configurations</span><span class="sxs-lookup"><span data-stu-id="d4fdf-118">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="d4fdf-119">Outre les paramètres intégrés, vous pouvez également ajouter vos propres paramètres à vos configurations.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-119">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span>
<span data-ttu-id="d4fdf-120">Le bloc de paramètres est placé directement dans la déclaration de la configuration, exactement comme une fonction.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-120">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="d4fdf-121">Un bloc de paramètres de configuration doit être placé en dehors de toute déclaration de **nœud** et avant toute instruction *import*.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-121">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="d4fdf-122">En ajoutant des paramètres, vous pouvez rendre vos configurations plus robustes et dynamiques.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-122">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="d4fdf-123">Ajouter un paramètre ComputerName</span><span class="sxs-lookup"><span data-stu-id="d4fdf-123">Add a ComputerName parameter</span></span>

<span data-ttu-id="d4fdf-124">Le premier paramètre que vous pouvez ajouter est un paramètre `-Computername` afin de compiler dynamiquement un fichier « .mof » pour tout paramètre `-Computername` que vous transmettez à votre configuration.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-124">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="d4fdf-125">Comme pour les fonctions, vous pouvez également définir une valeur par défaut, au cas où l’utilisateur ne transmet aucune valeur pour `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="d4fdf-125">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="d4fdf-126">Au sein de votre configuration, vous pouvez alors spécifier votre paramètre `-ComputerName` lors de la définition de votre bloc de nœud.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-126">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="d4fdf-127">Appel de votre configuration avec des paramètres</span><span class="sxs-lookup"><span data-stu-id="d4fdf-127">Calling your Configuration with parameters</span></span>

<span data-ttu-id="d4fdf-128">Après avoir ajouté des paramètres à votre configuration, vous pouvez les utiliser comme s’il s’agissait d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-128">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="d4fdf-129">Compilation de plusieurs fichiers .mof</span><span class="sxs-lookup"><span data-stu-id="d4fdf-129">Compiling multiple .mof files</span></span>

<span data-ttu-id="d4fdf-130">Le bloc de nœud peut également accepter une liste séparée par des virgules de noms d’ordinateurs, et générer des fichiers « .mof » pour chacun de ces ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-130">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="d4fdf-131">Vous pouvez exécuter l’exemple suivant afin de générer des fichiers « .mof » pour tous les ordinateurs transmis au paramètre `-ComputerName`.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-131">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String[]]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="d4fdf-132">Paramètres avancés dans les configurations</span><span class="sxs-lookup"><span data-stu-id="d4fdf-132">Advanced parameters in Configurations</span></span>

<span data-ttu-id="d4fdf-133">Outre un paramètre `-ComputerName`, nous pouvons ajouter des paramètres pour le nom du service et l’état.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-133">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span>
<span data-ttu-id="d4fdf-134">L’exemple suivant ajoute un bloc de paramètres avec un paramètre `-ServiceName` et l’utilise pour définir dynamiquement le bloc de ressources **Service**.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-134">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="d4fdf-135">Il ajoute également un paramètre `-State` pour définir dynamiquement l’**état** dans le bloc de ressources **Service**.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-135">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="d4fdf-136">Dans des scénarios plus complexes, il peut être plus judicieux de déplacer vos données dynamiques vers des [données de configuration](configData.md) structurées.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-136">In more advanced scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="d4fdf-137">L’exemple de configuration utilise désormais un paramètre `$ServiceName` dynamique, mais si aucune valeur n’est spécifiée, la compilation génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-137">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="d4fdf-138">Vous pouvez ajouter une valeur par défaut, comme dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-138">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="d4fdf-139">Mais dans cette instance, il est plus judicieux de forcer simplement l’utilisateur à spécifier une valeur pour le paramètre `$ServiceName`.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-139">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="d4fdf-140">L’attribut `parameter` vous permet d’ajouter une prise en charge de validation et de pipeline pour les paramètres de votre configuration.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-140">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="d4fdf-141">Au-dessus de toute déclaration de paramètre, ajoutez le bloc d’attributs `parameter`, comme dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-141">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="d4fdf-142">Vous pouvez spécifier des arguments pour chaque attribut `parameter` afin de contrôler divers aspects du paramètre défini.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-142">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="d4fdf-143">L’exemple suivant fait du paramètre `$ServiceName` un paramètre **obligatoire**.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-143">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="d4fdf-144">Pour le paramètre `$State`, nous aimerions empêcher l’utilisateur de spécifier des valeurs en dehors d’un ensemble prédéfini, par exemple Running (en cours d’exécution) ou Stopped (arrêté). L’attribut `ValidationSet*` empêche l’utilisateur de spécifier des valeurs en dehors d’un ensemble prédéfini, par exemple Running (en cours d’exécution) ou Stopped (arrêté).</span><span class="sxs-lookup"><span data-stu-id="d4fdf-144">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="d4fdf-145">L’exemple suivant ajoute l’attribut `ValidationSet` au paramètre `$State`.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-145">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="d4fdf-146">Comme nous ne souhaitons pas rendre le paramètre `$State`**obligatoire**, nous devrons lui ajouter une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-146">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="d4fdf-147">Vous n’avez pas besoin de spécifier un attribut `parameter` lorsque vous utilisez un attribut `validation`.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-147">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="d4fdf-148">Pour en savoir plus sur les `parameter` et les attributs de validation, consultez [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span><span class="sxs-lookup"><span data-stu-id="d4fdf-148">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="d4fdf-149">Configuration entièrement paramétrable</span><span class="sxs-lookup"><span data-stu-id="d4fdf-149">Fully parameterized Configuration</span></span>

<span data-ttu-id="d4fdf-150">Nous disposons désormais d’une configuration paramétrable qui oblige l’utilisateur à spécifier des valeurs `-InstanceName`, `-ServiceName`, et qui valide le paramètre `-State`.</span><span class="sxs-lookup"><span data-stu-id="d4fdf-150">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="d4fdf-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4fdf-151">See also</span></span>

- [<span data-ttu-id="d4fdf-152">Écrire une aide pour les configurations DSC</span><span class="sxs-lookup"><span data-stu-id="d4fdf-152">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="d4fdf-153">Configurations dynamiques</span><span class="sxs-lookup"><span data-stu-id="d4fdf-153">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="d4fdf-154">Utiliser des données de configuration dans vos configurations</span><span class="sxs-lookup"><span data-stu-id="d4fdf-154">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="d4fdf-155">Séparer des données de configuration et d’environnement</span><span class="sxs-lookup"><span data-stu-id="d4fdf-155">Separate configuration and environment data</span></span>](separatingEnvData.md)
