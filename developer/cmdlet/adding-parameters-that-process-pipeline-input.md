---
title: Ajout de paramètres qui traitent l’entrée de Pipeline | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: c790d20a792bcdb4a34485e53375560e129433a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854535"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="c1958-102">Ajout de paramètres qui traitent l’entrée du pipeline</span><span class="sxs-lookup"><span data-stu-id="c1958-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="c1958-103">Une source d’entrée pour une applet de commande est un objet sur le pipeline qui provient d’une applet de commande en amont.</span><span class="sxs-lookup"><span data-stu-id="c1958-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="c1958-104">Cette section décrit comment ajouter un paramètre à l’applet de commande Get-Process (décrit dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)) afin que l’applet de commande peut traiter les objets pipeline.</span><span class="sxs-lookup"><span data-stu-id="c1958-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="c1958-105">Cette applet de commande Get-Process utilise un `Name` paramètre qui accepte les entrées à partir d’un objet de pipeline, récupère les informations de processus à partir de l’ordinateur local selon les noms fournis, puis affiche des informations sur les processus à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c1958-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

<span data-ttu-id="c1958-106">Rubriques de cette section sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c1958-106">Topics in this section include the following:</span></span>

- [<span data-ttu-id="c1958-107">Définition de la classe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c1958-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="c1958-108">Définition d’entrée provenant du Pipeline</span><span class="sxs-lookup"><span data-stu-id="c1958-108">Defining Input from the Pipeline</span></span>](#Defining-Input-from-the-Pipeline)

- [<span data-ttu-id="c1958-109">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="c1958-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="c1958-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="c1958-110">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="c1958-111">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="c1958-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="c1958-112">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c1958-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="c1958-113">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c1958-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="c1958-114">Définition de la classe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c1958-114">Defining the Cmdlet Class</span></span>

<span data-ttu-id="c1958-115">La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c1958-115">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="c1958-116">Cette applet de commande récupère des informations de processus, par conséquent, le nom du verbe choisi ici est « Get ».</span><span class="sxs-lookup"><span data-stu-id="c1958-116">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="c1958-117">(Presque toute sorte de l’applet de commande qui est capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="c1958-117">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="c1958-118">Voici la définition de cette applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="c1958-118">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="c1958-119">Informations de cette définition sont fournies dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c1958-119">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="c1958-120">Définition d’entrée provenant du Pipeline</span><span class="sxs-lookup"><span data-stu-id="c1958-120">Defining Input from the Pipeline</span></span>

<span data-ttu-id="c1958-121">Cette section décrit comment définir l’entrée du pipeline pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c1958-121">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="c1958-122">Cette applet de commande Get-Process définit une propriété qui représente le `Name` paramètre comme décrit dans [ajoutant des paramètres de cette entrée de ligne de commande de processus](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="c1958-122">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="c1958-123">(Consultez la rubrique appropriée pour des informations générales sur la déclaration de paramètres).</span><span class="sxs-lookup"><span data-stu-id="c1958-123">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="c1958-124">Toutefois, quand une applet de commande doit traiter l’entrée de pipeline, il doit avoir ses paramètres liés aux valeurs d’entrée par le runtime de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1958-124">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="c1958-125">Pour ce faire, vous devez ajouter le `ValueFromPipeline` mot clé ou d’ajouter le `ValueFromPipelineByProperty` mot clé à la [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) déclaration de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="c1958-125">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="c1958-126">Spécifiez le `ValueFromPipeline` mot clé si l’applet de commande accède à l’objet d’entrée complet.</span><span class="sxs-lookup"><span data-stu-id="c1958-126">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="c1958-127">Spécifiez le `ValueFromPipelineByProperty` si l’applet de commande accède à une propriété de l’objet uniquement.</span><span class="sxs-lookup"><span data-stu-id="c1958-127">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="c1958-128">Voici la déclaration de paramètre pour le `Name` paramètre de cette applet de commande Get-Process qui accepte les entrées de pipeline.</span><span class="sxs-lookup"><span data-stu-id="c1958-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<span data-ttu-id="c1958-129">Les ensembles de déclaration précédente le `ValueFromPipeline` mot clé à `true` afin que le runtime Windows PowerShell lier le paramètre à l’objet entrant, si l’objet est le même type que le paramètre, ou si elle peut être forcé au même type.</span><span class="sxs-lookup"><span data-stu-id="c1958-129">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="c1958-130">Le `ValueFromPipelineByPropertyName` mot clé est également défini sur `true` afin que le runtime Windows PowerShell recherche l’objet entrant pour un `Name` propriété.</span><span class="sxs-lookup"><span data-stu-id="c1958-130">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="c1958-131">Si l’objet entrant a une telle propriété, le runtime crée une liaison le `Name` paramètre à la `Name` propriété de l’objet entrant.</span><span class="sxs-lookup"><span data-stu-id="c1958-131">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="c1958-132">Le paramètre de la `ValueFromPipeline` mot clé d’attribut d’un paramètre est prioritaire sur le paramètre pour le `ValueFromPipelineByPropertyName` mot clé.</span><span class="sxs-lookup"><span data-stu-id="c1958-132">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="c1958-133">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="c1958-133">Overriding an Input Processing Method</span></span>

<span data-ttu-id="c1958-134">Si votre applet de commande consiste à gérer l’entrée de pipeline, il doit remplacer la méthodes de traitement d’entrée appropriée.</span><span class="sxs-lookup"><span data-stu-id="c1958-134">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="c1958-135">Les méthodes de traitement d’entrée de base sont introduites dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c1958-135">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="c1958-136">Cette applet de commande Get-Process remplace le [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode pour gérer la `Name` entrée de paramètre fournie par l’utilisateur ou un script.</span><span class="sxs-lookup"><span data-stu-id="c1958-136">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="c1958-137">Cette méthode obtient les processus pour chaque nom de processus demandé ou tous les processus si aucun nom n’est fourni.</span><span class="sxs-lookup"><span data-stu-id="c1958-137">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="c1958-138">Notez que dans [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), l’appel à [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) est le mécanisme de sortie pour envoyer des objets de sortie au pipeline.</span><span class="sxs-lookup"><span data-stu-id="c1958-138">Notice that within [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="c1958-139">Le deuxième paramètre de cet appel, `enumerateCollection`, est défini sur `true` indiquer au runtime de Windows PowerShell d’énumérer le tableau d’objets de processus et écrire un seul processus à la fois à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c1958-139">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="c1958-140">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="c1958-140">Code Sample</span></span>

<span data-ttu-id="c1958-141">Pour l’ensemble C# exemple de code, consultez [GetProcessSample03 exemple](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c1958-141">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="c1958-142">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="c1958-142">Defining Object Types and Formatting</span></span>

<span data-ttu-id="c1958-143">Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="c1958-143">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="c1958-144">Par conséquent, peut-être une applet de commande définir son propre type, ou peut-être l’applet de commande étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c1958-144">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="c1958-145">Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="c1958-145">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="c1958-146">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c1958-146">Building the Cmdlet</span></span>

<span data-ttu-id="c1958-147">Après l’implémentation d’une applet de commande, il doit être enregistré avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1958-147">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="c1958-148">Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="c1958-148">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="c1958-149">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c1958-149">Testing the Cmdlet</span></span>

<span data-ttu-id="c1958-150">Lorsque votre applet de commande a été inscrite avec Windows PowerShell, testez-le en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c1958-150">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="c1958-151">Par exemple, tester le code de l’applet de commande d’exemple.</span><span class="sxs-lookup"><span data-stu-id="c1958-151">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="c1958-152">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c1958-152">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="c1958-153">À l’invite Windows PowerShell, entrez les commandes suivantes pour récupérer les noms de processus à travers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="c1958-153">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="c1958-154">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c1958-154">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="c1958-155">Entrez les lignes suivantes pour obtenir les objets de processus qui ont un `Name` propriété des processus appelé « IEXPLORE ».</span><span class="sxs-lookup"><span data-stu-id="c1958-155">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="c1958-156">Cet exemple utilise le `Get-Process` applet de commande (fourni par Windows PowerShell) en tant qu’une commande en amont pour récupérer les processus Iexplore « a ».</span><span class="sxs-lookup"><span data-stu-id="c1958-156">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="c1958-157">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c1958-157">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="c1958-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1958-158">See Also</span></span>

[<span data-ttu-id="c1958-159">Ajout de paramètres qui traitent l’entrée de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="c1958-159">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="c1958-160">Création de votre première applet de commande</span><span class="sxs-lookup"><span data-stu-id="c1958-160">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="c1958-161">Extension des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="c1958-161">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="c1958-162">Comment inscrire les applets de commande, fournisseurs et héberger des Applications</span><span class="sxs-lookup"><span data-stu-id="c1958-162">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="c1958-163">Informations de référence sur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1958-163">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="c1958-164">Exemples d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c1958-164">Cmdlet Samples</span></span>](./cmdlet-samples.md)
