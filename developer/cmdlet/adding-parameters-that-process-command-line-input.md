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
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322749"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="14ae3-102">Ajout de paramètres qui traitent l’entrée de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="14ae3-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="14ae3-103">Une source d’entrée pour une applet de commande est la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="14ae3-104">Cette rubrique explique comment ajouter un paramètre à l’applet de commande **« obtenir-proc »** (décrit dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande) afin que l’applet de commande puisse traiter l’entrée de l’ordinateur local en fonction d’objets explicites passés à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="14ae3-105">L’applet de commande **« obtenir-proc »** décrite ici récupère les processus en fonction de leurs noms, puis affiche des informations sur les processus à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="14ae3-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="14ae3-106">Définition de la classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="14ae3-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="14ae3-107">La première étape de la création des applets de commande consiste à nommer l’applet de commande et la déclaration de la classe .NET Framework qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="14ae3-108">Cette applet de commande récupère les informations sur le processus. le nom du verbe choisi ici est « obtenir ».</span><span class="sxs-lookup"><span data-stu-id="14ae3-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="14ae3-109">(Presque tout type d’applet de commande capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="14ae3-110">Voici la déclaration de classe pour l’applet de commande **« obtenir-proc »** .</span><span class="sxs-lookup"><span data-stu-id="14ae3-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="14ae3-111">Des informations détaillées sur cette définition sont fournies dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="14ae3-112">Déclarer des paramètres</span><span class="sxs-lookup"><span data-stu-id="14ae3-112">Declaring Parameters</span></span>

<span data-ttu-id="14ae3-113">Un paramètre d’applet de commande permet à l’utilisateur de fournir une entrée à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="14ae3-114">Dans l’exemple suivant, **obtenir-proc** et `Get-Member` sont les noms des applets de commande canalisées `MemberType` , et est un paramètre `Get-Member` de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="14ae3-115">Le paramètre a l’argument « Property ».</span><span class="sxs-lookup"><span data-stu-id="14ae3-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="14ae3-116">**Bloc de > PS-proc ; `get-member` -MemberType, propriété**</span><span class="sxs-lookup"><span data-stu-id="14ae3-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="14ae3-117">Pour déclarer des paramètres pour une applet de commande, vous devez d’abord définir les propriétés qui représentent les paramètres.</span><span class="sxs-lookup"><span data-stu-id="14ae3-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="14ae3-118">Dans l’applet de commande **obtenir-proc** , le seul `Name`paramètre est, qui, dans ce cas, représente le nom de l’objet de processus .NET Framework à récupérer.</span><span class="sxs-lookup"><span data-stu-id="14ae3-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="14ae3-119">Par conséquent, la classe d’applet de commande définit une propriété de type chaîne pour accepter un tableau de noms.</span><span class="sxs-lookup"><span data-stu-id="14ae3-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="14ae3-120">Voici la déclaration de paramètre pour le `Name` paramètre de l’applet de commande **« obtenir-proc »** .</span><span class="sxs-lookup"><span data-stu-id="14ae3-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

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

<span data-ttu-id="14ae3-121">Pour informer le runtime Windows PowerShell que cette propriété est le `Name` paramètre, un attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) est ajouté à la définition de propriété.</span><span class="sxs-lookup"><span data-stu-id="14ae3-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="14ae3-122">La syntaxe de base pour déclarer cet attribut est `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="14ae3-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="14ae3-123">Un paramètre doit être explicitement marqué comme public.</span><span class="sxs-lookup"><span data-stu-id="14ae3-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="14ae3-124">Les paramètres qui ne sont pas marqués comme étant des paramètres par défaut publics et internes sont introuvables par le runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14ae3-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="14ae3-125">Cette applet de commande utilise un tableau de chaînes `Name` pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="14ae3-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="14ae3-126">Si possible, votre applet de commande doit également définir un paramètre en tant que tableau, car cela permet à l’applet de commande d’accepter plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="14ae3-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="14ae3-127">Points à retenir sur les définitions de paramètres</span><span class="sxs-lookup"><span data-stu-id="14ae3-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="14ae3-128">Les noms de paramètres et les types de données Windows PowerShell prédéfinis doivent être réutilisés autant que possible pour garantir la compatibilité de votre applet de commande avec les applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14ae3-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="14ae3-129">Par exemple, si toutes les applets de commande utilisent le `Id` nom de paramètre prédéfini pour identifier une ressource, l’utilisateur peut facilement comprendre la signification du paramètre, quelle que soit l’applet de commande qu’il utilise.</span><span class="sxs-lookup"><span data-stu-id="14ae3-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="14ae3-130">Fondamentalement, les noms de paramètres suivent les mêmes règles que celles utilisées pour les noms de variables dans le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="14ae3-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="14ae3-131">Pour plus d’informations sur la dénomination des paramètres, consultez [noms des paramètres](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb)de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="14ae3-132">Windows PowerShell réserve quelques noms de paramètres pour fournir une expérience utilisateur cohérente.</span><span class="sxs-lookup"><span data-stu-id="14ae3-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="14ae3-133">N’utilisez pas ces noms de paramètres `WhatIf`: `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, et `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="14ae3-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="14ae3-134">En outre, les alias suivants pour ces noms de paramètres sont réservés : `vb`, `db`, `ea` `ev` `ov`,, et `ob`.</span><span class="sxs-lookup"><span data-stu-id="14ae3-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="14ae3-135">`Name`est un nom de paramètre simple et commun, recommandé pour une utilisation dans vos applets de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="14ae3-136">Il est préférable de choisir un nom de paramètre comme celui-ci plutôt qu’un nom complexe propre à une applet de commande spécifique et difficile à retenir.</span><span class="sxs-lookup"><span data-stu-id="14ae3-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="14ae3-137">Les paramètres ne sont pas sensibles à la casse dans Windows PowerShell, bien que l’interpréteur de commandes conserve par défaut la casse.</span><span class="sxs-lookup"><span data-stu-id="14ae3-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="14ae3-138">Le respect de la casse des arguments dépend du fonctionnement de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="14ae3-139">Les arguments sont passés à un paramètre comme spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="14ae3-140">Pour obtenir des exemples d’autres déclarations de paramètres, consultez [paramètres d’applet](./cmdlet-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="14ae3-141">Déclarer des paramètres en tant que positionnels ou nommés</span><span class="sxs-lookup"><span data-stu-id="14ae3-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="14ae3-142">Une applet de commande doit définir chaque paramètre en tant que paramètre positionnel ou nommé.</span><span class="sxs-lookup"><span data-stu-id="14ae3-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="14ae3-143">Les deux types de paramètres acceptent des arguments uniques, plusieurs arguments séparés par des virgules et des paramètres booléens.</span><span class="sxs-lookup"><span data-stu-id="14ae3-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="14ae3-144">Un paramètre booléen, également appelé *commutateur*, gère uniquement les paramètres booléens.</span><span class="sxs-lookup"><span data-stu-id="14ae3-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="14ae3-145">Le commutateur est utilisé pour déterminer la présence du paramètre.</span><span class="sxs-lookup"><span data-stu-id="14ae3-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="14ae3-146">La valeur par défaut `false`recommandée est.</span><span class="sxs-lookup"><span data-stu-id="14ae3-146">The recommended default is `false`.</span></span>

<span data-ttu-id="14ae3-147">L’applet de commande Sample **-proc** définit `Name` le paramètre en tant que paramètre positionnel avec la position 0.</span><span class="sxs-lookup"><span data-stu-id="14ae3-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="14ae3-148">Cela signifie que le premier argument entré par l’utilisateur sur la ligne de commande est automatiquement inséré pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="14ae3-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="14ae3-149">Si vous souhaitez définir un paramètre nommé, pour lequel l’utilisateur doit spécifier le nom de paramètre à partir de la ligne de commande `Position` , laissez le mot clé en dehors de la déclaration d’attribut.</span><span class="sxs-lookup"><span data-stu-id="14ae3-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="14ae3-150">À moins que les paramètres ne soient nommés, nous vous recommandons de définir la position des paramètres les plus utilisés de manière à ce que les utilisateurs n’aient pas à taper le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="14ae3-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="14ae3-151">Déclarer des paramètres comme obligatoires ou facultatifs</span><span class="sxs-lookup"><span data-stu-id="14ae3-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="14ae3-152">Une applet de commande doit définir chaque paramètre en tant que paramètre facultatif ou obligatoire.</span><span class="sxs-lookup"><span data-stu-id="14ae3-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="14ae3-153">Dans l’applet de commande Sample **-proc** , `Name` le paramètre est défini comme étant facultatif `Mandatory` , car le mot clé n’est pas défini dans la déclaration d’attribut.</span><span class="sxs-lookup"><span data-stu-id="14ae3-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="14ae3-154">Prise en charge de la validation des paramètres</span><span class="sxs-lookup"><span data-stu-id="14ae3-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="14ae3-155">L’applet de commande Sample **-proc** ajoute un attribut de validation d’entrée, [System. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute) `Name` , au paramètre pour permettre la validation que l' `null` entrée n’est ni ni vide.</span><span class="sxs-lookup"><span data-stu-id="14ae3-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="14ae3-156">Cet attribut est l’un des nombreux attributs de validation fournis par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14ae3-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="14ae3-157">Pour obtenir des exemples d’autres attributs de validation, consultez [validation des entrées de paramètres](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="14ae3-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="14ae3-158">Substitution d’une méthode de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="14ae3-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="14ae3-159">Si votre applet de commande doit gérer l’entrée de ligne de commande, elle doit remplacer les méthodes de traitement d’entrée appropriées.</span><span class="sxs-lookup"><span data-stu-id="14ae3-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="14ae3-160">Les méthodes de traitement d’entrée de base sont introduites lors de la [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="14ae3-161">L’applet de commande **obtenir-proc** remplace la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) pour `Name` gérer l’entrée de paramètre fournie par l’utilisateur ou un script.</span><span class="sxs-lookup"><span data-stu-id="14ae3-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="14ae3-162">Cette méthode obtient les processus pour chaque nom de processus demandé, ou tous les processus si aucun nom n’est fourni.</span><span class="sxs-lookup"><span data-stu-id="14ae3-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="14ae3-163">Notez que dans [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), l’appel à [System. Management. Automation. applet de commande. WriteObject% 28System. Object% 2CSystem. Boolean% 29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) est le mécanisme de sortie permettant d’envoyer des objets de sortie à l’applet de commande canaux.</span><span class="sxs-lookup"><span data-stu-id="14ae3-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="14ae3-164">Le deuxième paramètre de cet appel, `enumerateCollection`, est défini sur `true` pour indiquer à l’exécution de Windows PowerShell d’énumérer le tableau de sortie des objets de processus et d’écrire un processus à la fois sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="14ae3-165">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="14ae3-165">Code Sample</span></span>

<span data-ttu-id="14ae3-166">Pour obtenir l' C# exemple de code complet, consultez [exemple GetProcessSample02](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="14ae3-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="14ae3-167">Définition des types d’objets et de la mise en forme</span><span class="sxs-lookup"><span data-stu-id="14ae3-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="14ae3-168">Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="14ae3-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="14ae3-169">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou une applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="14ae3-170">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="14ae3-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="14ae3-171">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="14ae3-171">Building the Cmdlet</span></span>

<span data-ttu-id="14ae3-172">Après avoir implémenté une applet de commande, vous devez l’inscrire auprès de Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="14ae3-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="14ae3-173">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="14ae3-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="14ae3-174">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="14ae3-174">Testing the Cmdlet</span></span>

<span data-ttu-id="14ae3-175">Lorsque votre applet de commande est inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="14ae3-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="14ae3-176">Voici deux façons de tester le code de l’applet de commande Sample.</span><span class="sxs-lookup"><span data-stu-id="14ae3-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="14ae3-177">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="14ae3-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="14ae3-178">À l’invite de commandes Windows PowerShell, utilisez la commande suivante pour répertorier le processus Internet Explorer, qui est nommé « IEXPLORE ».</span><span class="sxs-lookup"><span data-stu-id="14ae3-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="14ae3-179">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="14ae3-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="14ae3-180">Pour répertorier les processus Internet Explorer, Outlook et bloc-notes nommés « IEXPLORE », « OUTLOOK » et « NOTEPAD », utilisez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="14ae3-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="14ae3-181">S’il existe plusieurs processus, ils sont tous affichés.</span><span class="sxs-lookup"><span data-stu-id="14ae3-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="14ae3-182">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="14ae3-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="14ae3-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14ae3-183">See Also</span></span>

[<span data-ttu-id="14ae3-184">Ajout de paramètres qui traitent l’entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="14ae3-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="14ae3-185">Création de votre première applet de commande</span><span class="sxs-lookup"><span data-stu-id="14ae3-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="14ae3-186">Extension des types d’objets et de la mise en forme</span><span class="sxs-lookup"><span data-stu-id="14ae3-186">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="14ae3-187">Comment inscrire des applets de commande, des fournisseurs et des applications hôtes</span><span class="sxs-lookup"><span data-stu-id="14ae3-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="14ae3-188">Informations de référence sur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="14ae3-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="14ae3-189">Exemples d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="14ae3-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
