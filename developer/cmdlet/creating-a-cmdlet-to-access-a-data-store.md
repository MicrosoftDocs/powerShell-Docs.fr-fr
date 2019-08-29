---
title: Création d’une applet de commande pour accéder à un magasin de données
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 7acccbd48dcfb654b11e448a1f24835ad3668fae
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104463"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a><span data-ttu-id="4532f-102">Création d’une applet de commande pour accéder à un magasin de données</span><span class="sxs-lookup"><span data-stu-id="4532f-102">Creating a Cmdlet to Access a Data Store</span></span>

<span data-ttu-id="4532f-103">Cette section décrit comment créer une applet de commande qui accède aux données stockées au moyen d’un fournisseur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4532f-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span></span> <span data-ttu-id="4532f-104">Ce type d’applet de commande utilise l’infrastructure du fournisseur Windows PowerShell du runtime Windows PowerShell et, par conséquent, la classe cmdlet doit dériver de la classe de base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="4532f-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span>

<span data-ttu-id="4532f-105">L’applet de commande SELECT-Str décrite ici peut rechercher et sélectionner des chaînes dans un fichier ou un objet.</span><span class="sxs-lookup"><span data-stu-id="4532f-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span></span> <span data-ttu-id="4532f-106">Les modèles utilisés pour identifier la chaîne peuvent être spécifiés explicitement par `Path` le biais du paramètre de l’applet de commande `Script` ou implicitement via le paramètre.</span><span class="sxs-lookup"><span data-stu-id="4532f-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span></span>

<span data-ttu-id="4532f-107">L’applet de commande est conçue pour utiliser n’importe quel fournisseur Windows PowerShell dérivé de [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span><span class="sxs-lookup"><span data-stu-id="4532f-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span></span> <span data-ttu-id="4532f-108">Par exemple, l’applet de commande peut spécifier le fournisseur FileSystem ou le fournisseur de variables fourni par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4532f-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span></span> <span data-ttu-id="4532f-109">Pour plus d’informations sur les fournisseurs aboutWindows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4532f-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="4532f-110">Définition de la classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="4532f-110">Defining the Cmdlet Class</span></span>

<span data-ttu-id="4532f-111">La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="4532f-112">Cette applet de commande détecte certaines chaînes. par conséquent, le nom du verbe choisi ici est «Select», défini par la classe [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) .</span><span class="sxs-lookup"><span data-stu-id="4532f-112">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span></span> <span data-ttu-id="4532f-113">Le nom substantif «str» est utilisé, car l’applet de commande agit sur des chaînes.</span><span class="sxs-lookup"><span data-stu-id="4532f-113">The noun name "Str" is used because the cmdlet acts upon strings.</span></span> <span data-ttu-id="4532f-114">Dans la déclaration ci-dessous, Notez que le verbe d’applet de commande et le nom substantif sont reflétés dans le nom de la classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-114">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span> <span data-ttu-id="4532f-115">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez noms des verbes d' [applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="4532f-116">La classe .NET pour cette applet de commande doit dériver de la classe de base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) , car elle fournit la prise en charge requise par le runtime Windows PowerShell pour exposer l’infrastructure du fournisseur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4532f-116">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span></span> <span data-ttu-id="4532f-117">Notez que cette applet de commande utilise également les classes d’expressions régulières .NET Framework, telles que [System. Text. RegularExpressions. Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span><span class="sxs-lookup"><span data-stu-id="4532f-117">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span></span>

<span data-ttu-id="4532f-118">Le code suivant est la définition de classe pour cette applet de commande SELECT-Str.</span><span class="sxs-lookup"><span data-stu-id="4532f-118">The following code is the class definition for this Select-Str cmdlet.</span></span>

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

<span data-ttu-id="4532f-119">Cette applet de commande définit un jeu de paramètres par `DefaultParameterSetName` défaut en ajoutant le mot clé Attribute à la déclaration de classe.</span><span class="sxs-lookup"><span data-stu-id="4532f-119">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span></span> <span data-ttu-id="4532f-120">Le jeu `PatternParameterSet` de paramètres par défaut est utilisé `Script` lorsque le paramètre n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="4532f-120">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span></span> <span data-ttu-id="4532f-121">Pour plus d’informations sur ce jeu de paramètres, `Pattern` consultez `Script` la discussion sur les paramètres et dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="4532f-121">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span></span>

## <a name="defining-parameters-for-data-access"></a><span data-ttu-id="4532f-122">Définition des paramètres pour l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="4532f-122">Defining Parameters for Data Access</span></span>

<span data-ttu-id="4532f-123">Cette applet de commande définit plusieurs paramètres qui permettent à l’utilisateur d’accéder aux données stockées et de les examiner.</span><span class="sxs-lookup"><span data-stu-id="4532f-123">This cmdlet defines several parameters that allow the user to access and examine stored data.</span></span> <span data-ttu-id="4532f-124">Ces paramètres incluent un `Path` paramètre qui indique l’emplacement du magasin de données, un `Pattern` paramètre qui spécifie le modèle à utiliser dans la recherche et plusieurs autres paramètres qui prennent en charge l’exécution de la recherche.</span><span class="sxs-lookup"><span data-stu-id="4532f-124">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="4532f-125">Pour plus d’informations sur les principes de base de la définition de paramètres, consultez [Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="4532f-125">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

### <a name="declaring-the-path-parameter"></a><span data-ttu-id="4532f-126">Déclaration du paramètre Path</span><span class="sxs-lookup"><span data-stu-id="4532f-126">Declaring the Path Parameter</span></span>

<span data-ttu-id="4532f-127">Pour localiser le magasin de données, cette applet de commande doit utiliser un chemin d’accès Windows PowerShell pour identifier le fournisseur Windows PowerShell qui est conçu pour accéder au magasin de données.</span><span class="sxs-lookup"><span data-stu-id="4532f-127">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span></span> <span data-ttu-id="4532f-128">Par conséquent, il définit `Path` un paramètre de type tableau de chaînes pour indiquer l’emplacement du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4532f-128">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span></span>

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

<span data-ttu-id="4532f-129">Notez que ce paramètre appartient à deux jeux de paramètres différents et qu’il a un alias.</span><span class="sxs-lookup"><span data-stu-id="4532f-129">Note that this parameter belongs to two different parameter sets and that it has an alias.</span></span>

<span data-ttu-id="4532f-130">Deux attributs [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) déclarent que `Path` le `ScriptParameterSet` paramètre appartient au et au `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="4532f-130">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span></span> <span data-ttu-id="4532f-131">Pour plus d’informations sur les jeux de paramètres, consultez [Ajout de jeux de paramètres à une applet](./adding-parameter-sets-to-a-cmdlet.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-131">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

<span data-ttu-id="4532f-132">L’attribut [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) déclare un `PSPath` alias pour le `Path` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4532f-132">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span></span> <span data-ttu-id="4532f-133">La déclaration de cet alias est fortement recommandée pour assurer la cohérence avec d’autres applets de commande qui accèdent aux fournisseurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4532f-133">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span></span> <span data-ttu-id="4532f-134">Pour plus d’informations sur les chemins d’accès PowerShell aboutWindows, consultez «concepts du chemin d’accès PowerShell» dans fonctionnement de [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="4532f-134">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

### <a name="declaring-the-pattern-parameter"></a><span data-ttu-id="4532f-135">Déclaration du paramètre de modèle</span><span class="sxs-lookup"><span data-stu-id="4532f-135">Declaring the Pattern Parameter</span></span>

<span data-ttu-id="4532f-136">Pour spécifier les modèles à rechercher, cette applet de commande déclare un `Pattern` paramètre qui est un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="4532f-136">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span></span> <span data-ttu-id="4532f-137">Un résultat positif est retourné lorsque l’un des modèles est trouvé dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="4532f-137">A positive result is returned when any of the patterns are found in the data store.</span></span> <span data-ttu-id="4532f-138">Notez que ces modèles peuvent être compilés dans un tableau d’expressions régulières compilées ou un tableau de modèles de caractère générique utilisé pour les recherches littérales.</span><span class="sxs-lookup"><span data-stu-id="4532f-138">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

<span data-ttu-id="4532f-139">Lorsque ce paramètre est spécifié, l’applet de commande utilise le jeu `PatternParameterSet`de paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="4532f-139">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span></span> <span data-ttu-id="4532f-140">Dans ce cas, l’applet de commande utilise les modèles spécifiés ici pour sélectionner des chaînes.</span><span class="sxs-lookup"><span data-stu-id="4532f-140">In this case, the cmdlet uses the patterns specified here to select strings.</span></span> <span data-ttu-id="4532f-141">En revanche, le `Script` paramètre peut également être utilisé pour fournir un script qui contient les modèles.</span><span class="sxs-lookup"><span data-stu-id="4532f-141">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span></span> <span data-ttu-id="4532f-142">Les `Script` paramètres `Pattern` et définissent deux jeux de paramètres distincts, afin qu’ils s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="4532f-142">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span></span>

### <a name="declaring-search-support-parameters"></a><span data-ttu-id="4532f-143">Déclaration des paramètres de prise en charge de recherche</span><span class="sxs-lookup"><span data-stu-id="4532f-143">Declaring Search Support Parameters</span></span>

<span data-ttu-id="4532f-144">Cette applet de commande définit les paramètres de prise en charge suivants qui peuvent être utilisés pour modifier les fonctions de recherche de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-144">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span></span>

<span data-ttu-id="4532f-145">Le `Script` paramètre spécifie un bloc de script qui peut être utilisé pour fournir un autre mécanisme de recherche pour l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-145">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span></span> <span data-ttu-id="4532f-146">Le script doit contenir les modèles utilisés pour la correspondance et retourner un objet [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) .</span><span class="sxs-lookup"><span data-stu-id="4532f-146">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span></span> <span data-ttu-id="4532f-147">Notez que ce paramètre est également le paramètre unique qui identifie le `ScriptParameterSet` jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="4532f-147">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span></span> <span data-ttu-id="4532f-148">Quand le runtime Windows PowerShell voit ce paramètre, il utilise uniquement les `ScriptParameterSet` paramètres qui appartiennent au jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="4532f-148">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

<span data-ttu-id="4532f-149">Le `SimpleMatch` paramètre est un paramètre de commutateur qui indique si l’applet de commande doit faire correspondre explicitement les modèles à mesure qu’ils sont fournis.</span><span class="sxs-lookup"><span data-stu-id="4532f-149">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span></span> <span data-ttu-id="4532f-150">Lorsque l’utilisateur spécifie le paramètre au niveau de la`true`ligne de commande (), l’applet de commande utilise les modèles tels qu’ils sont fournis.</span><span class="sxs-lookup"><span data-stu-id="4532f-150">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span></span> <span data-ttu-id="4532f-151">Si le paramètre n’est pas spécifié`false`(), l’applet de commande utilise des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="4532f-151">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span></span> <span data-ttu-id="4532f-152">La valeur par défaut de ce `false`paramètre est.</span><span class="sxs-lookup"><span data-stu-id="4532f-152">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

<span data-ttu-id="4532f-153">Le `CaseSensitive` paramètre est un paramètre de commutateur qui indique si une recherche respectant la casse est effectuée.</span><span class="sxs-lookup"><span data-stu-id="4532f-153">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span></span> <span data-ttu-id="4532f-154">Lorsque l’utilisateur spécifie le paramètre au niveau de la`true`ligne de commande (), l’applet de commande recherche les caractères majuscules et minuscules lors de la comparaison des modèles.</span><span class="sxs-lookup"><span data-stu-id="4532f-154">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span></span> <span data-ttu-id="4532f-155">Si le paramètre n’est pas spécifié`false`(), l’applet de commande ne fait pas la distinction entre les majuscules et les minuscules.</span><span class="sxs-lookup"><span data-stu-id="4532f-155">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span></span> <span data-ttu-id="4532f-156">Par exemple, «MyFile» et «MyFile» seraient tous deux retournés en tant que résultats positifs.</span><span class="sxs-lookup"><span data-stu-id="4532f-156">For example "MyFile" and "myfile" would both be returned as positive hits.</span></span> <span data-ttu-id="4532f-157">La valeur par défaut de ce `false`paramètre est.</span><span class="sxs-lookup"><span data-stu-id="4532f-157">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

<span data-ttu-id="4532f-158">Les `Exclude` paramètres `Include` et identifient les éléments qui sont explicitement exclus de la recherche ou inclus dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="4532f-158">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span></span> <span data-ttu-id="4532f-159">Par défaut, l’applet de commande recherche tous les éléments dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="4532f-159">By default, the cmdlet will search all items in the data store.</span></span> <span data-ttu-id="4532f-160">Toutefois, pour limiter la recherche effectuée par l’applet de commande, ces paramètres peuvent être utilisés pour indiquer explicitement les éléments à inclure dans la recherche ou à omettre.</span><span class="sxs-lookup"><span data-stu-id="4532f-160">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a><span data-ttu-id="4532f-161">Déclarer des jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="4532f-161">Declaring Parameter Sets</span></span>

<span data-ttu-id="4532f-162">Cette applet de commande utilise deux jeux`ScriptParameterSet` de `PatternParameterSet`paramètres (et, qui est la valeur par défaut) comme noms de deux jeux de paramètres utilisés dans l’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="4532f-162">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span></span> <span data-ttu-id="4532f-163">`PatternParameterSet`est le jeu de paramètres par défaut et est utilisé `Pattern` lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="4532f-163">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span></span> <span data-ttu-id="4532f-164">`ScriptParameterSet`est utilisé lorsque l’utilisateur spécifie un autre mécanisme de recherche `Script` par le biais du paramètre.</span><span class="sxs-lookup"><span data-stu-id="4532f-164">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span></span> <span data-ttu-id="4532f-165">Pour plus d’informations sur les jeux de paramètres, consultez [Ajout de jeux de paramètres à une applet](./adding-parameter-sets-to-a-cmdlet.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-165">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="4532f-166">Substitution des méthodes de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="4532f-166">Overriding Input Processing Methods</span></span>

<span data-ttu-id="4532f-167">Les applets de commande doivent remplacer une ou plusieurs méthodes de traitement d’entrée pour la classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="4532f-167">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span> <span data-ttu-id="4532f-168">Pour plus d’informations sur les méthodes de traitement d’entrée, consultez [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-168">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="4532f-169">Cette applet de commande remplace la méthode [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) pour générer un tableau d’expressions régulières compilées au démarrage.</span><span class="sxs-lookup"><span data-stu-id="4532f-169">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span></span> <span data-ttu-id="4532f-170">Cela augmente les performances lors des recherches qui n’utilisent pas une correspondance simple.</span><span class="sxs-lookup"><span data-stu-id="4532f-170">This increases performance during searches that do not use simple matching.</span></span>

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

<span data-ttu-id="4532f-171">Cette applet de commande remplace également la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) pour traiter les sélections de chaîne que l’utilisateur effectue sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-171">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span></span> <span data-ttu-id="4532f-172">Il écrit les résultats de la sélection de chaîne sous la forme d’un objet personnalisé en appelant une méthode **MatchString** privée.</span><span class="sxs-lookup"><span data-stu-id="4532f-172">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span></span>

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a><span data-ttu-id="4532f-173">Accès au contenu</span><span class="sxs-lookup"><span data-stu-id="4532f-173">Accessing Content</span></span>

<span data-ttu-id="4532f-174">Votre applet de commande doit ouvrir le fournisseur indiqué par le chemin d’accès Windows PowerShell afin qu’il puisse accéder aux données.</span><span class="sxs-lookup"><span data-stu-id="4532f-174">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span></span> <span data-ttu-id="4532f-175">L’objet [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) pour l’instance d’exécution est utilisé pour l’accès au fournisseur, tandis que la propriété [System. Management. Automation. PSCmdlet. Invokeprovider \*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) de l’applet de commande est utilisée pour ouvrir le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="4532f-175">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span></span> <span data-ttu-id="4532f-176">L’accès au contenu est fourni par la récupération de l’objet [System. Management. Automation. Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) pour le fournisseur ouvert.</span><span class="sxs-lookup"><span data-stu-id="4532f-176">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span></span>

<span data-ttu-id="4532f-177">Cet exemple d’applet de commande SELECT-Str utilise la propriété [System. Management. Automation. Providerintrinsics. Content \*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) pour exposer le contenu à analyser.</span><span class="sxs-lookup"><span data-stu-id="4532f-177">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span></span> <span data-ttu-id="4532f-178">Il peut ensuite appeler la méthode [System. Management. Automation. Contentcmdletproviderintrinsics. GetReader \*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) , en transmettant le chemin d’accès Windows PowerShell requis.</span><span class="sxs-lookup"><span data-stu-id="4532f-178">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4532f-179">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="4532f-179">Code Sample</span></span>

<span data-ttu-id="4532f-180">Le code suivant illustre l’implémentation de cette version de l’applet de commande SELECT-Str.</span><span class="sxs-lookup"><span data-stu-id="4532f-180">The following code shows the implementation of this version of this Select-Str cmdlet.</span></span> <span data-ttu-id="4532f-181">Notez que ce code comprend la classe d’applet de commande, les méthodes privées utilisées par l’applet de commande et le code de composant logiciel enfichable Windows PowerShell utilisé pour inscrire l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-181">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span></span> <span data-ttu-id="4532f-182">Pour plus d’informations sur l’inscription de l’applet de commande, consultez [génération de l’applet](#defining-the-cmdlet-class)de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-182">For more information about registering the cmdlet, see [Building the Cmdlet](#defining-the-cmdlet-class).</span></span>

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a><span data-ttu-id="4532f-183">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="4532f-183">Building the Cmdlet</span></span>

<span data-ttu-id="4532f-184">Après l’implémentation d’une applet de commande, vous devez l’inscrire auprès de Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4532f-184">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="4532f-185">Pour plus d’informations sur l’enregistrement des applets de commande, consultez Comment inscrire des applets de commande [, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="4532f-185">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="4532f-186">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="4532f-186">Testing the Cmdlet</span></span>

<span data-ttu-id="4532f-187">Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="4532f-187">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="4532f-188">La procédure suivante peut être utilisée pour tester l’exemple d’applet de commande SELECT-Str.</span><span class="sxs-lookup"><span data-stu-id="4532f-188">The following procedure can be used to test the sample Select-Str cmdlet.</span></span>

1. <span data-ttu-id="4532f-189">Démarrez Windows PowerShell et recherchez dans le fichier Notes des occurrences de lignes avec l’expression «.NET».</span><span class="sxs-lookup"><span data-stu-id="4532f-189">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span></span> <span data-ttu-id="4532f-190">Notez que les guillemets autour du nom du chemin d’accès sont requis uniquement si le chemin d’accès comprend plusieurs mots.</span><span class="sxs-lookup"><span data-stu-id="4532f-190">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span></span>

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    <span data-ttu-id="4532f-191">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4532f-191">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. <span data-ttu-id="4532f-192">Recherchez dans le fichier Notes des occurrences de lignes avec le mot «sur», suivi d’un autre texte.</span><span class="sxs-lookup"><span data-stu-id="4532f-192">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span></span> <span data-ttu-id="4532f-193">Le `SimpleMatch` paramètre utilise la `false`valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4532f-193">The `SimpleMatch` parameter is using the default value of `false`.</span></span> <span data-ttu-id="4532f-194">La recherche ne respecte pas la casse, car `CaseSensitive` le paramètre a la `false`valeur.</span><span class="sxs-lookup"><span data-stu-id="4532f-194">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span></span>

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    <span data-ttu-id="4532f-195">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4532f-195">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. <span data-ttu-id="4532f-196">Recherchez le fichier Notes à l’aide d’une expression régulière comme modèle.</span><span class="sxs-lookup"><span data-stu-id="4532f-196">Search the Notes file using a regular expression as the pattern.</span></span> <span data-ttu-id="4532f-197">L’applet de commande recherche des caractères alphabétiques et des espaces vides entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="4532f-197">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span></span>

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    <span data-ttu-id="4532f-198">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4532f-198">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. <span data-ttu-id="4532f-199">Effectuez une recherche qui respecte la casse du fichier Notes pour les occurrences du mot «paramètre».</span><span class="sxs-lookup"><span data-stu-id="4532f-199">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span></span>

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    <span data-ttu-id="4532f-200">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4532f-200">The following output appears.</span></span>

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. <span data-ttu-id="4532f-201">Recherchez dans le fournisseur de variables livré avec Windows PowerShell les variables dont les valeurs numériques sont comprises entre 0 et 9.</span><span class="sxs-lookup"><span data-stu-id="4532f-201">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span></span>

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    <span data-ttu-id="4532f-202">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4532f-202">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. <span data-ttu-id="4532f-203">Utilisez un bloc de script pour rechercher la chaîne «pos» dans le fichier SelectStrCommandSample.cs.</span><span class="sxs-lookup"><span data-stu-id="4532f-203">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span></span> <span data-ttu-id="4532f-204">La fonction **cmatch** du script effectue une correspondance de modèle qui ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="4532f-204">The **cmatch** function for the script performs a case-insensitive pattern match.</span></span>

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    <span data-ttu-id="4532f-205">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4532f-205">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a><span data-ttu-id="4532f-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4532f-206">See Also</span></span>

[<span data-ttu-id="4532f-207">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4532f-207">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[<span data-ttu-id="4532f-208">Création de votre première applet de commande</span><span class="sxs-lookup"><span data-stu-id="4532f-208">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="4532f-209">Création d’une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="4532f-209">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="4532f-210">Concevoir votre fournisseur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4532f-210">Design Your Windows PowerShell Provider</span></span>](../prog-guide/designing-your-windows-powershell-provider.md)

<span data-ttu-id="4532f-211">[Fonctionnement de Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4532f-211">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="4532f-212">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4532f-212">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="4532f-213">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4532f-213">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
