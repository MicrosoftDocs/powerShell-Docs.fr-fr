---
ms.date: 12/12/2018
keywords: DSC, powershell, ressource, galerie, le programme d’installation
title: Ajouter des paramètres à une configuration
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401431"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="73529-103">Ajouter des paramètres à une configuration</span><span class="sxs-lookup"><span data-stu-id="73529-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="73529-104">Comme les fonctions, [Configurations](configurations.md) peut être paramétré pour permettre aux configurations plus dynamiques en fonction de l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="73529-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="73529-105">Les étapes sont similaires à ceux décrits dans [fonctions munies de paramètres](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="73529-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="73529-106">Cet exemple démarre avec une Configuration de base qui configure le service « Spooler » à « Exécution ».</span><span class="sxs-lookup"><span data-stu-id="73529-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="73529-107">Paramètres de Configuration intégrés</span><span class="sxs-lookup"><span data-stu-id="73529-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="73529-108">Contrairement à une fonction, le [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribut n’ajoute aucune fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="73529-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="73529-109">En plus de [paramètres communs](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations peuvent également utiliser les intégrées dans les paramètres sans avoir à les définir suivantes.</span><span class="sxs-lookup"><span data-stu-id="73529-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="73529-110">Paramètre</span><span class="sxs-lookup"><span data-stu-id="73529-110">Parameter</span></span>  |<span data-ttu-id="73529-111">Description</span><span class="sxs-lookup"><span data-stu-id="73529-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="73529-112">Utilisé dans la définition [Configurations Composite](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="73529-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="73529-113">Utilisé dans la définition [Configurations Composite](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="73529-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="73529-114">Utilisé dans la définition [Configurations Composite](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="73529-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="73529-115">Utilisé pour passer dans structuré [les données de Configuration](configData.md) pour une utilisation dans la Configuration.</span><span class="sxs-lookup"><span data-stu-id="73529-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="73529-116">Utilisé pour spécifier l’emplacement où votre «\<computername\>.mof « fichier sera compilé</span><span class="sxs-lookup"><span data-stu-id="73529-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="73529-117">Ajout de vos propres paramètres aux Configurations</span><span class="sxs-lookup"><span data-stu-id="73529-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="73529-118">Outre les paramètres intégrés, vous pouvez également ajouter vos propres paramètres pour vos Configurations.</span><span class="sxs-lookup"><span data-stu-id="73529-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="73529-119">Le bloc de paramètres est placé directement dans la déclaration de la Configuration, comme une fonction.</span><span class="sxs-lookup"><span data-stu-id="73529-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="73529-120">Un bloc de paramètres de Configuration doit être en dehors des **nœud** déclarations et avant tout autre *importer* instructions.</span><span class="sxs-lookup"><span data-stu-id="73529-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="73529-121">En ajoutant des paramètres, vous pouvez appliquer vos Configurations plus robuste et dynamique.</span><span class="sxs-lookup"><span data-stu-id="73529-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="73529-122">Ajouter un paramètre ComputerName</span><span class="sxs-lookup"><span data-stu-id="73529-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="73529-123">Est le premier paramètre que vous pouvez ajouter un `-Computername` paramètre afin de compiler dynamiquement un fichier « .mof » pour tout `-Computername` vous passez à votre configuration.</span><span class="sxs-lookup"><span data-stu-id="73529-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="73529-124">Comme les fonctions, vous pouvez également définir une valeur par défaut, au cas où l’utilisateur ne passe pas une valeur pour `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="73529-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="73529-125">Au sein de votre configuration, vous pouvez ensuite spécifier votre `-ComputerName` paramètre lors de la définition de votre bloc de nœud.</span><span class="sxs-lookup"><span data-stu-id="73529-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="73529-126">Appelez votre Configuration avec des paramètres</span><span class="sxs-lookup"><span data-stu-id="73529-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="73529-127">Une fois que vous avez ajouté des paramètres à votre Configuration, vous pouvez les utiliser comme vous le feriez avec une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="73529-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="73529-128">Compilation de plusieurs fichiers .mof</span><span class="sxs-lookup"><span data-stu-id="73529-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="73529-129">Le bloc de nœud peut également accepter une liste séparée par des virgules de noms d’ordinateur et génère des fichiers « .mof » pour chaque.</span><span class="sxs-lookup"><span data-stu-id="73529-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="73529-130">Vous pouvez exécuter l’exemple suivant pour générer des fichiers « .mof » pour tous les ordinateurs passés à la `-ComputerName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="73529-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="73529-131">Paramètres avancés dans les Configurations</span><span class="sxs-lookup"><span data-stu-id="73529-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="73529-132">Outre un `-ComputerName` paramètre, nous pouvons ajouter des paramètres pour le nom du service et l’état.</span><span class="sxs-lookup"><span data-stu-id="73529-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="73529-133">L’exemple suivant ajoute un bloc de paramètres avec un `-ServiceName` paramètre et l’utilise pour définir dynamiquement le **Service** bloc de ressources.</span><span class="sxs-lookup"><span data-stu-id="73529-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="73529-134">Il ajoute également un `-State` paramètre pour définir dynamiquement le **état** dans le **Service** bloc de ressources.</span><span class="sxs-lookup"><span data-stu-id="73529-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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
> <span data-ttu-id="73529-135">Dans d’autres scénarios advacned, il peut être plus judicieux de déplacer vos données dynamiques dans un texte structuré [les données de Configuration](configData.md).</span><span class="sxs-lookup"><span data-stu-id="73529-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="73529-136">L’exemple de Configuration maintenant prend un dynamique `$ServiceName`, mais s’il n’est pas spécifié, génère une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="73529-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="73529-137">Vous pouvez ajouter une valeur par défaut, comme dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="73529-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="73529-138">Dans cette instance, il est plus judicieux de simplement forcer l’utilisateur de spécifier une valeur pour le `$ServiceName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="73529-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="73529-139">Le `parameter` attribut vous permet d’ajouter la prise en charge supplémentaire de validation et de pipeline pour les paramètres de Configuration de votre.</span><span class="sxs-lookup"><span data-stu-id="73529-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="73529-140">Au-dessus de toute déclaration de paramètre, ajoutez le `parameter` bloc d’attributs comme dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="73529-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="73529-141">Vous pouvez spécifier des arguments à chaque `parameter` attribut, de contrôler divers aspects du paramètre défini.</span><span class="sxs-lookup"><span data-stu-id="73529-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="73529-142">L’exemple suivant effectue la `$ServiceName` un **obligatoire** paramètre.</span><span class="sxs-lookup"><span data-stu-id="73529-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="73529-143">Pour le `$State` paramètre, nous aimerions empêcher l’utilisateur de spécifier des valeurs en dehors d’un ensemble prédéfini (comme en cours d’exécution, arrêté) le `ValidationSet*`attribut empêche l’utilisateur de spécifier des valeurs en dehors d’un ensemble prédéfini (par exemple, en cours d’exécution, Arrêté).</span><span class="sxs-lookup"><span data-stu-id="73529-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="73529-144">L’exemple suivant ajoute le `ValidationSet` attribut le `$State` paramètre.</span><span class="sxs-lookup"><span data-stu-id="73529-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="73529-145">Étant donné que nous ne souhaitez pas rendre le `$State` paramètre **obligatoire**, nous devrons ajouter une valeur par défaut pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="73529-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="73529-146">Vous n’avez pas besoin de spécifier un `parameter` attribut lorsque vous utilisez un `validation` attribut.</span><span class="sxs-lookup"><span data-stu-id="73529-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="73529-147">Vous pouvez en savoir plus sur la `parameter` et attributs de validation dans [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="73529-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="73529-148">Configuration entièrement paramétrable</span><span class="sxs-lookup"><span data-stu-id="73529-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="73529-149">Nous disposons désormais d’une Configuration paramétrable qui oblige l’utilisateur à spécifier un `-InstanceName`, `-ServiceName`et valide les `-State` paramètre.</span><span class="sxs-lookup"><span data-stu-id="73529-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="see-also"></a><span data-ttu-id="73529-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73529-150">See also</span></span>

- [<span data-ttu-id="73529-151">Écrire une aide pour les configurations DSC</span><span class="sxs-lookup"><span data-stu-id="73529-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="73529-152">Configuration dynamique</span><span class="sxs-lookup"><span data-stu-id="73529-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="73529-153">Utiliser les données de Configuration dans vos Configurations</span><span class="sxs-lookup"><span data-stu-id="73529-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="73529-154">Données de configuration et d’environnement distinct</span><span class="sxs-lookup"><span data-stu-id="73529-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
