---
title: Ajout de paramètres qui traitent l’entrée de pipeline | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 4966ac274713899e7ea9e0c375dca220a972a1b5
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978727"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="c9bb3-102">Ajout de paramètres qui traitent l’entrée du pipeline</span><span class="sxs-lookup"><span data-stu-id="c9bb3-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="c9bb3-103">Une source d’entrée pour une applet de commande est un objet sur le pipeline qui provient d’une applet de commande en amont.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="c9bb3-104">Cette section décrit comment ajouter un paramètre à l’applet de commande « obtenir-proc » (décrit dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande) afin que l’applet de commande puisse traiter les objets de pipeline.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="c9bb3-105">Cette applet de commande Accept-proc utilise un paramètre `Name` qui accepte l’entrée d’un objet pipeline, récupère des informations de processus à partir de l’ordinateur local en fonction des noms fournis, puis affiche des informations sur les processus sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="c9bb3-106">Définition de la classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9bb3-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="c9bb3-107">La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="c9bb3-108">Cette applet de commande récupère les informations de processus, le nom du verbe choisi ici est « obtenir ».</span><span class="sxs-lookup"><span data-stu-id="c9bb3-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="c9bb3-109">(Presque tout type d’applet de commande capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="c9bb3-110">Voici la définition de cette applet de commande « obtenir-proc ».</span><span class="sxs-lookup"><span data-stu-id="c9bb3-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="c9bb3-111">Les détails de cette définition sont donnés dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="c9bb3-112">Définition de l’entrée à partir du pipeline</span><span class="sxs-lookup"><span data-stu-id="c9bb3-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="c9bb3-113">Cette section décrit comment définir une entrée à partir du pipeline pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="c9bb3-114">Cette applet de commande obtenir-proc définit une propriété qui représente le paramètre `Name` comme décrit dans [Ajout de paramètres qui traitent l’entrée de ligne de commande](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="c9bb3-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>
<span data-ttu-id="c9bb3-115">(Pour obtenir des informations générales sur la déclaration des paramètres, consultez la rubrique.)</span><span class="sxs-lookup"><span data-stu-id="c9bb3-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="c9bb3-116">Toutefois, lorsqu’une applet de commande doit traiter l’entrée de pipeline, elle doit avoir ses paramètres liés aux valeurs d’entrée par le runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="c9bb3-117">Pour ce faire, vous devez ajouter le mot clé `ValueFromPipeline` ou ajouter le mot clé `ValueFromPipelineByProperty` à la déclaration d’attribut [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="c9bb3-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="c9bb3-118">Spécifiez le mot clé `ValueFromPipeline` si l’applet de commande accède à l’objet d’entrée complet.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="c9bb3-119">Spécifiez le `ValueFromPipelineByProperty` si l’applet de commande accède uniquement à une propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="c9bb3-120">Voici la déclaration de paramètre pour le paramètre `Name` de cette applet de commande Accept-proc qui accepte l’entrée de pipeline.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

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

<span data-ttu-id="c9bb3-121">La déclaration précédente définit le mot clé `ValueFromPipeline` sur `true` afin que le runtime Windows PowerShell lie le paramètre à l’objet entrant si l’objet est du même type que le paramètre, ou s’il peut être forcé au même type.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="c9bb3-122">Le mot clé `ValueFromPipelineByPropertyName` est également défini sur `true` afin que le runtime Windows PowerShell vérifie l’objet entrant pour une propriété `Name`.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="c9bb3-123">Si l’objet entrant possède une telle propriété, le runtime lie le paramètre `Name` à la propriété `Name` de l’objet entrant.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="c9bb3-124">La valeur du mot clé d’attribut `ValueFromPipeline` pour un paramètre est prioritaire sur le paramètre du mot clé `ValueFromPipelineByPropertyName`.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="c9bb3-125">Substitution d’une méthode de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="c9bb3-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="c9bb3-126">Si votre applet de commande doit gérer l’entrée de pipeline, elle doit remplacer les méthodes de traitement d’entrée appropriées.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="c9bb3-127">Les méthodes de traitement d’entrée de base sont introduites lors de la [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="c9bb3-128">Cette applet de commande obtenir-proc remplace la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) pour gérer le `Name` entrée de paramètre fournie par l’utilisateur ou un script.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="c9bb3-129">Cette méthode obtient les processus pour chaque nom de processus demandé ou tous les processus si aucun nom n’est fourni.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="c9bb3-130">Notez que dans [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), l’appel à [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) est le mécanisme de sortie permettant d’envoyer des objets de sortie au pipeline.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="c9bb3-131">Le deuxième paramètre de cet appel, `enumerateCollection`, est défini sur `true` pour indiquer au runtime Windows PowerShell d’énumérer le tableau d’objets de processus et d’écrire un processus à la fois sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="c9bb3-132">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="c9bb3-132">Code Sample</span></span>

<span data-ttu-id="c9bb3-133">Pour obtenir l' C# exemple de code complet, consultez [exemple GetProcessSample03](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c9bb3-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="c9bb3-134">Définition des types d’objets et de la mise en forme</span><span class="sxs-lookup"><span data-stu-id="c9bb3-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="c9bb3-135">Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="c9bb3-136">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="c9bb3-137">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="c9bb3-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="c9bb3-138">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c9bb3-138">Building the Cmdlet</span></span>

<span data-ttu-id="c9bb3-139">Après l’implémentation d’une applet de commande, celle-ci doit être inscrite auprès de Windows PowerShell via un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="c9bb3-140">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="c9bb3-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="c9bb3-141">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c9bb3-141">Testing the Cmdlet</span></span>

<span data-ttu-id="c9bb3-142">Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, testez-la en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="c9bb3-143">Par exemple, testez le code de l’applet de commande Sample.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="c9bb3-144">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c9bb3-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="c9bb3-145">À l’invite Windows PowerShell, entrez les commandes suivantes pour récupérer les noms de processus via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

  ```powershell
  PS> type ProcessNames | get-proc
  ```

  <span data-ttu-id="c9bb3-146">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-146">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      809      21  40856    4448    147    9.50  2288  iexplore
      737      21  26036   16348    144   22.03  3860  iexplore
       39       2   1024     388     30    0.08  3396  notepad
     3927      62  71836   26984    467  195.19  1848  OUTLOOK
  ```

- <span data-ttu-id="c9bb3-147">Entrez les lignes suivantes pour obtenir les objets processus qui ont une propriété `Name` à partir des processus appelés « IEXPLORE ».</span><span class="sxs-lookup"><span data-stu-id="c9bb3-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="c9bb3-148">Cet exemple utilise l’applet de commande `Get-Process` (fournie par Windows PowerShell) en tant que commande amont pour récupérer les processus « IEXPLORE ».</span><span class="sxs-lookup"><span data-stu-id="c9bb3-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

  ```powershell
  PS> get-process iexplore | get-proc
  ```

  <span data-ttu-id="c9bb3-149">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c9bb3-149">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
  ```

## <a name="see-also"></a><span data-ttu-id="c9bb3-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9bb3-150">See Also</span></span>

[<span data-ttu-id="c9bb3-151">Ajout de paramètres qui traitent l’entrée de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="c9bb3-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="c9bb3-152">Création de votre première applet de commande</span><span class="sxs-lookup"><span data-stu-id="c9bb3-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="c9bb3-153">[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="c9bb3-153">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="c9bb3-154">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="c9bb3-154">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="c9bb3-155">Référence Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9bb3-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="c9bb3-156">Exemples d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c9bb3-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
