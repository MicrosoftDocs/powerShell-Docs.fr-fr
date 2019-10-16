---
title: Ajout de messages utilisateur à votre applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 1e048f6ae94ac226218c18c8f8f7590a4db26226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370068"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="58793-102">Ajout de messages utilisateur à votre applet de commande</span><span class="sxs-lookup"><span data-stu-id="58793-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="58793-103">Les applets de commande peuvent écrire plusieurs types de messages qui peuvent être affichés à l’utilisateur par le runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58793-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="58793-104">Ces messages incluent les types suivants :</span><span class="sxs-lookup"><span data-stu-id="58793-104">These messages include the following types:</span></span>

- <span data-ttu-id="58793-105">Messages détaillés qui contiennent des informations générales sur l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="58793-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="58793-106">Déboguez les messages qui contiennent des informations de dépannage.</span><span class="sxs-lookup"><span data-stu-id="58793-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="58793-107">Messages d’avertissement qui contiennent une notification indiquant que l’applet de commande est sur le lieu d’effectuer une opération qui peut avoir des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="58793-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="58793-108">Les messages du rapport de progression qui contiennent des informations sur la quantité de travail effectuée par l’applet de commande lors de l’exécution d’une opération qui prend beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="58793-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="58793-109">Il n’existe aucune limite quant au nombre de messages que votre applet de commande peut écrire ou au type de messages que votre applet de commande écrit.</span><span class="sxs-lookup"><span data-stu-id="58793-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="58793-110">Chaque message est écrit en effectuant un appel spécifique dans la méthode de traitement d’entrée de votre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58793-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="58793-111">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="58793-111">Defining the Cmdlet</span></span>

<span data-ttu-id="58793-112">La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58793-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="58793-113">Tout type d’applet de commande peut écrire des notifications utilisateur à partir de ses méthodes de traitement d’entrée. ainsi, en général, vous pouvez nommer cette applet de commande à l’aide de n’importe quel verbe qui indique les modifications système effectuées par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58793-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="58793-114">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="58793-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="58793-115">L’applet de commande Stop-proc est conçue pour modifier le système. par conséquent, la Déclaration [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) pour la classe .net doit inclure le mot clé d’attribut `SupportsShouldProcess` et avoir la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="58793-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="58793-116">Le code suivant est la définition de cette classe d’applet de commande Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="58793-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="58793-117">Pour plus d’informations sur cette définition, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="58793-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="58793-118">Définition des paramètres pour la modification du système</span><span class="sxs-lookup"><span data-stu-id="58793-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="58793-119">L’applet de commande Stop-proc définit trois paramètres : `Name`, `Force` et `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="58793-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="58793-120">Pour plus d’informations sur la définition de ces paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="58793-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="58793-121">Voici la déclaration du paramètre pour l’applet de commande Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="58793-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="58793-122">Substitution d’une méthode de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="58793-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="58793-123">Votre applet de commande doit remplacer une méthode de traitement d’entrée, le plus souvent, [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)de commande. ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="58793-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="58793-124">Cette applet de commande Stop-proc remplace la méthode de traitement d’entrée [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) de commande. ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="58793-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="58793-125">Dans cette implémentation de l’applet de commande Stop-proc, des appels sont effectués pour écrire des messages détaillés, des messages de débogage et des messages d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="58793-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="58793-126">Pour plus d’informations sur la façon dont cette méthode appelle les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="58793-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="58793-127">Écriture d’un message détaillé</span><span class="sxs-lookup"><span data-stu-id="58793-127">Writing a Verbose Message</span></span>

<span data-ttu-id="58793-128">La méthode [System. Management. Automation. applet de commande. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) est utilisée pour écrire des informations générales au niveau de l’utilisateur qui ne sont pas liées à des conditions d’erreur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="58793-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="58793-129">L’administrateur système peut ensuite utiliser ces informations pour continuer à traiter d’autres commandes.</span><span class="sxs-lookup"><span data-stu-id="58793-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="58793-130">En outre, toutes les informations écrites à l’aide de cette méthode doivent être localisées en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="58793-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="58793-131">Le code suivant de cette applet de commande Stop-proc montre deux appels à la méthode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="58793-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="58793-132">Écriture d’un message de débogage</span><span class="sxs-lookup"><span data-stu-id="58793-132">Writing a Debug Message</span></span>

<span data-ttu-id="58793-133">La méthode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) est utilisée pour écrire des messages de débogage qui peuvent être utilisés pour dépanner le fonctionnement de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58793-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="58793-134">L’appel est effectué à partir d’une méthode de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="58793-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="58793-135">Windows PowerShell définit également un paramètre `Debug` qui présente des informations détaillées et de débogage.</span><span class="sxs-lookup"><span data-stu-id="58793-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="58793-136">Si votre applet de commande prend en charge ce paramètre, il n’est pas nécessaire d’appeler [System. Management. Automation. applet de commande. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) dans le même code qui appelle [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)de commande. WriteVerbose.</span><span class="sxs-lookup"><span data-stu-id="58793-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="58793-137">Les deux sections de code suivantes de l’exemple d’applet de commande Stop-proc affichent les appels à la méthode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="58793-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="58793-138">Ce message de débogage est écrit juste avant l’appel de [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de commande. ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="58793-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="58793-139">Ce message de débogage est écrit juste avant l’appel de [System. Management. Automation. applet de commande. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .</span><span class="sxs-lookup"><span data-stu-id="58793-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="58793-140">Windows PowerShell achemine automatiquement les appels [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) de commande. WriteDebug vers l’infrastructure de suivi et les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="58793-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="58793-141">Cela permet aux appels de méthode d’être suivis à l’application d’hébergement, à un fichier ou à un débogueur sans que vous ayez à effectuer d’autres tâches de développement dans l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58793-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="58793-142">L’entrée de ligne de commande suivante implémente une opération de suivi.</span><span class="sxs-lookup"><span data-stu-id="58793-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="58793-143">**PS > trace-expression Stop-proc-file proc. log-Command Stop-Process Notepad**</span><span class="sxs-lookup"><span data-stu-id="58793-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="58793-144">Écriture d’un message d’avertissement</span><span class="sxs-lookup"><span data-stu-id="58793-144">Writing a Warning Message</span></span>

<span data-ttu-id="58793-145">La méthode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) est utilisée pour écrire un avertissement lorsque l’applet de commande est sur le paragraphe d’effectuer une opération qui peut avoir un résultat inattendu, par exemple en remplaçant un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="58793-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="58793-146">Le code suivant de l’exemple d’applet de commande Stop-proc montre l’appel à la méthode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="58793-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="58793-147">Écriture d’un message de progression</span><span class="sxs-lookup"><span data-stu-id="58793-147">Writing a Progress Message</span></span>

<span data-ttu-id="58793-148">[System. Management. Automation. applet de commande. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) est utilisé pour écrire des messages de progression lorsque l’exécution des opérations d’applet de commande prend un certain temps.</span><span class="sxs-lookup"><span data-stu-id="58793-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="58793-149">Un appel à [System. Management. Automation. applet de commande. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passe un objet [System. Management. Automation. ProgressRecord](/dotnet/api/System.Management.Automation.ProgressRecord) qui est envoyé à l’application d’hébergement pour un rendu à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="58793-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="58793-150">Cette applet de commande Stop-proc n’inclut pas d’appel à la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) de commande. WriteProgress.</span><span class="sxs-lookup"><span data-stu-id="58793-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="58793-151">Le code suivant est un exemple de message de progression écrit par une applet de commande qui tente de copier un élément.</span><span class="sxs-lookup"><span data-stu-id="58793-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="58793-152">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="58793-152">Code Sample</span></span>

<span data-ttu-id="58793-153">Pour obtenir l' C# exemple de code complet, consultez [exemple StopProcessSample02](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="58793-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="58793-154">Définir les types d’objets et la mise en forme</span><span class="sxs-lookup"><span data-stu-id="58793-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="58793-155">Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="58793-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="58793-156">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="58793-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="58793-157">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="58793-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="58793-158">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="58793-158">Building the Cmdlet</span></span>

<span data-ttu-id="58793-159">Après l’implémentation d’une applet de commande, celle-ci doit être inscrite auprès de Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58793-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="58793-160">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="58793-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="58793-161">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="58793-161">Testing the Cmdlet</span></span>

<span data-ttu-id="58793-162">Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="58793-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="58793-163">Nous allons tester l’exemple d’applet de commande Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="58793-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="58793-164">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="58793-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="58793-165">L’entrée de ligne de commande suivante utilise Stop-proc pour arrêter le processus nommé « NOTEPAD », fournir des notifications détaillées et imprimer les informations de débogage.</span><span class="sxs-lookup"><span data-stu-id="58793-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="58793-166">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="58793-166">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="58793-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58793-167">See Also</span></span>

[<span data-ttu-id="58793-168">Créer une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="58793-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="58793-169">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="58793-169">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="58793-170">[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="58793-170">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="58793-171">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="58793-171">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="58793-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="58793-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
