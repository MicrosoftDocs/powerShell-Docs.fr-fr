---
title: Ajout de jeux de paramètres à une applet de commande | Microsoft Docs
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
ms.openlocfilehash: 59db96cf03ff7086e8c89fb45bc96fd805078ac8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364588"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="47662-102">Ajout de jeux de paramètres à une applet de commande</span><span class="sxs-lookup"><span data-stu-id="47662-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="47662-103">Choses à savoir sur les jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="47662-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="47662-104">Windows PowerShell définit un jeu de paramètres sous la forme d’un groupe de paramètres qui fonctionnent ensemble.</span><span class="sxs-lookup"><span data-stu-id="47662-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="47662-105">En regroupant les paramètres d’une applet de commande, vous pouvez créer une applet de commande unique qui peut modifier ses fonctionnalités en fonction du groupe de paramètres que l’utilisateur spécifie.</span><span class="sxs-lookup"><span data-stu-id="47662-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="47662-106">Un exemple d’applet de commande qui utilise deux jeux de paramètres pour définir des fonctionnalités différentes est l’applet de commande `Get-EventLog` fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47662-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="47662-107">Cette applet de commande retourne des informations différentes lorsque l’utilisateur spécifie le paramètre `List` ou `LogName`.</span><span class="sxs-lookup"><span data-stu-id="47662-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="47662-108">Si le paramètre `LogName` est spécifié, l’applet de commande renvoie des informations sur les événements dans un journal des événements donné.</span><span class="sxs-lookup"><span data-stu-id="47662-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="47662-109">Si le paramètre `List` est spécifié, l’applet de commande renvoie des informations sur les fichiers journaux eux-mêmes (pas sur les informations d’événement qu’elles contiennent).</span><span class="sxs-lookup"><span data-stu-id="47662-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="47662-110">Dans ce cas, les paramètres `List` et `LogName` identifient deux jeux de paramètres distincts.</span><span class="sxs-lookup"><span data-stu-id="47662-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="47662-111">Deux points importants à retenir concernant les jeux de paramètres sont que le runtime Windows PowerShell n’utilise qu’un seul jeu de paramètres pour une entrée particulière, et que chaque jeu de paramètres doit avoir au moins un paramètre unique pour ce jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="47662-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="47662-112">Pour illustrer ce dernier point, cette applet de commande Stop-proc utilise trois jeux de paramètres : `ProcessName`, `ProcessId` et `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="47662-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="47662-113">Chacun de ces jeux de paramètres possède un paramètre qui n’est pas dans les autres jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="47662-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="47662-114">Les jeux de paramètres peuvent partager d’autres paramètres, mais l’applet de commande utilise les paramètres uniques `ProcessName`, `ProcessId` et `InputObject` pour identifier le jeu de paramètres que le runtime Windows PowerShell doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="47662-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="47662-115">Déclaration de la classe d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="47662-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="47662-116">La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47662-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="47662-117">Pour cette applet de commande, le verbe « Stop » du cycle de vie est utilisé, car l’applet de commande arrête les processus système.</span><span class="sxs-lookup"><span data-stu-id="47662-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="47662-118">Le nom substantif « proc » est utilisé, car l’applet de commande fonctionne sur les processus.</span><span class="sxs-lookup"><span data-stu-id="47662-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="47662-119">Dans la déclaration ci-dessous, Notez que le verbe d’applet de commande et le nom substantif sont reflétés dans le nom de la classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47662-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="47662-120">Pour plus d’informations sur les noms des verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="47662-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="47662-121">Le code suivant est la définition de classe pour cette applet de commande Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="47662-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="47662-122">Déclaration des paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="47662-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="47662-123">Cette applet de commande définit trois paramètres nécessaires comme entrée pour l’applet de commande (ces paramètres définissent également les jeux de paramètres), ainsi qu’un paramètre `Force` qui gère ce que fait l’applet de commande et un paramètre `PassThru` qui détermine si l’applet de commande envoie un objet de sortie. via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="47662-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="47662-124">Par défaut, cette applet de commande ne passe pas un objet via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="47662-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="47662-125">Pour plus d’informations sur ces deux derniers paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="47662-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="47662-126">Déclaration du paramètre Name</span><span class="sxs-lookup"><span data-stu-id="47662-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="47662-127">Ce paramètre d’entrée permet à l’utilisateur de spécifier les noms des processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="47662-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="47662-128">Notez que le mot clé d’attribut `ParameterSetName` de l’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) spécifie le paramètre `ProcessName` défini pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="47662-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

<span data-ttu-id="47662-129">Notez également que l’alias « ProcessName » est donné à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="47662-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="47662-130">Déclaration du paramètre ID</span><span class="sxs-lookup"><span data-stu-id="47662-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="47662-131">Ce paramètre d’entrée permet à l’utilisateur de spécifier les identificateurs des processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="47662-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="47662-132">Notez que le mot clé d’attribut `ParameterSetName` de l’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) spécifie le jeu de paramètres `ProcessId`.</span><span class="sxs-lookup"><span data-stu-id="47662-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="47662-133">Notez également que l’alias « ProcessId » est donné à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="47662-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="47662-134">Déclaration du paramètre InputObject</span><span class="sxs-lookup"><span data-stu-id="47662-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="47662-135">Ce paramètre d’entrée permet à l’utilisateur de spécifier un objet d’entrée qui contient des informations sur les processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="47662-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="47662-136">Notez que le mot clé d’attribut `ParameterSetName` de l’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) spécifie le paramètre `InputObject` défini pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="47662-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="47662-137">Notez également que ce paramètre n’a pas d’alias.</span><span class="sxs-lookup"><span data-stu-id="47662-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="47662-138">Déclaration de paramètres dans plusieurs jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="47662-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="47662-139">Bien qu’il ne doive y avoir qu’un seul paramètre pour chaque jeu de paramètres, les paramètres peuvent appartenir à plusieurs jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="47662-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="47662-140">Dans ce cas, attribuez au paramètre Shared une déclaration d’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) pour chaque ensemble auquel appartient le paramètre.</span><span class="sxs-lookup"><span data-stu-id="47662-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="47662-141">Si un paramètre est dans tous les jeux de paramètres, vous ne devez déclarer l’attribut de paramètre qu’une seule fois et vous n’avez pas besoin de spécifier le nom du jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="47662-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="47662-142">Substitution d’une méthode de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="47662-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="47662-143">Chaque applet de commande doit remplacer une méthode de traitement d’entrée, le plus souvent, il s’agit de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="47662-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="47662-144">Dans cette applet de commande, la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) est remplacée afin que l’applet de commande puisse traiter un nombre quelconque de processus.</span><span class="sxs-lookup"><span data-stu-id="47662-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="47662-145">Il contient une instruction SELECT qui appelle une méthode différente selon le jeu de paramètres spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="47662-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="47662-146">Les méthodes d’assistance appelées par l’instruction SELECT ne sont pas décrites ici, mais vous pouvez voir leur implémentation dans l’exemple de code complet dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="47662-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="47662-147">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="47662-147">Code Sample</span></span>

<span data-ttu-id="47662-148">Pour obtenir l' C# exemple de code complet, consultez [exemple StopProcessSample04](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="47662-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="47662-149">Définition des types d’objets et de la mise en forme</span><span class="sxs-lookup"><span data-stu-id="47662-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="47662-150">Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="47662-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="47662-151">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47662-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="47662-152">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="47662-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="47662-153">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="47662-153">Building the Cmdlet</span></span>

<span data-ttu-id="47662-154">Après l’implémentation d’une applet de commande, vous devez l’inscrire auprès de Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47662-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="47662-155">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="47662-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="47662-156">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="47662-156">Testing the Cmdlet</span></span>

<span data-ttu-id="47662-157">Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, testez-la en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="47662-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="47662-158">Voici quelques tests qui montrent comment les paramètres `ProcessId` et `InputObject` peuvent être utilisés pour tester leurs jeux de paramètres afin d’arrêter un processus.</span><span class="sxs-lookup"><span data-stu-id="47662-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="47662-159">Après avoir démarré Windows PowerShell, exécutez l’applet de commande Stop-proc avec le paramètre `ProcessId` défini pour arrêter un processus en fonction de son identificateur.</span><span class="sxs-lookup"><span data-stu-id="47662-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="47662-160">Dans ce cas, l’applet de commande utilise le paramètre `ProcessId` défini pour arrêter le processus.</span><span class="sxs-lookup"><span data-stu-id="47662-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="47662-161">Après avoir démarré Windows PowerShell, exécutez l’applet de commande Stop-proc avec le paramètre `InputObject` défini sur arrêter les processus sur l’objet Notepad récupéré par la commande `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="47662-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="47662-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47662-162">See Also</span></span>

[<span data-ttu-id="47662-163">Création d’une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="47662-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="47662-164">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="47662-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="47662-165">[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="47662-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="47662-166">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="47662-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="47662-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="47662-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)