---
title: Ajout de paramètres qui traitent l’entrée de ligne de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: e010e28ec705932063bb418b260a1087fc3eef9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856005"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="b5e48-102">Ajout de paramètres qui traitent l’entrée de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b5e48-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="b5e48-103">Une source d’entrée pour une applet de commande est la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="b5e48-104">Cette rubrique décrit comment ajouter un paramètre à la **Get-Process** applet de commande (qui est décrite dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)) afin que l’applet de commande peut traiter l’entrée à partir de l’ordinateur local selon explicite objets passés à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="b5e48-105">Le **Get-Process** applet de commande décrite ici récupère des processus basés sur leurs noms, puis affiche des informations sur les processus à l’invite de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

<span data-ttu-id="b5e48-106">Les sections suivantes sont dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="b5e48-106">The following sections are in this topic:</span></span>

- [<span data-ttu-id="b5e48-107">Définition de la classe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b5e48-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="b5e48-108">Déclaration de paramètres</span><span class="sxs-lookup"><span data-stu-id="b5e48-108">Declaring Parameters</span></span>](#Declaring-Parameters)

- [<span data-ttu-id="b5e48-109">Prise en charge de la Validation de paramètre</span><span class="sxs-lookup"><span data-stu-id="b5e48-109">Supporting Parameter Validation</span></span>](#Supporting-Parameter-Validation)

- [<span data-ttu-id="b5e48-110">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="b5e48-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="b5e48-111">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="b5e48-111">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="b5e48-112">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="b5e48-112">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="b5e48-113">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b5e48-113">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="b5e48-114">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b5e48-114">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="b5e48-115">Définition de la classe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b5e48-115">Defining the Cmdlet Class</span></span>

<span data-ttu-id="b5e48-116">La première étape de création de l’applet de commande est l’applet de commande d’affectation de noms et la déclaration de la classe .NET Framework qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-116">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="b5e48-117">Cette applet de commande récupère les informations de processus, par conséquent, le nom du verbe choisi ici est « Get ».</span><span class="sxs-lookup"><span data-stu-id="b5e48-117">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="b5e48-118">(Presque toute sorte de l’applet de commande qui est capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="b5e48-118">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b5e48-119">Voici la déclaration de classe pour le **Get-Process** applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-119">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="b5e48-120">Plus d’informations sur cette définition sont fournies dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b5e48-120">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="b5e48-121">Déclaration de paramètres</span><span class="sxs-lookup"><span data-stu-id="b5e48-121">Declaring Parameters</span></span>

<span data-ttu-id="b5e48-122">Un paramètre d’applet de commande permet à l’utilisateur à fournir l’entrée à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-122">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="b5e48-123">Dans l’exemple suivant, **Get-Process** et `Get-Member` sont les noms des applets de commande canalisée en rafale et `MemberType` est un paramètre pour le `Get-Member` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-123">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="b5e48-124">Le paramètre a l’argument « property ».</span><span class="sxs-lookup"><span data-stu-id="b5e48-124">The parameter has the argument "property."</span></span>

<span data-ttu-id="b5e48-125">**PS > get-Process ; `get-member` membertype - propriété**</span><span class="sxs-lookup"><span data-stu-id="b5e48-125">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="b5e48-126">Pour déclarer des paramètres pour une applet de commande, vous devez d’abord définir les propriétés qui représentent les paramètres.</span><span class="sxs-lookup"><span data-stu-id="b5e48-126">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="b5e48-127">Dans le **Get-Process** applet de commande, le seul paramètre est `Name`, qui dans ce cas représente le nom de l’objet de processus de .NET Framework à récupérer.</span><span class="sxs-lookup"><span data-stu-id="b5e48-127">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="b5e48-128">Par conséquent, la classe de l’applet de commande définit une propriété de type chaîne pour accepter un tableau de noms.</span><span class="sxs-lookup"><span data-stu-id="b5e48-128">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="b5e48-129">Voici la déclaration de paramètre pour le `Name` paramètre de la **Get-Process** applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-129">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="b5e48-130">Pour informer le runtime de Windows PowerShell que cette propriété est la `Name` paramètre, un [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribut est ajouté à la définition de propriété.</span><span class="sxs-lookup"><span data-stu-id="b5e48-130">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="b5e48-131">La syntaxe de base pour déclarer cet attribut est `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="b5e48-131">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="b5e48-132">Un paramètre doit être explicitement marqué comme public.</span><span class="sxs-lookup"><span data-stu-id="b5e48-132">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="b5e48-133">Paramètres qui ne sont pas marqués comme public par défaut interne et ne sont pas localisés par le runtime de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5e48-133">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="b5e48-134">Cette applet de commande utilise un tableau de chaînes pour la `Name` paramètre.</span><span class="sxs-lookup"><span data-stu-id="b5e48-134">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="b5e48-135">Si possible, votre applet de commande doit également définir un paramètre sous forme de tableau, car cela permet à l’applet de commande accepter plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="b5e48-135">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="b5e48-136">Points à retenir sur les définitions de paramètres</span><span class="sxs-lookup"><span data-stu-id="b5e48-136">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="b5e48-137">Prédéfinies Windows PowerShell paramètre noms et types de données doivent être réutilisés autant que possible pour vous assurer que votre applet de commande est compatible avec les applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5e48-137">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="b5e48-138">Par exemple, si toutes les applets de commande utilisent prédéfinis `Id` nom de paramètre pour identifier une ressource, l’utilisateur sera facilement comprendre la signification du paramètre, quel que soit l’applet de commande qu’ils utilisent.</span><span class="sxs-lookup"><span data-stu-id="b5e48-138">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="b5e48-139">En fait, les noms de paramètres suivent les mêmes règles que celles utilisées pour les noms de variables dans le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b5e48-139">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="b5e48-140">Pour plus d’informations sur le paramètre d’affectation de noms, consultez [noms de paramètre d’applet de commande](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="b5e48-140">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="b5e48-141">Windows PowerShell réserve quelques noms de paramètre pour fournir une expérience utilisateur cohérente.</span><span class="sxs-lookup"><span data-stu-id="b5e48-141">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="b5e48-142">N’utilisez pas ces noms de paramètre : `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, et `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b5e48-142">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="b5e48-143">En outre, les alias suivants de ces noms de paramètres sont réservés : `vb`, `db`, `ea`, `ev`, `ov`, et `ob`.</span><span class="sxs-lookup"><span data-stu-id="b5e48-143">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="b5e48-144">`Name` est un nom de paramètre simple et courant recommandé pour une utilisation dans vos applets de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-144">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="b5e48-145">Il est préférable de choisir un nom de paramètre, ainsi qu’un nom complex qui est unique pour une applet de commande spécifique et difficiles à mémoriser.</span><span class="sxs-lookup"><span data-stu-id="b5e48-145">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="b5e48-146">Les paramètres respectent la casse dans Windows PowerShell, bien que par défaut l’interpréteur de commandes préserve la casse.</span><span class="sxs-lookup"><span data-stu-id="b5e48-146">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="b5e48-147">Respect de la casse des arguments dépend de l’opération de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-147">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="b5e48-148">Arguments sont passés à un paramètre comme spécifié dans la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-148">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="b5e48-149">Pour obtenir des exemples d’autres déclarations de paramètre, consultez [paramètres de l’applet de commande](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b5e48-149">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="b5e48-150">Déclarer des paramètres positionnels ou nommés</span><span class="sxs-lookup"><span data-stu-id="b5e48-150">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="b5e48-151">Une applet de commande doit définir chaque paramètre soit un paramètre positionnel ou nommé.</span><span class="sxs-lookup"><span data-stu-id="b5e48-151">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="b5e48-152">Les deux types de paramètres acceptent des arguments uniques, plusieurs arguments séparés par des virgules et les paramètres de type Boolean.</span><span class="sxs-lookup"><span data-stu-id="b5e48-152">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="b5e48-153">Un paramètre booléen, également appelé un *commutateur*, gère uniquement les paramètres de type Boolean.</span><span class="sxs-lookup"><span data-stu-id="b5e48-153">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="b5e48-154">Le commutateur est utilisé pour déterminer la présence du paramètre.</span><span class="sxs-lookup"><span data-stu-id="b5e48-154">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="b5e48-155">La valeur par défaut recommandée est `false`.</span><span class="sxs-lookup"><span data-stu-id="b5e48-155">The recommended default is `false`.</span></span>

<span data-ttu-id="b5e48-156">L’exemple **Get-Process** applet de commande définit le `Name` paramètre comme un paramètre de positionnement à la position 0.</span><span class="sxs-lookup"><span data-stu-id="b5e48-156">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="b5e48-157">Cela signifie que le premier argument de l’utilisateur entre dans la ligne de commande est automatiquement inséré pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="b5e48-157">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="b5e48-158">Si vous souhaitez définir un paramètre nommé, pour lequel l’utilisateur doit spécifier le nom du paramètre à partir de la ligne de commande, laissez le `Position` mot clé hors de la déclaration d’attribut.</span><span class="sxs-lookup"><span data-stu-id="b5e48-158">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="b5e48-159">Sauf si les paramètres doivent être nommés, nous vous recommandons d’apporter les paramètres plus utilisées positionnels afin que les utilisateurs devront pas taper le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="b5e48-159">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="b5e48-160">Déclarer des paramètres comme étant obligatoires ou facultatifs</span><span class="sxs-lookup"><span data-stu-id="b5e48-160">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="b5e48-161">Une applet de commande doit définir chaque paramètre optionnel ou un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b5e48-161">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="b5e48-162">Dans l’exemple **Get-Process** applet de commande, le `Name` paramètre est défini comme étant facultatifs, car le `Mandatory` mot clé n’est pas défini dans la déclaration d’attribut.</span><span class="sxs-lookup"><span data-stu-id="b5e48-162">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="b5e48-163">Prise en charge de la Validation de paramètre</span><span class="sxs-lookup"><span data-stu-id="b5e48-163">Supporting Parameter Validation</span></span>

<span data-ttu-id="b5e48-164">L’exemple **Get-Process** applet de commande ajoute un attribut de validation d’entrée, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), à le `Name` paramètre pour activer la validation que le entrée n’est ni `null` ni vide.</span><span class="sxs-lookup"><span data-stu-id="b5e48-164">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="b5e48-165">Cet attribut est un des attributs de validation de fournies par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5e48-165">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="b5e48-166">Pour obtenir des exemples d’autres attributs de validation, consultez [validation des entrées de paramètre de](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="b5e48-166">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b5e48-167">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="b5e48-167">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b5e48-168">Si votre applet de commande consiste à gérer l’entrée de ligne de commande, il doit remplacer la méthodes de traitement d’entrée appropriée.</span><span class="sxs-lookup"><span data-stu-id="b5e48-168">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="b5e48-169">Les méthodes de traitement d’entrée de base sont introduites dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b5e48-169">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="b5e48-170">Le **Get-Process** applet de commande remplace le [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode pour gérer la `Name` entrée de paramètre fournie par l’utilisateur ou un script.</span><span class="sxs-lookup"><span data-stu-id="b5e48-170">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="b5e48-171">Cette méthode obtient les processus pour chaque nom de processus demandé, ou tous les processus si aucun nom n’est fourni.</span><span class="sxs-lookup"><span data-stu-id="b5e48-171">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="b5e48-172">Notez que dans [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), l’appel à [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) correspond à la sortie mécanisme pour envoyer la sortie des objets au pipeline.</span><span class="sxs-lookup"><span data-stu-id="b5e48-172">Notice that in [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="b5e48-173">Le deuxième paramètre de cet appel, `enumerateCollection`, est définie sur `true` pour informer le runtime de Windows PowerShell pour énumérer le tableau de sortie d’objets de processus et d’écrire un seul processus à la fois à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-173">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="b5e48-174">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="b5e48-174">Code Sample</span></span>

<span data-ttu-id="b5e48-175">Pour l’ensemble C# exemple de code, consultez [exemple GetProcessSample02](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b5e48-175">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="b5e48-176">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="b5e48-176">Defining Object Types and Formatting</span></span>

<span data-ttu-id="b5e48-177">Windows PowerShell passe les informations entre les applets de commande à l’aide des objets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5e48-177">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="b5e48-178">Par conséquent, une applet de commande devrez peut-être définir son propre type, ou peut-être une applet de commande étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-178">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b5e48-179">Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="b5e48-179">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b5e48-180">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b5e48-180">Building the Cmdlet</span></span>

<span data-ttu-id="b5e48-181">Une fois que vous implémentez une applet de commande, vous devez l’inscrire avec Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5e48-181">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b5e48-182">Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="b5e48-182">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b5e48-183">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b5e48-183">Testing the Cmdlet</span></span>

<span data-ttu-id="b5e48-184">Lorsque votre applet de commande est enregistré avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e48-184">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="b5e48-185">Voici deux façons de tester le code pour l’applet de commande d’exemple.</span><span class="sxs-lookup"><span data-stu-id="b5e48-185">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="b5e48-186">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b5e48-186">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="b5e48-187">À l’invite Windows PowerShell, utilisez la commande suivante pour répertorier le processus Internet Explorer, qui est nommé « IEXPLORE. »</span><span class="sxs-lookup"><span data-stu-id="b5e48-187">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="b5e48-188">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b5e48-188">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="b5e48-189">Pour répertorier les processus Internet Explorer, Outlook et le bloc-notes, nommés « IEXPLORE », « OUTLOOK » et « NOTEPAD », utilisent la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="b5e48-189">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="b5e48-190">S’il existe plusieurs processus, tous d'entre eux sont affichés.</span><span class="sxs-lookup"><span data-stu-id="b5e48-190">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="b5e48-191">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b5e48-191">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="b5e48-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5e48-192">See Also</span></span>

[<span data-ttu-id="b5e48-193">Ajout de paramètres d’entrée de Pipeline de processus</span><span class="sxs-lookup"><span data-stu-id="b5e48-193">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="b5e48-194">Création de votre première applet de commande</span><span class="sxs-lookup"><span data-stu-id="b5e48-194">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="b5e48-195">Extension des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="b5e48-195">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="b5e48-196">Comment inscrire les applets de commande, fournisseurs et héberger des Applications</span><span class="sxs-lookup"><span data-stu-id="b5e48-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="b5e48-197">Informations de référence sur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5e48-197">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="b5e48-198">Exemples d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b5e48-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)
