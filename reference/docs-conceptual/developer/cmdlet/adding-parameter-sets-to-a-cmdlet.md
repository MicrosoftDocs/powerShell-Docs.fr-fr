---
ms.date: 09/13/2016
ms.topic: reference
title: Ajout de jeux de paramètres à une applet de commande
description: Ajout de jeux de paramètres à une applet de commande
ms.openlocfilehash: dd5ee2a880a4d516ea82e5afe0ced12369197243
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648647"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="eec85-103">Ajout de jeux de paramètres à une applet de commande</span><span class="sxs-lookup"><span data-stu-id="eec85-103">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="eec85-104">Choses à savoir sur les jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="eec85-104">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="eec85-105">Windows PowerShell définit un jeu de paramètres sous la forme d’un groupe de paramètres qui fonctionnent ensemble.</span><span class="sxs-lookup"><span data-stu-id="eec85-105">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="eec85-106">En regroupant les paramètres d’une applet de commande, vous pouvez créer une applet de commande unique qui peut modifier ses fonctionnalités en fonction du groupe de paramètres que l’utilisateur spécifie.</span><span class="sxs-lookup"><span data-stu-id="eec85-106">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="eec85-107">L’applet de commande `Get-EventLog` fournie par Windows PowerShell est un exemple d’applet de commande qui utilise deux jeux de paramètres pour définir des fonctionnalités différentes.</span><span class="sxs-lookup"><span data-stu-id="eec85-107">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="eec85-108">Cette applet de commande retourne des informations différentes lorsque l’utilisateur spécifie le `List` `LogName` paramètre ou.</span><span class="sxs-lookup"><span data-stu-id="eec85-108">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="eec85-109">Si le `LogName` paramètre est spécifié, l’applet de commande retourne des informations sur les événements dans un journal des événements donné.</span><span class="sxs-lookup"><span data-stu-id="eec85-109">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="eec85-110">Si le `List` paramètre est spécifié, l’applet de commande renvoie des informations sur les fichiers journaux eux-mêmes (pas sur les informations d’événement qu’elles contiennent).</span><span class="sxs-lookup"><span data-stu-id="eec85-110">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="eec85-111">Dans ce cas, les `List` `LogName` paramètres et identifient deux jeux de paramètres distincts.</span><span class="sxs-lookup"><span data-stu-id="eec85-111">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="eec85-112">Deux points importants à retenir concernant les jeux de paramètres sont que le runtime Windows PowerShell n’utilise qu’un seul jeu de paramètres pour une entrée particulière, et que chaque jeu de paramètres doit avoir au moins un paramètre unique pour ce jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="eec85-112">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="eec85-113">Pour illustrer ce dernier point, cette applet de commande Stop-Proc utilise trois jeux de paramètres : `ProcessName` , `ProcessId` et `InputObject` .</span><span class="sxs-lookup"><span data-stu-id="eec85-113">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="eec85-114">Chacun de ces jeux de paramètres possède un paramètre qui n’est pas dans les autres jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="eec85-114">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="eec85-115">Les jeux de paramètres peuvent partager d’autres paramètres, mais l’applet de commande utilise les paramètres uniques `ProcessName` , `ProcessId` et `InputObject` pour identifier le jeu de paramètres que le runtime Windows PowerShell doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="eec85-115">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="eec85-116">Déclaration de la classe d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="eec85-116">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="eec85-117">La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eec85-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="eec85-118">Pour cette applet de commande, le verbe de cycle de vie « Stop » est utilisé, car l’applet de commande arrête les processus système.</span><span class="sxs-lookup"><span data-stu-id="eec85-118">For this cmdlet, the lifecycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="eec85-119">Le nom substantif « proc » est utilisé, car l’applet de commande fonctionne sur les processus.</span><span class="sxs-lookup"><span data-stu-id="eec85-119">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="eec85-120">Dans la déclaration ci-dessous, Notez que le verbe d’applet de commande et le nom substantif sont reflétés dans le nom de la classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eec85-120">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="eec85-121">Pour plus d’informations sur les noms des verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="eec85-121">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="eec85-122">Le code suivant est la définition de classe pour cette applet de commande Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="eec85-122">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="eec85-123">Déclaration des paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="eec85-123">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="eec85-124">Cette applet de commande définit trois paramètres nécessaires comme entrée de l’applet de commande (ces paramètres définissent également les jeux de paramètres), ainsi qu’un `Force` paramètre qui gère ce que fait l’applet de commande et un `PassThru` paramètre qui détermine si l’applet de commande envoie un objet de sortie via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="eec85-124">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="eec85-125">Par défaut, cette applet de commande ne passe pas un objet via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="eec85-125">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="eec85-126">Pour plus d’informations sur ces deux derniers paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="eec85-126">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="eec85-127">Déclaration du paramètre Name</span><span class="sxs-lookup"><span data-stu-id="eec85-127">Declaring the Name Parameter</span></span>

<span data-ttu-id="eec85-128">Ce paramètre d’entrée permet à l’utilisateur de spécifier les noms des processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="eec85-128">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="eec85-129">Notez que le `ParameterSetName` mot clé Attribute de l’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) spécifie le `ProcessName` jeu de paramètres pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="eec85-129">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs" range="44-58":::

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

<span data-ttu-id="eec85-130">Notez également que l’alias « ProcessName » est donné à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="eec85-130">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="eec85-131">Déclaration du paramètre ID</span><span class="sxs-lookup"><span data-stu-id="eec85-131">Declaring the Id Parameter</span></span>

<span data-ttu-id="eec85-132">Ce paramètre d’entrée permet à l’utilisateur de spécifier les identificateurs des processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="eec85-132">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="eec85-133">Notez que le `ParameterSetName` mot clé Attribute de l’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) spécifie le `ProcessId` jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="eec85-133">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="eec85-134">Notez également que l’alias « ProcessId » est donné à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="eec85-134">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="eec85-135">Déclaration du paramètre InputObject</span><span class="sxs-lookup"><span data-stu-id="eec85-135">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="eec85-136">Ce paramètre d’entrée permet à l’utilisateur de spécifier un objet d’entrée qui contient des informations sur les processus à arrêter.</span><span class="sxs-lookup"><span data-stu-id="eec85-136">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="eec85-137">Notez que le `ParameterSetName` mot clé Attribute de l’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) spécifie le `InputObject` jeu de paramètres pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="eec85-137">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="eec85-138">Notez également que ce paramètre n’a pas d’alias.</span><span class="sxs-lookup"><span data-stu-id="eec85-138">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="eec85-139">Déclaration de paramètres dans plusieurs jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="eec85-139">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="eec85-140">Bien qu’il ne doive y avoir qu’un seul paramètre pour chaque jeu de paramètres, les paramètres peuvent appartenir à plusieurs jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="eec85-140">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="eec85-141">Dans ce cas, attribuez au paramètre Shared une déclaration d’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) pour chaque ensemble auquel appartient le paramètre.</span><span class="sxs-lookup"><span data-stu-id="eec85-141">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="eec85-142">Si un paramètre est dans tous les jeux de paramètres, vous ne devez déclarer l’attribut de paramètre qu’une seule fois et vous n’avez pas besoin de spécifier le nom du jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="eec85-142">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="eec85-143">Substitution d’une méthode de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="eec85-143">Overriding an Input Processing Method</span></span>

<span data-ttu-id="eec85-144">Chaque applet de commande doit remplacer une méthode de traitement d’entrée, le plus souvent, il s’agit de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="eec85-144">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="eec85-145">Dans cette applet de commande, la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) est remplacée afin que l’applet de commande puisse traiter un nombre quelconque de processus.</span><span class="sxs-lookup"><span data-stu-id="eec85-145">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="eec85-146">Il contient une instruction SELECT qui appelle une méthode différente selon le jeu de paramètres spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eec85-146">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="eec85-147">Les méthodes d’assistance appelées par l’instruction SELECT ne sont pas décrites ici, mais vous pouvez voir leur implémentation dans l’exemple de code complet dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="eec85-147">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="eec85-148">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="eec85-148">Code Sample</span></span>

<span data-ttu-id="eec85-149">Pour obtenir l’exemple de code C# complet, consultez [exemple StopProcessSample04](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="eec85-149">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="eec85-150">Définition des types d’objets et de la mise en forme</span><span class="sxs-lookup"><span data-stu-id="eec85-150">Defining Object Types and Formatting</span></span>

<span data-ttu-id="eec85-151">Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="eec85-151">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="eec85-152">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="eec85-152">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="eec85-153">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="eec85-153">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="eec85-154">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="eec85-154">Building the Cmdlet</span></span>

<span data-ttu-id="eec85-155">Après l’implémentation d’une applet de commande, vous devez l’inscrire auprès de Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eec85-155">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="eec85-156">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="eec85-156">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="eec85-157">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="eec85-157">Testing the Cmdlet</span></span>

<span data-ttu-id="eec85-158">Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, testez-la en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="eec85-158">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="eec85-159">Voici quelques tests qui montrent comment les `ProcessId` paramètres et `InputObject` peuvent être utilisés pour tester leurs jeux de paramètres afin d’arrêter un processus.</span><span class="sxs-lookup"><span data-stu-id="eec85-159">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="eec85-160">Avec Windows PowerShell démarré, exécutez l’applet de commande Stop-Proc avec le `ProcessId` paramètre défini pour arrêter un processus en fonction de son identificateur.</span><span class="sxs-lookup"><span data-stu-id="eec85-160">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="eec85-161">Dans ce cas, l’applet de commande utilise le `ProcessId` paramètre défini pour arrêter le processus.</span><span class="sxs-lookup"><span data-stu-id="eec85-161">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

  ```
  PS> stop-proc -Id 444
  Confirm
  Are you sure you want to perform this action?
  Performing operation "stop-proc" on Target "notepad (444)".
  [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
  ```

- <span data-ttu-id="eec85-162">Après avoir démarré Windows PowerShell, exécutez l’applet de commande Stop-Proc avec le `InputObject` paramètre défini sur arrêter les processus sur l’objet Notepad récupéré par la `Get-Process` commande.</span><span class="sxs-lookup"><span data-stu-id="eec85-162">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

  ```
  PS> get-process notepad | stop-proc
  Confirm
  Are you sure you want to perform this action?
  Performing operation "stop-proc" on Target "notepad (444)".
  [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
  ```

## <a name="see-also"></a><span data-ttu-id="eec85-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eec85-163">See Also</span></span>

[<span data-ttu-id="eec85-164">Création d’une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="eec85-164">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="eec85-165">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eec85-165">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="eec85-166">[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="eec85-166">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="eec85-167">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="eec85-167">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="eec85-168">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="eec85-168">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
