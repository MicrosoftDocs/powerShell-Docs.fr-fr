---
title: Ajout de Messages de l’utilisateur à votre applet de commande | Microsoft Docs
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
ms.openlocfilehash: 5b3a5f5d5d02c7d5a3c1d622ec1a3740739c694f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068774"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="b0762-102">Ajout de messages utilisateur à votre applet de commande</span><span class="sxs-lookup"><span data-stu-id="b0762-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="b0762-103">Applets de commande peut écrire plusieurs types de messages qui peuvent être affichées à l’utilisateur par le runtime de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0762-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="b0762-104">Ces messages incluent les types suivants :</span><span class="sxs-lookup"><span data-stu-id="b0762-104">These messages include the following types:</span></span>

- <span data-ttu-id="b0762-105">Messages détaillés qui contiennent des informations utilisateur générales.</span><span class="sxs-lookup"><span data-stu-id="b0762-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="b0762-106">Les messages qui contiennent des informations de résolution des problèmes de débogage.</span><span class="sxs-lookup"><span data-stu-id="b0762-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="b0762-107">Messages d’avertissement qui contiennent une notification indiquant que l’applet de commande est sur le point d’effectuer une opération qui peut avoir des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="b0762-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="b0762-108">Rapport de progression des messages qui contiennent des informations sur la quantité utiliser l’applet de commande est terminée lorsque vous effectuez une opération qui prend beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="b0762-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="b0762-109">Il n’existe aucune limite au nombre de messages que votre applet de commande peut écrire ou le type de message qui écrit votre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0762-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="b0762-110">Chaque message est écrit en effectuant un appel spécifique à partir de dans l’entrée de la méthode de votre applet de commande de traitement.</span><span class="sxs-lookup"><span data-stu-id="b0762-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="b0762-111">L’applet de commande StopProc</span><span class="sxs-lookup"><span data-stu-id="b0762-111">The StopProc Cmdlet</span></span>

<span data-ttu-id="b0762-112">Rubriques de cette section sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b0762-112">Topics in this section include the following:</span></span>

- [<span data-ttu-id="b0762-113">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b0762-113">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="b0762-114">Définition des paramètres pour la Modification du système</span><span class="sxs-lookup"><span data-stu-id="b0762-114">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="b0762-115">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="b0762-115">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="b0762-116">Écriture d’un Message détaillé</span><span class="sxs-lookup"><span data-stu-id="b0762-116">Writing a Verbose Message</span></span>](#Writing-a-Verbose-Message)

- [<span data-ttu-id="b0762-117">Écriture d’un Message de débogage</span><span class="sxs-lookup"><span data-stu-id="b0762-117">Writing a Debug Message</span></span>](#Writing-a-Debug-Message)

- [<span data-ttu-id="b0762-118">Écriture d’un Message d’avertissement</span><span class="sxs-lookup"><span data-stu-id="b0762-118">Writing a Warning Message</span></span>](#Writing-a-Warning-Message)

- [<span data-ttu-id="b0762-119">Écriture d’un Message de progression</span><span class="sxs-lookup"><span data-stu-id="b0762-119">Writing a Progress Message</span></span>](#Writing-a-Progress-Message)

- [<span data-ttu-id="b0762-120">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="b0762-120">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="b0762-121">Définir les Types d’objets et la mise en forme</span><span class="sxs-lookup"><span data-stu-id="b0762-121">Define Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="b0762-122">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b0762-122">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="b0762-123">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b0762-123">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="b0762-124">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b0762-124">Defining the Cmdlet</span></span>

<span data-ttu-id="b0762-125">La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0762-125">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="b0762-126">Toute sorte de l’applet de commande peut écrire des notifications à l’utilisateur à partir de son entrée méthodes ; de traitement Par conséquent, en règle générale, vous pouvez nommer cette applet de commande à l’aide de n’importe quel verbe qui indique les modifications du système de l’applet de commande effectue.</span><span class="sxs-lookup"><span data-stu-id="b0762-126">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="b0762-127">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="b0762-127">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b0762-128">L’applet de commande Stop-Process est conçu pour modifier le système ; Par conséquent, le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) déclaration pour la classe .NET doit inclure le `SupportsShouldProcess` mot clé d’attribut et la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="b0762-128">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="b0762-129">Le code suivant est la définition de cette classe d’applet de commande Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="b0762-129">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="b0762-130">Pour plus d’informations sur cette définition, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="b0762-130">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="b0762-131">Définition des paramètres pour la Modification du système</span><span class="sxs-lookup"><span data-stu-id="b0762-131">Defining Parameters for System Modification</span></span>

<span data-ttu-id="b0762-132">L’applet de commande Stop-Process définit trois paramètres : `Name`, `Force`, et `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="b0762-132">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="b0762-133">Pour plus d’informations sur la définition de ces paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="b0762-133">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="b0762-134">Voici la déclaration de paramètre pour l’applet de commande Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="b0762-134">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b0762-135">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="b0762-135">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b0762-136">Votre applet de commande doit substituer une méthode de traitement des entrées, il sera plus souvent [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="b0762-136">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="b0762-137">Cette applet de commande Stop-Process remplace le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b0762-137">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="b0762-138">Dans cette implémentation de l’applet de commande Stop-Process, les appels sont effectués pour écrire les messages documentés, les messages de débogage et les messages d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="b0762-138">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="b0762-139">Pour plus d’informations sur la façon dont cette méthode appelle la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes, consultez [Création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="b0762-139">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="b0762-140">Écriture d’un Message détaillé</span><span class="sxs-lookup"><span data-stu-id="b0762-140">Writing a Verbose Message</span></span>

<span data-ttu-id="b0762-141">Le [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) méthode est utilisée pour écrire des informations générales au niveau de l’utilisateur qui ne sont pas liées aux conditions d’erreur spécifique.</span><span class="sxs-lookup"><span data-stu-id="b0762-141">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="b0762-142">L’administrateur système peut ensuite utiliser ces informations pour continuer à traiter d’autres commandes.</span><span class="sxs-lookup"><span data-stu-id="b0762-142">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="b0762-143">En outre, toute information enregistrée à l’aide de cette méthode doit être localisée en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="b0762-143">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="b0762-144">Le code suivant à partir de cette applet de commande Stop-Process présente deux appels à la [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) méthode à partir de la substitution de la [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).</span><span class="sxs-lookup"><span data-stu-id="b0762-144">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="b0762-145">Écriture d’un Message de débogage</span><span class="sxs-lookup"><span data-stu-id="b0762-145">Writing a Debug Message</span></span>

<span data-ttu-id="b0762-146">Le [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) méthode est utilisée pour écrire des messages de débogage qui peuvent être utilisées pour résoudre les problèmes de l’opération de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0762-146">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="b0762-147">L’appel est effectué à partir d’une méthode de traitement des entrées.</span><span class="sxs-lookup"><span data-stu-id="b0762-147">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="b0762-148">Windows PowerShell définit également un `Debug` paramètre qui présente à la fois détaillé et les informations de débogage.</span><span class="sxs-lookup"><span data-stu-id="b0762-148">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="b0762-149">Si votre applet de commande prend en charge ce paramètre, il n’a pas besoin d’appeler [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) dans le même code qui appelle [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="b0762-149">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="b0762-150">Les deux sections de code à partir de l’applet de commande Stop-Process exemple suivantes montrent des appels à la [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) méthode à partir de la substitution de la [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).</span><span class="sxs-lookup"><span data-stu-id="b0762-150">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="b0762-151">Ce message de débogage est écrite immédiatement avant [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) est appelée.</span><span class="sxs-lookup"><span data-stu-id="b0762-151">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="b0762-152">Ce message de débogage est écrite immédiatement avant [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) est appelée.</span><span class="sxs-lookup"><span data-stu-id="b0762-152">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="b0762-153">Windows PowerShell achemine automatiquement les [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) appels à l’infrastructure de suivi et les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="b0762-153">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="b0762-154">Ainsi, les appels de méthode à suivre pour l’application d’hébergement, un fichier ou un débogueur sans devoir effectuer tout travail de développement supplémentaire au sein de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0762-154">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="b0762-155">L’entrée de ligne de commande suivante implémente une opération de suivi.</span><span class="sxs-lookup"><span data-stu-id="b0762-155">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="b0762-156">**PS > expression de trace stop-Process-fichier proc.log-le bloc-notes de commande stop-Process**</span><span class="sxs-lookup"><span data-stu-id="b0762-156">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="b0762-157">Écriture d’un Message d’avertissement</span><span class="sxs-lookup"><span data-stu-id="b0762-157">Writing a Warning Message</span></span>

<span data-ttu-id="b0762-158">Le [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) méthode est utilisée pour écrire un avertissement lorsque l’applet de commande est sur le point d’effectuer une opération qui peut avoir un résultat d’inattendu, par exemple, en remplaçant un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="b0762-158">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="b0762-159">Le code suivant à partir de l’applet de commande Stop-Process exemple illustre l’appel à la [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) méthode à partir de la substitution de la [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).</span><span class="sxs-lookup"><span data-stu-id="b0762-159">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="b0762-160">Écriture d’un Message de progression</span><span class="sxs-lookup"><span data-stu-id="b0762-160">Writing a Progress Message</span></span>

<span data-ttu-id="b0762-161">Le [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) est utilisé pour écrire des messages de progression lorsque les opérations de l’applet de commande prennent un certain temps.</span><span class="sxs-lookup"><span data-stu-id="b0762-161">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="b0762-162">Un appel à [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) transmet un [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) objet qui est envoyé à l’application d’hébergement pour le rendu à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b0762-162">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="b0762-163">Cette applet de commande Stop-Process n’inclut pas d’un appel à la [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) (méthode).</span><span class="sxs-lookup"><span data-stu-id="b0762-163">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="b0762-164">Le code suivant est un exemple d’un message de progression écrit par une applet de commande qui tente de copier un élément.</span><span class="sxs-lookup"><span data-stu-id="b0762-164">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="b0762-165">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="b0762-165">Code Sample</span></span>

<span data-ttu-id="b0762-166">Pour l’ensemble C# exemple de code, consultez [StopProcessSample02 exemple](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b0762-166">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="b0762-167">Définir les Types d’objets et la mise en forme</span><span class="sxs-lookup"><span data-stu-id="b0762-167">Define Object Types and Formatting</span></span>

<span data-ttu-id="b0762-168">Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="b0762-168">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="b0762-169">Par conséquent, une applet de commande devez définir son propre type, ou l’applet de commande peut étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0762-169">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b0762-170">Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="b0762-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b0762-171">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b0762-171">Building the Cmdlet</span></span>

<span data-ttu-id="b0762-172">Après l’implémentation d’une applet de commande, il doit être enregistré avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0762-172">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b0762-173">Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="b0762-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b0762-174">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="b0762-174">Testing the Cmdlet</span></span>

<span data-ttu-id="b0762-175">Lorsque votre applet de commande a été inscrite avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b0762-175">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="b0762-176">Testons l’applet de commande Stop-Process exemple.</span><span class="sxs-lookup"><span data-stu-id="b0762-176">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="b0762-177">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b0762-177">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="b0762-178">L’entrée de ligne de commande suivante utilise Stop-Process pour arrêter le processus nommé « NOTEPAD », fournissent des notifications détaillées et imprimer les informations de débogage.</span><span class="sxs-lookup"><span data-stu-id="b0762-178">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="b0762-179">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b0762-179">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b0762-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0762-180">See Also</span></span>

[<span data-ttu-id="b0762-181">Créer une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="b0762-181">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="b0762-182">Comment créer une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0762-182">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="b0762-183">Extension des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="b0762-183">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="b0762-184">Comment inscrire les applets de commande, fournisseurs et héberger des Applications</span><span class="sxs-lookup"><span data-stu-id="b0762-184">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="b0762-185">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b0762-185">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
