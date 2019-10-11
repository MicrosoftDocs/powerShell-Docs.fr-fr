---
ms.date: 12/12/2018
keywords: dsc,powershell,ressource,galerie,configuration
title: Ajouter des paramètres à une configuration
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954196"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="108b1-103">Ajouter des paramètres à une configuration</span><span class="sxs-lookup"><span data-stu-id="108b1-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="108b1-104">Comme les fonctions, les [configurations](configurations.md) peuvent être paramétrées pour offrir des configurations plus dynamiques selon les données entrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="108b1-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="108b1-105">Les étapes sont similaires à celles décrites dans la section [Fonctions avec paramètres](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="108b1-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="108b1-106">Cet exemple commence avec une configuration de base qui définit le service « Spooler » sur « Running » (En cours d’exécution).</span><span class="sxs-lookup"><span data-stu-id="108b1-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="108b1-107">Paramètres de configuration intégrés</span><span class="sxs-lookup"><span data-stu-id="108b1-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="108b1-108">Mais contrairement à une fonction, l’attribut [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) n’ajoute aucune fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="108b1-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="108b1-109">Outre les [paramètres communs](/powershell/module/microsoft.powershell.core/about/about_commonparameters), les configurations peuvent également utiliser les paramètres intégrés suivants, sans que vous ayez à les définir.</span><span class="sxs-lookup"><span data-stu-id="108b1-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="108b1-110">Paramètre</span><span class="sxs-lookup"><span data-stu-id="108b1-110">Parameter</span></span>  |<span data-ttu-id="108b1-111">Description</span><span class="sxs-lookup"><span data-stu-id="108b1-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="108b1-112">Permet de définir des [configurations composites](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="108b1-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="108b1-113">Permet de définir des [configurations composites](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="108b1-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="108b1-114">Permet de définir des [configurations composites](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="108b1-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="108b1-115">Permet de transmettre des [données de configuration](configData.md) structurées à utiliser dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="108b1-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="108b1-116">Permet de spécifier l’emplacement où votre fichier « \<computername\>.mof » sera compilé</span><span class="sxs-lookup"><span data-stu-id="108b1-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="108b1-117">Ajout de vos propres paramètres à des configurations</span><span class="sxs-lookup"><span data-stu-id="108b1-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="108b1-118">Outre les paramètres intégrés, vous pouvez également ajouter vos propres paramètres à vos configurations.</span><span class="sxs-lookup"><span data-stu-id="108b1-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="108b1-119">Le bloc de paramètres est placé directement dans la déclaration de la configuration, exactement comme une fonction.</span><span class="sxs-lookup"><span data-stu-id="108b1-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="108b1-120">Un bloc de paramètres de configuration doit être placé en dehors de toute déclaration de **nœud** et avant toute instruction *import*.</span><span class="sxs-lookup"><span data-stu-id="108b1-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="108b1-121">En ajoutant des paramètres, vous pouvez rendre vos configurations plus robustes et dynamiques.</span><span class="sxs-lookup"><span data-stu-id="108b1-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="108b1-122">Ajouter un paramètre ComputerName</span><span class="sxs-lookup"><span data-stu-id="108b1-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="108b1-123">Le premier paramètre que vous pouvez ajouter est un paramètre `-Computername` afin de compiler dynamiquement un fichier « .mof » pour tout paramètre `-Computername` que vous transmettez à votre configuration.</span><span class="sxs-lookup"><span data-stu-id="108b1-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="108b1-124">Comme pour les fonctions, vous pouvez également définir une valeur par défaut, au cas où l’utilisateur ne transmet aucune valeur pour `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="108b1-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="108b1-125">Au sein de votre configuration, vous pouvez alors spécifier votre paramètre `-ComputerName` lors de la définition de votre bloc de nœud.</span><span class="sxs-lookup"><span data-stu-id="108b1-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="108b1-126">Appel de votre configuration avec des paramètres</span><span class="sxs-lookup"><span data-stu-id="108b1-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="108b1-127">Après avoir ajouté des paramètres à votre configuration, vous pouvez les utiliser comme s’il s’agissait d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="108b1-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="108b1-128">Compilation de plusieurs fichiers .mof</span><span class="sxs-lookup"><span data-stu-id="108b1-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="108b1-129">Le bloc de nœud peut également accepter une liste séparée par des virgules de noms d’ordinateurs, et générer des fichiers « .mof » pour chacun de ces ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="108b1-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="108b1-130">Vous pouvez exécuter l’exemple suivant afin de générer des fichiers « .mof » pour tous les ordinateurs transmis au paramètre `-ComputerName`.</span><span class="sxs-lookup"><span data-stu-id="108b1-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="108b1-131">Paramètres avancés dans les configurations</span><span class="sxs-lookup"><span data-stu-id="108b1-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="108b1-132">Outre un paramètre `-ComputerName`, nous pouvons ajouter des paramètres pour le nom du service et l’état.</span><span class="sxs-lookup"><span data-stu-id="108b1-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="108b1-133">L’exemple suivant ajoute un bloc de paramètres avec un paramètre `-ServiceName` et l’utilise pour définir dynamiquement le bloc de ressources **Service**.</span><span class="sxs-lookup"><span data-stu-id="108b1-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="108b1-134">Il ajoute également un paramètre `-State` pour définir dynamiquement l’**état** dans le bloc de ressources **Service**.</span><span class="sxs-lookup"><span data-stu-id="108b1-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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
> <span data-ttu-id="108b1-135">Dans des scénarios plus complexes, il peut être plus judicieux de déplacer vos données dynamiques vers des [données de configuration](configData.md) structurées.</span><span class="sxs-lookup"><span data-stu-id="108b1-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="108b1-136">L’exemple de configuration utilise désormais un paramètre `$ServiceName` dynamique, mais si aucune valeur n’est spécifiée, la compilation génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="108b1-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="108b1-137">Vous pouvez ajouter une valeur par défaut, comme dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="108b1-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="108b1-138">Mais dans cette instance, il est plus judicieux de forcer simplement l’utilisateur à spécifier une valeur pour le paramètre `$ServiceName`.</span><span class="sxs-lookup"><span data-stu-id="108b1-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="108b1-139">L’attribut `parameter` vous permet d’ajouter une prise en charge de validation et de pipeline pour les paramètres de votre configuration.</span><span class="sxs-lookup"><span data-stu-id="108b1-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="108b1-140">Au-dessus de toute déclaration de paramètre, ajoutez le bloc d’attributs `parameter`, comme dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="108b1-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="108b1-141">Vous pouvez spécifier des arguments pour chaque attribut `parameter` afin de contrôler divers aspects du paramètre défini.</span><span class="sxs-lookup"><span data-stu-id="108b1-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="108b1-142">L’exemple suivant fait du paramètre `$ServiceName` un paramètre **obligatoire**.</span><span class="sxs-lookup"><span data-stu-id="108b1-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="108b1-143">Pour le paramètre `$State`, nous aimerions empêcher l’utilisateur de spécifier des valeurs en dehors d’un ensemble prédéfini, par exemple Running (en cours d’exécution) ou Stopped (arrêté). L’attribut `ValidationSet*` empêche l’utilisateur de spécifier des valeurs en dehors d’un ensemble prédéfini, par exemple Running (en cours d’exécution) ou Stopped (arrêté).</span><span class="sxs-lookup"><span data-stu-id="108b1-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="108b1-144">L’exemple suivant ajoute l’attribut `ValidationSet` au paramètre `$State`.</span><span class="sxs-lookup"><span data-stu-id="108b1-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="108b1-145">Comme nous ne souhaitons pas rendre le paramètre `$State` **obligatoire**, nous devrons lui ajouter une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="108b1-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="108b1-146">Vous n’avez pas besoin de spécifier un attribut `parameter` lorsque vous utilisez un attribut `validation`.</span><span class="sxs-lookup"><span data-stu-id="108b1-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="108b1-147">Pour en savoir plus sur les `parameter` et les attributs de validation, consultez [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span><span class="sxs-lookup"><span data-stu-id="108b1-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="108b1-148">Configuration entièrement paramétrable</span><span class="sxs-lookup"><span data-stu-id="108b1-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="108b1-149">Nous disposons désormais d’une configuration paramétrable qui oblige l’utilisateur à spécifier des valeurs `-InstanceName`, `-ServiceName`, et qui valide le paramètre `-State`.</span><span class="sxs-lookup"><span data-stu-id="108b1-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="108b1-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="108b1-150">See also</span></span>

- [<span data-ttu-id="108b1-151">Écrire une aide pour les configurations DSC</span><span class="sxs-lookup"><span data-stu-id="108b1-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="108b1-152">Configurations dynamiques</span><span class="sxs-lookup"><span data-stu-id="108b1-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="108b1-153">Utiliser des données de configuration dans vos configurations</span><span class="sxs-lookup"><span data-stu-id="108b1-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="108b1-154">Séparer des données de configuration et d’environnement</span><span class="sxs-lookup"><span data-stu-id="108b1-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
