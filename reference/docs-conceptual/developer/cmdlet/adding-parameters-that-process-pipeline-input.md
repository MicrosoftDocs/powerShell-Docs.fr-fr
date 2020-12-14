---
ms.date: 09/13/2016
ms.topic: reference
title: Ajout de paramètres qui traitent l’entrée du pipeline
description: Ajout de paramètres qui traitent l’entrée du pipeline
ms.openlocfilehash: b150d5be93207d9c010a6d2d4de901b4526f1d79
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668352"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="15e60-103">Ajout de paramètres qui traitent l’entrée du pipeline</span><span class="sxs-lookup"><span data-stu-id="15e60-103">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="15e60-104">Une source d’entrée pour une applet de commande est un objet sur le pipeline qui provient d’une applet de commande en amont.</span><span class="sxs-lookup"><span data-stu-id="15e60-104">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="15e60-105">Cette section décrit comment ajouter un paramètre à l’applet de commande Get-Proc (décrit dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande) pour que l’applet de commande puisse traiter les objets de pipeline.</span><span class="sxs-lookup"><span data-stu-id="15e60-105">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="15e60-106">Cette applet de commande Get-Proc utilise un `Name` paramètre qui accepte l’entrée d’un objet pipeline, récupère des informations de processus à partir de l’ordinateur local en fonction des noms fournis, puis affiche des informations sur les processus sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="15e60-106">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="15e60-107">Définition de la classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="15e60-107">Defining the Cmdlet Class</span></span>

<span data-ttu-id="15e60-108">La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="15e60-108">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="15e60-109">Cette applet de commande récupère les informations de processus, le nom du verbe choisi ici est « obtenir ».</span><span class="sxs-lookup"><span data-stu-id="15e60-109">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="15e60-110">(Presque tout type d’applet de commande capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="15e60-110">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="15e60-111">Voici la définition de cette Get-Proc applet de commande.</span><span class="sxs-lookup"><span data-stu-id="15e60-111">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="15e60-112">Les détails de cette définition sont donnés dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="15e60-112">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="15e60-113">Définition de l’entrée à partir du pipeline</span><span class="sxs-lookup"><span data-stu-id="15e60-113">Defining Input from the Pipeline</span></span>

<span data-ttu-id="15e60-114">Cette section décrit comment définir une entrée à partir du pipeline pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="15e60-114">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="15e60-115">Cette applet de Get-Proc définit une propriété qui représente le `Name` paramètre comme décrit dans [Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="15e60-115">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>
<span data-ttu-id="15e60-116">(Pour obtenir des informations générales sur la déclaration des paramètres, consultez la rubrique.)</span><span class="sxs-lookup"><span data-stu-id="15e60-116">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="15e60-117">Toutefois, lorsqu’une applet de commande doit traiter l’entrée de pipeline, elle doit avoir ses paramètres liés aux valeurs d’entrée par le runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15e60-117">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="15e60-118">Pour ce faire, vous devez ajouter le `ValueFromPipeline` mot clé ou ajouter le `ValueFromPipelineByProperty` mot clé à la déclaration de l’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="15e60-118">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="15e60-119">Spécifiez le `ValueFromPipeline` mot clé si l’applet de commande accède à l’objet d’entrée complet.</span><span class="sxs-lookup"><span data-stu-id="15e60-119">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="15e60-120">Spécifiez `ValueFromPipelineByProperty` si la cmdlet accède uniquement à une propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="15e60-120">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="15e60-121">Voici la déclaration de paramètre pour le `Name` paramètre de cette Get-Proc applet de commande qui accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="15e60-121">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="35-44":::

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="15e60-122">La déclaration précédente affecte au `ValueFromPipeline` mot clé la valeur `true` afin que le runtime Windows PowerShell lie le paramètre à l’objet entrant si l’objet est du même type que le paramètre, ou s’il peut être forcé au même type.</span><span class="sxs-lookup"><span data-stu-id="15e60-122">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="15e60-123">Le `ValueFromPipelineByPropertyName` mot clé est également défini sur `true` afin que le runtime Windows PowerShell vérifie l’objet entrant pour une `Name` propriété.</span><span class="sxs-lookup"><span data-stu-id="15e60-123">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="15e60-124">Si l’objet entrant possède une telle propriété, le runtime lie le `Name` paramètre à la `Name` propriété de l’objet entrant.</span><span class="sxs-lookup"><span data-stu-id="15e60-124">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="15e60-125">La valeur du `ValueFromPipeline` mot clé Attribute pour un paramètre est prioritaire sur le paramètre du `ValueFromPipelineByPropertyName` mot clé.</span><span class="sxs-lookup"><span data-stu-id="15e60-125">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="15e60-126">Substitution d’une méthode de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="15e60-126">Overriding an Input Processing Method</span></span>

<span data-ttu-id="15e60-127">Si votre applet de commande doit gérer l’entrée de pipeline, elle doit remplacer les méthodes de traitement d’entrée appropriées.</span><span class="sxs-lookup"><span data-stu-id="15e60-127">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="15e60-128">Les méthodes de traitement d’entrée de base sont introduites lors de la [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="15e60-128">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="15e60-129">Cette applet de commande Get-Proc remplace la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) pour gérer l' `Name` entrée de paramètre fournie par l’utilisateur ou un script.</span><span class="sxs-lookup"><span data-stu-id="15e60-129">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="15e60-130">Cette méthode obtient les processus pour chaque nom de processus demandé ou tous les processus si aucun nom n’est fourni.</span><span class="sxs-lookup"><span data-stu-id="15e60-130">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="15e60-131">Notez que dans [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), l’appel à [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) est le mécanisme de sortie permettant d’envoyer des objets de sortie au pipeline.</span><span class="sxs-lookup"><span data-stu-id="15e60-131">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="15e60-132">Le deuxième paramètre de cet appel, `enumerateCollection` , est défini sur `true` pour indiquer au runtime Windows PowerShell d’énumérer le tableau d’objets de processus et d’écrire un processus à la fois sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="15e60-132">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="15e60-133">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="15e60-133">Code Sample</span></span>

<span data-ttu-id="15e60-134">Pour obtenir l’exemple de code C# complet, consultez [exemple GetProcessSample03](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="15e60-134">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="15e60-135">Définition des types d’objets et de la mise en forme</span><span class="sxs-lookup"><span data-stu-id="15e60-135">Defining Object Types and Formatting</span></span>

<span data-ttu-id="15e60-136">Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="15e60-136">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="15e60-137">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="15e60-137">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="15e60-138">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="15e60-138">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="15e60-139">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="15e60-139">Building the Cmdlet</span></span>

<span data-ttu-id="15e60-140">Après l’implémentation d’une applet de commande, celle-ci doit être inscrite auprès de Windows PowerShell via un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15e60-140">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="15e60-141">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="15e60-141">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="15e60-142">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="15e60-142">Testing the Cmdlet</span></span>

<span data-ttu-id="15e60-143">Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, testez-la en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="15e60-143">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="15e60-144">Par exemple, testez le code de l’applet de commande Sample.</span><span class="sxs-lookup"><span data-stu-id="15e60-144">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="15e60-145">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="15e60-145">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="15e60-146">À l’invite Windows PowerShell, entrez les commandes suivantes pour récupérer les noms de processus via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="15e60-146">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

  ```powershell
  PS> type ProcessNames | get-proc
  ```

  <span data-ttu-id="15e60-147">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="15e60-147">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      809      21  40856    4448    147    9.50  2288  iexplore
      737      21  26036   16348    144   22.03  3860  iexplore
       39       2   1024     388     30    0.08  3396  notepad
     3927      62  71836   26984    467  195.19  1848  OUTLOOK
  ```

- <span data-ttu-id="15e60-148">Entrez les lignes suivantes pour obtenir les objets processus qui ont une `Name` propriété des processus appelés « iexplore ».</span><span class="sxs-lookup"><span data-stu-id="15e60-148">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="15e60-149">Cet exemple utilise l' `Get-Process` applet de commande (fournie par Windows PowerShell) en tant que commande amont pour récupérer les processus « iexplore ».</span><span class="sxs-lookup"><span data-stu-id="15e60-149">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

  ```powershell
  PS> get-process iexplore | get-proc
  ```

  <span data-ttu-id="15e60-150">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="15e60-150">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
  ```

## <a name="see-also"></a><span data-ttu-id="15e60-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15e60-151">See Also</span></span>

[<span data-ttu-id="15e60-152">Ajout de paramètres qui traitent l’entrée de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="15e60-152">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="15e60-153">Création de votre première applet de commande</span><span class="sxs-lookup"><span data-stu-id="15e60-153">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="15e60-154">[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="15e60-154">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="15e60-155">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="15e60-155">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="15e60-156">Référence Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15e60-156">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="15e60-157">Exemples d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="15e60-157">Cmdlet Samples</span></span>](./cmdlet-samples.md)
