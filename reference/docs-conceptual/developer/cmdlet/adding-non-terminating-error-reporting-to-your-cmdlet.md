---
title: Ajout d’un rapport d’erreurs sans fin d’achèvement à votre applet de commande | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6421d510f3701c12807568ad8786459123e80223
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784586"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="371e9-102">Ajout de rapport d’erreurs sans fin d’exécution à votre applet de commande</span><span class="sxs-lookup"><span data-stu-id="371e9-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="371e9-103">Les applets de commande peuvent signaler des erreurs qui ne se terminent pas en appelant la méthode [System. Management. Automation. applet de commande. WriteError][] tout en continuant à fonctionner sur l’objet d’entrée actuel ou sur d’autres objets de pipeline entrants.</span><span class="sxs-lookup"><span data-stu-id="371e9-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="371e9-104">Cette section explique comment créer une applet de commande qui signale les erreurs qui ne se terminent pas à partir de ses méthodes de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="371e9-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="371e9-105">Pour les erreurs qui ne se terminent pas (ainsi que les erreurs de fin), l’applet de commande doit passer un objet [System. Management. Automation. ErrorRecord][] qui identifie l’erreur.</span><span class="sxs-lookup"><span data-stu-id="371e9-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span> <span data-ttu-id="371e9-106">Chaque enregistrement d’erreur est identifié par une chaîne unique appelée « identificateur d’erreur ».</span><span class="sxs-lookup"><span data-stu-id="371e9-106">Each error record is identified by a unique string called the "error identifier".</span></span> <span data-ttu-id="371e9-107">En plus de l’identificateur, la catégorie de chaque erreur est spécifiée par des constantes définies par une énumération [System. Management. Automation. ErrorCategory][] .</span><span class="sxs-lookup"><span data-stu-id="371e9-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span> <span data-ttu-id="371e9-108">L’utilisateur peut afficher les erreurs en fonction de sa catégorie en affectant à la variable la valeur `$ErrorView` « CategoryView ».</span><span class="sxs-lookup"><span data-stu-id="371e9-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="371e9-109">Pour plus d’informations sur les enregistrements d’erreurs, consultez la page [enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="371e9-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="371e9-110">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="371e9-110">Defining the Cmdlet</span></span>

<span data-ttu-id="371e9-111">La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="371e9-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="371e9-112">Cette applet de commande récupère les informations de processus, le nom du verbe choisi ici est « obtenir ».</span><span class="sxs-lookup"><span data-stu-id="371e9-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="371e9-113">(Presque tout type d’applet de commande capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="371e9-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="371e9-114">Voici la définition de cette applet de commande `Get-Proc` .</span><span class="sxs-lookup"><span data-stu-id="371e9-114">The following is the definition for this `Get-Proc` cmdlet.</span></span> <span data-ttu-id="371e9-115">Les détails de cette définition sont donnés dans [création de votre première applet](creating-a-cmdlet-without-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="371e9-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="371e9-116">Définition des paramètres</span><span class="sxs-lookup"><span data-stu-id="371e9-116">Defining Parameters</span></span>

<span data-ttu-id="371e9-117">Si nécessaire, votre applet de commande doit définir des paramètres pour le traitement de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="371e9-117">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="371e9-118">Cette applet de commande obtenir-proc définit un paramètre **Name** comme décrit dans [Ajout de paramètres qui traitent l’entrée de ligne de commande](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="371e9-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="371e9-119">Voici la déclaration de paramètre pour le paramètre **Name** de l’applet de commande « obtenir-proc ».</span><span class="sxs-lookup"><span data-stu-id="371e9-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="371e9-120">Substitution des méthodes de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="371e9-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="371e9-121">Toutes les applets de commande doivent remplacer au moins l’une des méthodes de traitement d’entrée fournies par la classe [System. Management. Automation. applet][] de commande.</span><span class="sxs-lookup"><span data-stu-id="371e9-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span> <span data-ttu-id="371e9-122">Ces méthodes sont décrites dans [création de votre première applet](creating-a-cmdlet-without-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="371e9-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="371e9-123">Votre applet de commande doit gérer chaque enregistrement de la manière la plus indépendante possible.</span><span class="sxs-lookup"><span data-stu-id="371e9-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="371e9-124">Cette applet de commande obtenir-proc remplace la méthode [System. Management. Automation. applet de commande. ProcessRecord][] pour gérer le paramètre **Name** de l’entrée fournie par l’utilisateur ou un script.</span><span class="sxs-lookup"><span data-stu-id="371e9-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span> <span data-ttu-id="371e9-125">Cette méthode obtient les processus pour chaque nom de processus demandé ou tous les processus si aucun nom n’est fourni.</span><span class="sxs-lookup"><span data-stu-id="371e9-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="371e9-126">Les détails de ce remplacement sont fournis lors de [la création de votre première applet](creating-a-cmdlet-without-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="371e9-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="371e9-127">Points à retenir lors de la création de rapports d’erreurs</span><span class="sxs-lookup"><span data-stu-id="371e9-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="371e9-128">L’objet [System. Management. Automation. ErrorRecord][] que l’applet de commande passe lors de l’écriture d’une erreur requiert une exception au niveau de son noyau.</span><span class="sxs-lookup"><span data-stu-id="371e9-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="371e9-129">Suivez les instructions .NET lors de la détermination de l’exception à utiliser.</span><span class="sxs-lookup"><span data-stu-id="371e9-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="371e9-130">Fondamentalement, si l’erreur est sémantiquement identique à une exception existante, l’applet de commande doit utiliser ou dériver de cette exception.</span><span class="sxs-lookup"><span data-stu-id="371e9-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="371e9-131">Dans le cas contraire, elle doit dériver une nouvelle exception ou une nouvelle hiérarchie d’exception directement à partir de la classe [System. exception][] .</span><span class="sxs-lookup"><span data-stu-id="371e9-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="371e9-132">Lorsque vous créez des identificateurs d’erreur (accessibles par le biais de la propriété FullyQualifiedErrorId de la classe ErrorRecord), gardez les points suivants à l’esprit.</span><span class="sxs-lookup"><span data-stu-id="371e9-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="371e9-133">Utilisez des chaînes ciblées à des fins de diagnostic afin que, lors de l’inspection de l’identificateur complet, vous puissiez déterminer l’origine de l’erreur et l’origine de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="371e9-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="371e9-134">Un identificateur d’erreur complet bien formé peut être comme suit.</span><span class="sxs-lookup"><span data-stu-id="371e9-134">A well formed fully qualified error identifier might be as follows.</span></span>

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="371e9-135">Notez que dans l’exemple précédent, l’identificateur d’erreur (le premier jeton) désigne l’erreur et la partie restante indique l’origine de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="371e9-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="371e9-136">Pour les scénarios plus complexes, l’identificateur d’erreur peut être un jeton séparé par des points qui peut être analysé lors de l’inspection.</span><span class="sxs-lookup"><span data-stu-id="371e9-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="371e9-137">Cela vous permet de créer des branches dans les parties de l’identificateur d’erreur, ainsi que l’identificateur d’erreur et la catégorie d’erreur.</span><span class="sxs-lookup"><span data-stu-id="371e9-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="371e9-138">L’applet de commande doit assigner des identificateurs d’erreur spécifiques à différents chemins de code.</span><span class="sxs-lookup"><span data-stu-id="371e9-138">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="371e9-139">Gardez à l’esprit les informations suivantes pour l’affectation des identificateurs d’erreur :</span><span class="sxs-lookup"><span data-stu-id="371e9-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="371e9-140">Un identificateur d’erreur doit rester constant tout au long du cycle de vie des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="371e9-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="371e9-141">Ne modifiez pas la sémantique d’un identificateur d’erreur entre les versions de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="371e9-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>
- <span data-ttu-id="371e9-142">Utilisez du texte pour un identificateur d’erreur que tersely correspond à l’erreur signalée.</span><span class="sxs-lookup"><span data-stu-id="371e9-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="371e9-143">N’utilisez pas d’espace blanc ou de ponctuation.</span><span class="sxs-lookup"><span data-stu-id="371e9-143">Do not use white space or punctuation.</span></span>
- <span data-ttu-id="371e9-144">Demander à votre applet de commande de générer uniquement des identificateurs d’erreur qui sont reproductibles.</span><span class="sxs-lookup"><span data-stu-id="371e9-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="371e9-145">Par exemple, il ne doit pas générer un identificateur qui comprend un identificateur de processus.</span><span class="sxs-lookup"><span data-stu-id="371e9-145">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="371e9-146">Les identificateurs d’erreur sont utiles à un utilisateur uniquement lorsqu’ils correspondent à des identificateurs qui sont visibles par d’autres utilisateurs rencontrant le même problème.</span><span class="sxs-lookup"><span data-stu-id="371e9-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="371e9-147">Les exceptions non gérées ne sont pas interceptées par PowerShell dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="371e9-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="371e9-148">Si une applet de commande crée un nouveau thread et que le code qui s’exécute dans ce thread lève une exception non gérée, PowerShell n’intercepte pas l’erreur et met fin au processus.</span><span class="sxs-lookup"><span data-stu-id="371e9-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>
- <span data-ttu-id="371e9-149">Si un objet a du code dans son destructeur ou des méthodes dispose qui provoquent une exception non gérée, PowerShell n’intercepte pas l’erreur et met fin au processus.</span><span class="sxs-lookup"><span data-stu-id="371e9-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="371e9-150">Signalement d’erreurs qui ne se terminent pas</span><span class="sxs-lookup"><span data-stu-id="371e9-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="371e9-151">L’une des méthodes de traitement d’entrée peut signaler une erreur sans fin d’exécution au flux de sortie à l’aide de la méthode [System. Management. Automation. applet de commande. WriteError][] .</span><span class="sxs-lookup"><span data-stu-id="371e9-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="371e9-152">Voici un exemple de code de cette applet de commande « obtenir-proc » qui illustre l’appel à [System. Management. Automation. cmdlet. WriteError][] à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord][] .</span><span class="sxs-lookup"><span data-stu-id="371e9-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span> <span data-ttu-id="371e9-153">Dans ce cas, l’appel est effectué si l’applet de commande ne parvient pas à trouver un processus pour un identificateur de processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="371e9-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="371e9-154">Points à retenir concernant l’écriture d’erreurs qui ne se terminent pas</span><span class="sxs-lookup"><span data-stu-id="371e9-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="371e9-155">Pour une erreur qui ne se termine pas, l’applet de commande doit générer un identificateur d’erreur spécifique pour chaque objet d’entrée spécifique.</span><span class="sxs-lookup"><span data-stu-id="371e9-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="371e9-156">Une applet de commande doit souvent modifier l’action PowerShell produite par une erreur qui ne se termine pas.</span><span class="sxs-lookup"><span data-stu-id="371e9-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="371e9-157">Pour ce faire, il peut définir `ErrorAction` les `ErrorVariable` paramètres et.</span><span class="sxs-lookup"><span data-stu-id="371e9-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="371e9-158">Si vous définissez le `ErrorAction` paramètre, l’applet de commande présente les options utilisateur [System. Management. Automation. PréférenceAction][]. vous pouvez également influencer directement l’action en définissant la `$ErrorActionPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="371e9-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="371e9-159">L’applet de commande peut enregistrer les erreurs sans fin d’utilisation dans une variable à l’aide du `ErrorVariable` paramètre, qui n’est pas affecté par le paramètre de `ErrorAction` .</span><span class="sxs-lookup"><span data-stu-id="371e9-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="371e9-160">Les échecs peuvent être ajoutés à une variable d’erreur existante en ajoutant un signe plus (+) au début du nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="371e9-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="371e9-161">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="371e9-161">Code Sample</span></span>

<span data-ttu-id="371e9-162">Pour obtenir l’exemple de code C# complet, consultez [exemple GetProcessSample04](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="371e9-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="371e9-163">Définir les types d’objets et la mise en forme</span><span class="sxs-lookup"><span data-stu-id="371e9-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="371e9-164">PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="371e9-164">PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="371e9-165">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="371e9-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="371e9-166">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions/ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="371e9-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="371e9-167">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="371e9-167">Building the Cmdlet</span></span>

<span data-ttu-id="371e9-168">Après l’implémentation d’une applet de commande, vous devez l’inscrire auprès de Windows PowerShell à l’aide d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="371e9-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="371e9-169">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="371e9-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="371e9-170">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="371e9-170">Testing the Cmdlet</span></span>

<span data-ttu-id="371e9-171">Lorsque votre applet de commande a été inscrite auprès de PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="371e9-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="371e9-172">Nous allons tester l’exemple d’applet de commande Sample-proc pour voir s’il signale une erreur :</span><span class="sxs-lookup"><span data-stu-id="371e9-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="371e9-173">Démarrez PowerShell et utilisez l’applet de commande obtenir-proc pour récupérer les processus nommés « TEST ».</span><span class="sxs-lookup"><span data-stu-id="371e9-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

  ```powershell
  get-proc -name test
  ```

  <span data-ttu-id="371e9-174">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="371e9-174">The following output appears.</span></span>

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a><span data-ttu-id="371e9-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="371e9-175">See Also</span></span>

[<span data-ttu-id="371e9-176">Ajout de paramètres qui traitent l’entrée du pipeline</span><span class="sxs-lookup"><span data-stu-id="371e9-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="371e9-177">Ajout de paramètres qui traitent l’entrée de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="371e9-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="371e9-178">Création de votre première applet de commande</span><span class="sxs-lookup"><span data-stu-id="371e9-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="371e9-179">[Extension des types d’objets et de la mise en forme](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="371e9-179">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

<span data-ttu-id="371e9-180">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="371e9-180">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="371e9-181">Référence Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="371e9-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="371e9-182">Exemples d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="371e9-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System. Management. Automation. PréférenceAction]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. applet de commande. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. applet de commande. WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. applet de commande]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
