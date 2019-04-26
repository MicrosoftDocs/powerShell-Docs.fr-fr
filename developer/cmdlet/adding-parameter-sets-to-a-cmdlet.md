---
title: Ajout de paramètre de jeux à une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: f0bff11618c18bf53b9c2a185445795a17306fa3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068835"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="b50a9-102">Ajout de jeux de paramètres à une applet de commande</span><span class="sxs-lookup"><span data-stu-id="b50a9-102">Adding Parameter Sets to a Cmdlet</span></span>

<span data-ttu-id="b50a9-103">Cette section décrit comment ajouter des ensembles de paramètre à l’applet de commande Stop-Process (décrit dans [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="b50a9-103">This section describes how to add parameter sets to the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span> <span data-ttu-id="b50a9-104">Comme pour les autres Stop-Process applets de commande décrites dans ce Guide du programmeur, cette applet de commande tente d’arrêter les processus qui sont récupérées à l’aide de l’applet de commande Get-Process (décrit dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="b50a9-104">Similar to the other Stop-Proc cmdlets described in this Programmer's Guide, this cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="b50a9-105">Rubriques de cette section sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b50a9-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="b50a9-106">Choses à savoir sur les jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="b50a9-106">Things to Know About Parameter Sets</span></span>](#Adding-Parameter-Sets-to-a-Cmdlet)

- [<span data-ttu-id="b50a9-107">Déclaration de la classe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b50a9-107">Declaring the Cmdlet Class</span></span>](#Declaring-the-Cmdlet-Class)

- [<span data-ttu-id="b50a9-108">Déclarer des paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b50a9-108">Declaring the Parameters of the Cmdlet</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="b50a9-109">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="b50a9-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="b50a9-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="b50a9-110">Code Sample</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="b50a9-111">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="b50a9-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="b50a9-112">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b50a9-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="b50a9-113">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b50a9-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="b50a9-114">Choses à savoir sur les jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="b50a9-114">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="b50a9-115">Windows PowerShell définit un paramètre défini en tant que groupe de paramètres qui fonctionnent ensemble.</span><span class="sxs-lookup"><span data-stu-id="b50a9-115">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="b50a9-116">En regroupant les paramètres d’applet de commande, vous pouvez créer une applet de commande unique que vous pouvez modifier ses fonctionnalités en fonction de l’utilisateur spécifie de quel groupe de paramètres.</span><span class="sxs-lookup"><span data-stu-id="b50a9-116">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="b50a9-117">Est un exemple d’une applet de commande qui utilise deux jeux de paramètres pour définir les différentes fonctionnalités du `Get-EventLog` applet de commande qui est fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b50a9-117">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="b50a9-118">Cette applet de commande renvoie des informations différentes lorsque l’utilisateur spécifie le `List` ou `LogName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="b50a9-118">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="b50a9-119">Si le `LogName` paramètre est spécifié, l’applet de commande renvoie des informations sur les événements dans un journal des événements donné.</span><span class="sxs-lookup"><span data-stu-id="b50a9-119">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="b50a9-120">Si le `List` paramètre est spécifié, l’applet de commande renvoie des informations sur le journal des fichiers (pas les informations d’événements qu’ils contiennent).</span><span class="sxs-lookup"><span data-stu-id="b50a9-120">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="b50a9-121">Dans ce cas, le `List` et `LogName` paramètres identifient deux jeux de paramètres distincts.</span><span class="sxs-lookup"><span data-stu-id="b50a9-121">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="b50a9-122">Deux points importants à retenir sur les jeux de paramètres est que le runtime Windows PowerShell n'utilise qu’un seul jeu de paramètres pour une entrée donnée, et que chaque jeu de paramètres doit avoir au moins un paramètre qui est unique pour ce jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="b50a9-122">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="b50a9-123">Pour illustrer ce dernier point, cette applet de commande Stop-Process utilise trois jeux de paramètres : `ProcessName`, `ProcessId`, et `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="b50a9-123">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="b50a9-124">Chacun de ces jeux de paramètre a un paramètre qui n’est pas dans les autres jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="b50a9-124">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="b50a9-125">Les jeux de paramètres puissent partager des autres paramètres, mais l’applet de commande utilise les paramètres uniques `ProcessName`, `ProcessId`, et `InputObject` pour identifier le jeu de paramètres que le runtime Windows PowerShell doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="b50a9-125">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="b50a9-126">Déclaration de la classe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b50a9-126">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="b50a9-127">La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b50a9-127">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="b50a9-128">Pour cette applet de commande, le verbe de cycle de vie « Stop » est utilisé, car l’applet de commande arrête les processus système.</span><span class="sxs-lookup"><span data-stu-id="b50a9-128">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="b50a9-129">Le nom de substantif « Proc » est utilisé, car l’applet de commande fonctionne sur les processus.</span><span class="sxs-lookup"><span data-stu-id="b50a9-129">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="b50a9-130">Dans la déclaration ci-dessous, notez que le nom du verbe et substantif applet de commande sont répercutées dans le nom de la classe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b50a9-130">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="b50a9-131">Pour plus d’informations sur les noms de verbe approuvé applet de commande, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="b50a9-131">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b50a9-132">Le code suivant est la définition de classe pour cette applet de commande Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="b50a9-132">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="b50a9-133">Déclarer des paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b50a9-133">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="b50a9-134">Cette applet de commande définit trois paramètres nécessaires comme entrée pour l’applet de commande (ces paramètres définissent également les jeux de paramètres), ainsi qu’un `Force` paramètre qui gère ce que fait l’applet de commande et un `PassThru` paramètre qui détermine si l’applet de commande renvoie un objet de sortie dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="b50a9-134">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="b50a9-135">Par défaut, cette applet de commande ne passe pas d’un objet à travers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="b50a9-135">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="b50a9-136">Pour plus d’informations sur ces deux derniers paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="b50a9-136">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="b50a9-137">Déclarer le paramètre de nom</span><span class="sxs-lookup"><span data-stu-id="b50a9-137">Declaring the Name Parameter</span></span>

<span data-ttu-id="b50a9-138">Ce paramètre d’entrée permet à l’utilisateur spécifier les noms des processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="b50a9-138">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="b50a9-139">Notez que le `ParameterSetName` attribut mot clé de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribut spécifie le `ProcessName` paramètre défini pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="b50a9-139">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="b50a9-140">Notez également que l’alias « ProcessName » est attribué à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="b50a9-140">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="b50a9-141">Déclarer le paramètre Id</span><span class="sxs-lookup"><span data-stu-id="b50a9-141">Declaring the Id Parameter</span></span>

<span data-ttu-id="b50a9-142">Ce paramètre d’entrée permet à l’utilisateur spécifier les identificateurs des processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="b50a9-142">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="b50a9-143">Notez que le `ParameterSetName` attribut mot clé de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribut spécifie le `ProcessId` jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="b50a9-143">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="b50a9-144">Notez également que l’alias « ProcessId » est attribué à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="b50a9-144">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="b50a9-145">Déclarer le paramètre InputObject</span><span class="sxs-lookup"><span data-stu-id="b50a9-145">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="b50a9-146">Ce paramètre d’entrée permet à l’utilisateur spécifier un objet d’entrée qui contient des informations sur les processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="b50a9-146">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="b50a9-147">Notez que le `ParameterSetName` attribut mot clé de la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribut spécifie le `InputObject` paramètre défini pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="b50a9-147">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="b50a9-148">Notez également que ce paramètre n’a pas d’alias.</span><span class="sxs-lookup"><span data-stu-id="b50a9-148">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="b50a9-149">Déclaration de paramètres dans plusieurs jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="b50a9-149">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="b50a9-150">Bien qu’il doit y avoir un paramètre unique pour chaque jeu de paramètres, les paramètres peuvent appartenir à plus d’un jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="b50a9-150">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="b50a9-151">Dans ce cas, donner du paramètre partagé un [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) déclaration d’attribut pour chaque jeu auquel le paramètre appartient.</span><span class="sxs-lookup"><span data-stu-id="b50a9-151">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="b50a9-152">Si un paramètre est dans tous les jeux de paramètres, vous uniquement obligé de déclarer l’attribut de paramètre qu’une seule fois et n’avez pas besoin de spécifier que le paramètre de nom du jeu.</span><span class="sxs-lookup"><span data-stu-id="b50a9-152">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b50a9-153">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="b50a9-153">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b50a9-154">Chaque applet de commande doit remplacer une méthode de traitement des entrées, ce sera souvent le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).</span><span class="sxs-lookup"><span data-stu-id="b50a9-154">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="b50a9-155">Dans cette applet de commande, le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode est remplacée afin que l’applet de commande peut traiter n’importe quel nombre de processus.</span><span class="sxs-lookup"><span data-stu-id="b50a9-155">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="b50a9-156">Il contient une instruction Select qui appelle une autre méthode basée sur le jeu de paramètres, l’utilisateur a spécifié.</span><span class="sxs-lookup"><span data-stu-id="b50a9-156">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="b50a9-157">Les méthodes d’assistance appelées par l’instruction Select ne sont pas décrits ici, mais vous pouvez voir leur implémentation dans l’exemple de code complet dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="b50a9-157">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b50a9-158">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="b50a9-158">Code Sample</span></span>

<span data-ttu-id="b50a9-159">Pour l’ensemble C# exemple de code, consultez [StopProcessSample04 exemple](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b50a9-159">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="b50a9-160">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="b50a9-160">Defining Object Types and Formatting</span></span>

<span data-ttu-id="b50a9-161">Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="b50a9-161">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="b50a9-162">Par conséquent, une applet de commande devez définir son propre type, ou l’applet de commande peut étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b50a9-162">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b50a9-163">Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="b50a9-163">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b50a9-164">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b50a9-164">Building the Cmdlet</span></span>

<span data-ttu-id="b50a9-165">Après l’implémentation d’une applet de commande, vous devez l’inscrire avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b50a9-165">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b50a9-166">Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="b50a9-166">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b50a9-167">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b50a9-167">Testing the Cmdlet</span></span>

<span data-ttu-id="b50a9-168">Lorsque votre applet de commande a été inscrite avec Windows PowerShell, testez-le en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b50a9-168">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="b50a9-169">Voici quelques tests qui montrent comment la `ProcessId` et `InputObject` paramètres peuvent être utilisés pour tester leurs jeux de paramètres pour arrêter un processus.</span><span class="sxs-lookup"><span data-stu-id="b50a9-169">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="b50a9-170">Avec Windows PowerShell de démarrer, exécutez l’applet de commande Stop-Process avec le `ProcessId` paramètre défini pour arrêter un processus en fonction de son identificateur.</span><span class="sxs-lookup"><span data-stu-id="b50a9-170">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="b50a9-171">Dans ce cas, l’applet de commande utilise le `ProcessId` paramètre défini pour arrêter le processus.</span><span class="sxs-lookup"><span data-stu-id="b50a9-171">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="b50a9-172">Avec Windows PowerShell de démarrer, exécutez l’applet de commande Stop-Process avec le `InputObject` paramètre défini pour arrêter des processus sur l’objet le bloc-notes récupérée par le `Get-Process` commande.</span><span class="sxs-lookup"><span data-stu-id="b50a9-172">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="b50a9-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b50a9-173">See Also</span></span>

[<span data-ttu-id="b50a9-174">Création d’une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="b50a9-174">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="b50a9-175">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b50a9-175">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="b50a9-176">Extension des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="b50a9-176">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="b50a9-177">Comment inscrire les applets de commande, fournisseurs et héberger des Applications</span><span class="sxs-lookup"><span data-stu-id="b50a9-177">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="b50a9-178">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b50a9-178">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
