---
title: Ajout de rapport d’erreurs à votre applet de commande sans terminaison | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 2f3bb481722363557c93ebbc5e6df62baeff2555
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862005"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="53026-102">Ajout de rapport d’erreurs sans fin d’exécution à votre applet de commande</span><span class="sxs-lookup"><span data-stu-id="53026-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="53026-103">Applets de commande peut signaler des erreurs sans fin d’exécution en appelant le [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (méthode) et continuer à opérer sur l’objet d’entrée actuel ou sur entrant autre pipeline d’objets.</span><span class="sxs-lookup"><span data-stu-id="53026-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="53026-104">Cette section explique comment créer une applet de commande qui signale les erreurs sans fin d’exécution à partir de ses méthodes de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="53026-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="53026-105">Pour les erreurs sans fin d’exécution (ainsi que des erreurs avec fin d’exécution), l’applet de commande doit passer un [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet identifiant l’erreur.</span><span class="sxs-lookup"><span data-stu-id="53026-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object identifying the error.</span></span> <span data-ttu-id="53026-106">Chaque enregistrement d’erreur est identifiée par une chaîne unique appelée le « identificateur d’erreur ».</span><span class="sxs-lookup"><span data-stu-id="53026-106">Each error record is identified by a unique string called the "error identifier."</span></span> <span data-ttu-id="53026-107">En plus de l’identificateur de la catégorie de chaque erreur est spécifiée par les constantes définies par un [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) énumération.</span><span class="sxs-lookup"><span data-stu-id="53026-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="53026-108">L’utilisateur peut afficher les erreurs en fonction de leur catégorie en définissant le `$ErrorView` variable « CategoryView ».</span><span class="sxs-lookup"><span data-stu-id="53026-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="53026-109">Pour plus d’informations sur les enregistrements d’erreur, consultez [enregistrements d’erreur Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="53026-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="53026-110">Rubriques de cette section sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="53026-110">Topics in this section include the following:</span></span>

- [<span data-ttu-id="53026-111">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="53026-111">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="53026-112">Définition des paramètres</span><span class="sxs-lookup"><span data-stu-id="53026-112">Defining Parameters</span></span>](#Defining-Parameters)

- [<span data-ttu-id="53026-113">Substitution de méthodes de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="53026-113">Overriding Input Processing Methods</span></span>](#Overriding-Input-Processing-Methods)

- [<span data-ttu-id="53026-114">Rapports d’erreurs sans fin d’exécution</span><span class="sxs-lookup"><span data-stu-id="53026-114">Reporting Nonterminating Errors</span></span>](#Reporting-Nonterminating-Errors)

- [<span data-ttu-id="53026-115">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="53026-115">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="53026-116">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="53026-116">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="53026-117">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="53026-117">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="53026-118">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="53026-118">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="53026-119">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="53026-119">Defining the Cmdlet</span></span>

<span data-ttu-id="53026-120">La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="53026-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="53026-121">Cette applet de commande récupère des informations de processus, par conséquent, le nom du verbe choisi ici est « Get ».</span><span class="sxs-lookup"><span data-stu-id="53026-121">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="53026-122">(Presque toute sorte de l’applet de commande qui est capable de récupérer des informations peut traiter l’entrée de ligne de commande.) Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="53026-122">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="53026-123">Voici la définition de cette applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="53026-123">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="53026-124">Informations de cette définition sont fournies dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="53026-124">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="53026-125">Définition des paramètres</span><span class="sxs-lookup"><span data-stu-id="53026-125">Defining Parameters</span></span>

<span data-ttu-id="53026-126">Si nécessaire, votre applet de commande doit définir les paramètres de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="53026-126">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="53026-127">Cette applet de commande Get-Process définit un `Name` paramètre comme décrit dans [Ajout de paramètres qui traitent les entrées de ligne de commande](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="53026-127">This Get-Proc cmdlet defines a `Name` parameter as described in [Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="53026-128">Voici la déclaration de paramètre pour le `Name` paramètre de cette applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="53026-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet.</span></span>

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="53026-129">Substitution de méthodes de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="53026-129">Overriding Input Processing Methods</span></span>

<span data-ttu-id="53026-130">Toutes les applets de commande doivent substituer au moins un de l’entrée de traitement des méthodes fournies par le [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="53026-130">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="53026-131">Ces méthodes sont décrites dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="53026-131">These methods are discussed in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="53026-132">Votre applet de commande doit gérer chaque enregistrement de manière indépendante que possible.</span><span class="sxs-lookup"><span data-stu-id="53026-132">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="53026-133">Se substitue à cette applet de commande Get-Process le [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode pour gérer la `Name` paramètre pour l’entrée fournie par l’utilisateur ou un script.</span><span class="sxs-lookup"><span data-stu-id="53026-133">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter for input provided by the user or a script.</span></span> <span data-ttu-id="53026-134">Cette méthode obtient les processus pour chaque nom de processus demandé ou tous les processus si aucun nom n’est fourni.</span><span class="sxs-lookup"><span data-stu-id="53026-134">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="53026-135">Détails de ce remplacement sont fournis dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="53026-135">Details of this override are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

#### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="53026-136">Points à retenir lors du signalement des erreurs</span><span class="sxs-lookup"><span data-stu-id="53026-136">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="53026-137">Le [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) que l’applet de commande passe lors de l’écriture d’une erreur nécessite une exception à la base de l’objet.</span><span class="sxs-lookup"><span data-stu-id="53026-137">The [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="53026-138">Suivez les instructions de .NET lors de la détermination de l’exception à utiliser.</span><span class="sxs-lookup"><span data-stu-id="53026-138">Follow the .NET guidelines when determining the exception to use.</span></span> <span data-ttu-id="53026-139">En fait, si l’erreur est sémantiquement identique à une exception existante, l’applet de commande doit utiliser ou dériver de cette exception.</span><span class="sxs-lookup"><span data-stu-id="53026-139">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="53026-140">Sinon, elle doit dériver une nouvelle exception ou la hiérarchie des exceptions directement à partir de la [System.Exception](/dotnet/api/System.Exception) classe.</span><span class="sxs-lookup"><span data-stu-id="53026-140">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception](/dotnet/api/System.Exception) class.</span></span>

<span data-ttu-id="53026-141">Gardez l’esprit ce qui suit lors de la création d’identificateurs d’erreur (accédés via la propriété FullyQualifiedErrorId de la classe ErrorRecord).</span><span class="sxs-lookup"><span data-stu-id="53026-141">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="53026-142">Chaînes d’utilisation qui sont ciblés pour faciliter le diagnostic afin que lors de l’inspection de l’identificateur complet, vous pouvez déterminer l’erreur qui est et où l’erreur provient.</span><span class="sxs-lookup"><span data-stu-id="53026-142">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="53026-143">Un identificateur d’erreur complet correct peut être comme suit.</span><span class="sxs-lookup"><span data-stu-id="53026-143">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

<span data-ttu-id="53026-144">Notez que dans l’exemple précédent, l’identificateur de l’erreur (le premier jeton) désigne l’erreur et la partie restante indique d'où provenance l’erreur.</span><span class="sxs-lookup"><span data-stu-id="53026-144">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="53026-145">Pour des scénarios plus complexes, l’identificateur de l’erreur peut être un jeton de point séparé qui peut être analysé à l’inspection.</span><span class="sxs-lookup"><span data-stu-id="53026-145">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="53026-146">Cela permet de que vous créer trop de branche sur les parties de l’identificateur de l’erreur, ainsi que la catégorie d’erreur identificateur et d’erreur.</span><span class="sxs-lookup"><span data-stu-id="53026-146">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="53026-147">L’applet de commande doit affecter des identificateurs de l’erreur spécifique aux chemins de code différents.</span><span class="sxs-lookup"><span data-stu-id="53026-147">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="53026-148">Gardez les informations suivantes à l’esprit pour l’affectation des identificateurs d’erreur :</span><span class="sxs-lookup"><span data-stu-id="53026-148">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="53026-149">Un identificateur de l’erreur doit rester constant tout au long du cycle de vie d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="53026-149">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="53026-150">Ne modifiez pas la sémantique d’un identificateur de l’erreur entre les versions de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="53026-150">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="53026-151">Utilisez le texte d’un identificateur d’erreur tersely correspond à l’erreur signalée.</span><span class="sxs-lookup"><span data-stu-id="53026-151">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="53026-152">N’utilisez pas les espaces blancs ou des signes de ponctuation.</span><span class="sxs-lookup"><span data-stu-id="53026-152">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="53026-153">Avoir votre applet de commande Générer uniquement des identificateurs d’erreur qui sont reproductibles.</span><span class="sxs-lookup"><span data-stu-id="53026-153">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="53026-154">Par exemple, il ne doit pas générer un identificateur qui inclut un identificateur de processus.</span><span class="sxs-lookup"><span data-stu-id="53026-154">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="53026-155">Identificateurs d’erreur sont utiles à un utilisateur uniquement lorsqu’ils correspondent aux identificateurs sont visibles par d’autres utilisateurs rencontrent le même problème.</span><span class="sxs-lookup"><span data-stu-id="53026-155">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="53026-156">Exceptions non gérées ne sont pas interceptées par Windows PowerShell dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="53026-156">Unhandled exceptions are not caught by Windows PowerShell in the following conditions:</span></span>

- <span data-ttu-id="53026-157">Si une applet de commande crée un nouveau thread et du code en cours d’exécution dans ce thread lève une exception non gérée, Windows PowerShell n’intercepte pas l’erreur et le processus prendra fin.</span><span class="sxs-lookup"><span data-stu-id="53026-157">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="53026-158">Si un objet possède un code qui lève une exception non gérée dans son destructeur ou les méthodes Dispose, Windows PowerShell n’intercepte pas l’erreur et le processus prendra fin.</span><span class="sxs-lookup"><span data-stu-id="53026-158">If an object has code in its destructor or Dispose methods that causes an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="53026-159">Rapports d’erreurs sans fin d’exécution</span><span class="sxs-lookup"><span data-stu-id="53026-159">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="53026-160">L’un des méthodes de traitement d’entrée peut signaler une erreur sans fin d’exécution pour le flux de sortie à l’aide de la [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (méthode).</span><span class="sxs-lookup"><span data-stu-id="53026-160">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="53026-161">Voici un exemple de code à partir de cette applet de commande Get-Process qui illustre l’appel de [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) à partir de dans la substitution de la [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).</span><span class="sxs-lookup"><span data-stu-id="53026-161">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from within the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="53026-162">Dans ce cas, l’appel est effectué si l’applet de commande ne peut pas trouver un processus pour un identificateur de processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="53026-162">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

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

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="53026-163">Points à retenir sur l’écriture des erreurs sans fin d’exécution</span><span class="sxs-lookup"><span data-stu-id="53026-163">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="53026-164">Pour une erreur sans fin d’exécution, l’applet de commande doit générer un identificateur de l’erreur spécifique pour chaque objet d’entrée spécifique.</span><span class="sxs-lookup"><span data-stu-id="53026-164">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="53026-165">Une applet de commande doit fréquemment modifier l’action de Windows PowerShell produite par une erreur sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="53026-165">A cmdlet frequently needs to modify the Windows PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="53026-166">Il peut le faire en définissant le `ErrorAction` et `ErrorVariable` paramètres.</span><span class="sxs-lookup"><span data-stu-id="53026-166">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="53026-167">Si la définition de la `ErrorAction` paramètre, l’applet de commande présente les options utilisateur [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), vous pouvez également directement influencer l’action en définissant le `$ErrorActionPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="53026-167">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="53026-168">L’applet de commande peut enregistrer des erreurs sans fin d’exécution dans une variable à l’aide du `ErrorVariable` paramètre, qui n’est pas affectée par la valeur de `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="53026-168">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="53026-169">Échecs peuvent être ajoutés à une variable d’erreur existant en ajoutant un signe plus (+) devant le nom de variable.</span><span class="sxs-lookup"><span data-stu-id="53026-169">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="53026-170">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="53026-170">Code Sample</span></span>

<span data-ttu-id="53026-171">Pour l’ensemble C# exemple de code, consultez [GetProcessSample04 exemple](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="53026-171">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="53026-172">Définir les Types d’objets et la mise en forme</span><span class="sxs-lookup"><span data-stu-id="53026-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="53026-173">Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="53026-173">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="53026-174">Par conséquent, une applet de commande devez définir son propre type, ou l’applet de commande peut étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="53026-174">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="53026-175">Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="53026-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="53026-176">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="53026-176">Building the Cmdlet</span></span>

<span data-ttu-id="53026-177">Après l’implémentation d’une applet de commande, vous devez l’inscrire avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53026-177">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="53026-178">Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="53026-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="53026-179">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="53026-179">Testing the Cmdlet</span></span>

<span data-ttu-id="53026-180">Lorsque votre applet de commande a été inscrite avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="53026-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="53026-181">Testons l’applet de commande Get-Process exemple pour voir si elle signale une erreur :</span><span class="sxs-lookup"><span data-stu-id="53026-181">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="53026-182">Démarrez Windows PowerShell et utilisez l’applet de commande Get-Process pour récupérer les processus nommés « TEST ».</span><span class="sxs-lookup"><span data-stu-id="53026-182">Start Windows PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="53026-183">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="53026-183">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="53026-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53026-184">See Also</span></span>

[<span data-ttu-id="53026-185">Ajout de paramètres d’entrée de Pipeline de processus</span><span class="sxs-lookup"><span data-stu-id="53026-185">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="53026-186">Ajout de paramètres qui traitent l’entrée de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="53026-186">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="53026-187">Création de votre première applet de commande</span><span class="sxs-lookup"><span data-stu-id="53026-187">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="53026-188">Extension des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="53026-188">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="53026-189">Comment inscrire les applets de commande, fournisseurs et héberger des Applications</span><span class="sxs-lookup"><span data-stu-id="53026-189">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="53026-190">Informations de référence sur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="53026-190">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="53026-191">Exemples d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="53026-191">Cmdlet Samples</span></span>](./cmdlet-samples.md)
