---
title: Création d’une applet de commande qui modifie le système | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365758"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="82ef4-102">Création d’une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="82ef4-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="82ef4-103">Parfois, une applet de commande doit modifier l’état d’exécution du système, et pas seulement l’état du runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82ef4-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="82ef4-104">Dans ce cas, l’applet de commande doit permettre à l’utilisateur de confirmer si la modification doit être apportée ou non.</span><span class="sxs-lookup"><span data-stu-id="82ef4-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="82ef4-105">Pour prendre en charge la confirmation, une applet de commande doit faire deux choses.</span><span class="sxs-lookup"><span data-stu-id="82ef4-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="82ef4-106">Déclarez que l’applet de commande prend en charge la confirmation quand vous spécifiez l’attribut [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) en définissant le mot clé SupportsShouldProcess sur `true`.</span><span class="sxs-lookup"><span data-stu-id="82ef4-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="82ef4-107">Appelez [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pendant l’exécution de l’applet de commande (comme indiqué dans l’exemple suivant).</span><span class="sxs-lookup"><span data-stu-id="82ef4-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="82ef4-108">En prenant en charge la confirmation, une applet de commande expose les paramètres `Confirm` et `WhatIf` fournis par Windows PowerShell, ainsi que les instructions de développement pour les applets de commande (pour plus d’informations sur les instructions de développement des applets de commande, consultez [instructions de développement d’applets](./cmdlet-development-guidelines.md)de commande).</span><span class="sxs-lookup"><span data-stu-id="82ef4-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="82ef4-109">Modification du système</span><span class="sxs-lookup"><span data-stu-id="82ef4-109">Changing the System</span></span>

<span data-ttu-id="82ef4-110">L’acte de « modification du système » fait référence à toute applet de commande qui modifie potentiellement l’état du système en dehors de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82ef4-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="82ef4-111">Par exemple, l’arrêt d’un processus, l’activation ou la désactivation d’un compte d’utilisateur, ou l’ajout d’une ligne à une table de base de données sont toutes des modifications apportées au système qui doivent être confirmées.</span><span class="sxs-lookup"><span data-stu-id="82ef4-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="82ef4-112">En revanche, les opérations qui lisent les données ou établissent des connexions temporaires ne modifient pas le système et ne nécessitent généralement pas de confirmation.</span><span class="sxs-lookup"><span data-stu-id="82ef4-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="82ef4-113">La confirmation n’est pas non plus nécessaire pour les actions dont l’effet est limité à dans le runtime Windows PowerShell, par exemple `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="82ef4-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="82ef4-114">Les applets de commande qui peuvent ou ne peuvent pas effectuer une modification permanente doivent déclarer `SupportsShouldProcess` et appeler [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) uniquement si elles sont sur le lieu d’effectuer une modification permanente.</span><span class="sxs-lookup"><span data-stu-id="82ef4-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="82ef4-115">La confirmation ShouldProcess s’applique uniquement aux applets de commande.</span><span class="sxs-lookup"><span data-stu-id="82ef4-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="82ef4-116">Si une commande ou un script modifie l’état d’exécution d’un système en appelant directement des méthodes ou des propriétés .NET, ou en appelant des applications en dehors de Windows PowerShell, cette forme de confirmation n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="82ef4-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="82ef4-117">Applet de commande StopProc</span><span class="sxs-lookup"><span data-stu-id="82ef4-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="82ef4-118">Cette rubrique décrit une applet de commande Stop-proc qui tente d’arrêter les processus qui sont récupérés à l’aide de l’applet de commande « obtenir-proc » (décrite dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande).</span><span class="sxs-lookup"><span data-stu-id="82ef4-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="82ef4-119">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="82ef4-119">Defining the Cmdlet</span></span>

<span data-ttu-id="82ef4-120">La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82ef4-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="82ef4-121">Étant donné que vous écrivez une applet de commande pour modifier le système, elle doit être nommée en conséquence.</span><span class="sxs-lookup"><span data-stu-id="82ef4-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="82ef4-122">Cette applet de commande arrête les processus système. par conséquent, le nom du verbe choisi ici est « Stop », défini par la classe [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , avec le nom « proc » pour indiquer que l’applet de commande arrête les processus.</span><span class="sxs-lookup"><span data-stu-id="82ef4-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="82ef4-123">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="82ef4-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="82ef4-124">Voici la définition de classe pour cette applet de commande Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="82ef4-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="82ef4-125">Sachez que dans la Déclaration [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , le mot clé d’attribut `SupportsShouldProcess` est défini sur `true` pour permettre à l’applet de commande d’effectuer des appels à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="82ef4-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="82ef4-126">Si ce mot clé n’est pas défini, les paramètres `Confirm` et `WhatIf` ne seront pas accessibles à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="82ef4-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="82ef4-127">Actions extrêmement destructrices</span><span class="sxs-lookup"><span data-stu-id="82ef4-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="82ef4-128">Certaines opérations sont extrêmement destructrices, telles que le reformatage d’une partition de disque dur active.</span><span class="sxs-lookup"><span data-stu-id="82ef4-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="82ef4-129">Dans ce cas, l’applet de commande doit définir `ConfirmImpact` = `ConfirmImpact.High` lors de la déclaration de l’attribut [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="82ef4-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="82ef4-130">Ce paramètre force l’applet de commande à demander la confirmation de l’utilisateur même si l’utilisateur n’a pas spécifié le paramètre `Confirm`.</span><span class="sxs-lookup"><span data-stu-id="82ef4-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="82ef4-131">Toutefois, les développeurs d’applets de commande doivent éviter d’utiliser des `ConfirmImpact` pour les opérations qui sont simplement potentiellement destructrices, telles que la suppression d’un compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="82ef4-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="82ef4-132">N’oubliez pas que si `ConfirmImpact` a la valeur [System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span><span class="sxs-lookup"><span data-stu-id="82ef4-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span></span>

<span data-ttu-id="82ef4-133">De même, certaines opérations ont peu de chances d’être destructrices, bien qu’elles modifient en théorie l’état d’exécution d’un système en dehors de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82ef4-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="82ef4-134">Ces applets de commande peuvent définir `ConfirmImpact` sur [System. Management. Automation. ConfirmImpact. Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="82ef4-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="82ef4-135">Cela permet de contourner les demandes de confirmation lorsque l’utilisateur a demandé à confirmer uniquement les opérations à impact moyen et à impact élevé.</span><span class="sxs-lookup"><span data-stu-id="82ef4-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="82ef4-136">Définition des paramètres pour la modification du système</span><span class="sxs-lookup"><span data-stu-id="82ef4-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="82ef4-137">Cette section décrit comment définir les paramètres de l’applet de commande, y compris ceux qui sont nécessaires pour prendre en charge la modification du système.</span><span class="sxs-lookup"><span data-stu-id="82ef4-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="82ef4-138">Consultez [Ajout de paramètres qui traitent l’entrée de la ligne de](./adding-parameters-that-process-command-line-input.md) commande si vous avez besoin d’informations générales sur la définition des paramètres.</span><span class="sxs-lookup"><span data-stu-id="82ef4-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="82ef4-139">L’applet de commande Stop-proc définit trois paramètres : `Name`, `Force`et `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="82ef4-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="82ef4-140">Le paramètre `Name` correspond à la propriété `Name` de l’objet de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="82ef4-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="82ef4-141">N’oubliez pas que le paramètre `Name` dans cet exemple est obligatoire, car l’applet de commande échoue s’il n’a pas de processus nommé à arrêter.</span><span class="sxs-lookup"><span data-stu-id="82ef4-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="82ef4-142">Le paramètre `Force` permet à l’utilisateur de substituer des appels à [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)de commande. ShouldContinue.</span><span class="sxs-lookup"><span data-stu-id="82ef4-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="82ef4-143">En fait, toute applet de commande qui appelle [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) doit avoir un paramètre `Force`. ainsi, lorsque `Force` est spécifié, l’applet de commande ignore l’appel à [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) et poursuit l’opération.</span><span class="sxs-lookup"><span data-stu-id="82ef4-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="82ef4-144">N’oubliez pas que cela n’affecte pas les appels à [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)de commande. ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="82ef4-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="82ef4-145">Le paramètre `PassThru` permet à l’utilisateur d’indiquer si l’applet de commande passe un objet de sortie via le pipeline, dans ce cas, après l’arrêt d’un processus.</span><span class="sxs-lookup"><span data-stu-id="82ef4-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="82ef4-146">N’oubliez pas que ce paramètre est lié à l’applet de commande elle-même et non à une propriété de l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="82ef4-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="82ef4-147">Voici la déclaration du paramètre pour l’applet de commande Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="82ef4-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="82ef4-148">Substitution d’une méthode de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="82ef4-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="82ef4-149">L’applet de commande doit remplacer une méthode de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="82ef4-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="82ef4-150">Le code suivant illustre la substitution [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) utilisée dans l’exemple d’applet de commande Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="82ef4-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="82ef4-151">Pour chaque nom de processus demandé, cette méthode garantit que le processus n’est pas un processus spécial, tente d’arrêter le processus, puis envoie un objet de sortie si le paramètre `PassThru` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="82ef4-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="82ef4-152">Appel de la méthode ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="82ef4-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="82ef4-153">La méthode de traitement d’entrée de votre applet de commande doit appeler la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pour confirmer l’exécution d’une opération avant qu’une modification (par exemple, la suppression de fichiers) soit apportée à l’état d’exécution du système.</span><span class="sxs-lookup"><span data-stu-id="82ef4-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="82ef4-154">Cela permet au runtime Windows PowerShell de fournir les comportements « WhatIf » et « Confirm » corrects dans l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="82ef4-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="82ef4-155">Si une applet de commande indique qu’elle prend en charge doit traiter et ne parvient pas à effectuer l’appel [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , l’utilisateur peut modifier le système de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="82ef4-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="82ef4-156">L’appel à [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime Windows PowerShell en tenant compte des paramètres de ligne de commande ou des variables de préférence pour déterminer ce qui doit être affiché à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="82ef4-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="82ef4-157">L’exemple suivant montre l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) dans l’exemple d’applet de commande Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="82ef4-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="82ef4-158">Appel de la méthode ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="82ef4-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="82ef4-159">L’appel à la méthode [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) envoie un message secondaire à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="82ef4-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="82ef4-160">Cet appel est effectué après l’appel à [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) retourne `true` et si le paramètre `Force` n’a pas la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="82ef4-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="82ef4-161">L’utilisateur peut ensuite fournir des commentaires pour indiquer si l’opération doit être poursuivie.</span><span class="sxs-lookup"><span data-stu-id="82ef4-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="82ef4-162">Votre applet de commande appelle [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) en guise de vérification supplémentaire des modifications système potentiellement dangereuses ou lorsque vous souhaitez fournir des options Oui-à-tout et non-tout à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="82ef4-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="82ef4-163">L’exemple suivant illustre l’appel à [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) dans l’exemple d’applet de commande Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="82ef4-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="82ef4-164">Arrêt du traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="82ef4-164">Stopping Input Processing</span></span>

<span data-ttu-id="82ef4-165">La méthode de traitement d’entrée d’une applet de commande qui effectue des modifications du système doit permettre d’arrêter le traitement des entrées.</span><span class="sxs-lookup"><span data-stu-id="82ef4-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="82ef4-166">Dans le cas de cette applet de commande Stop-proc, un appel est effectué à partir de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) vers la méthode [System. Diagnostics. Process. Kill \*](/dotnet/api/System.Diagnostics.Process.Kill) .</span><span class="sxs-lookup"><span data-stu-id="82ef4-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="82ef4-167">Étant donné que le paramètre `PassThru` a la valeur `true`, [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) de commande appelle également [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) pour envoyer l’objet processus au pipeline.</span><span class="sxs-lookup"><span data-stu-id="82ef4-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="82ef4-168">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="82ef4-168">Code Sample</span></span>

<span data-ttu-id="82ef4-169">Pour obtenir l' C# exemple de code complet, consultez [exemple StopProcessSample01](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="82ef4-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="82ef4-170">Définition des types d’objets et de la mise en forme</span><span class="sxs-lookup"><span data-stu-id="82ef4-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="82ef4-171">Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="82ef4-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="82ef4-172">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82ef4-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="82ef4-173">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="82ef4-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="82ef4-174">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="82ef4-174">Building the Cmdlet</span></span>

<span data-ttu-id="82ef4-175">Après l’implémentation d’une applet de commande, celle-ci doit être inscrite auprès de Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82ef4-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="82ef4-176">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="82ef4-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="82ef4-177">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="82ef4-177">Testing the Cmdlet</span></span>

<span data-ttu-id="82ef4-178">Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="82ef4-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="82ef4-179">Voici plusieurs tests qui testent l’applet de commande Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="82ef4-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="82ef4-180">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="82ef4-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="82ef4-181">Démarrez Windows PowerShell et utilisez l’applet de commande Stop-proc pour arrêter le traitement, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="82ef4-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="82ef4-182">Étant donné que l’applet de commande spécifie le paramètre `Name` comme obligatoire, l’applet de commande interroge le paramètre.</span><span class="sxs-lookup"><span data-stu-id="82ef4-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="82ef4-183">La sortie suivante s'affiche.</span><span class="sxs-lookup"><span data-stu-id="82ef4-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="82ef4-184">Nous allons maintenant utiliser l’applet de commande pour arrêter le processus nommé « NOTEPAD ».</span><span class="sxs-lookup"><span data-stu-id="82ef4-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="82ef4-185">L’applet de commande vous demande de confirmer l’action.</span><span class="sxs-lookup"><span data-stu-id="82ef4-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="82ef4-186">La sortie suivante s'affiche.</span><span class="sxs-lookup"><span data-stu-id="82ef4-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="82ef4-187">Utilisez Stop-proc comme indiqué pour arrêter le processus critique nommé « WINLOGON ».</span><span class="sxs-lookup"><span data-stu-id="82ef4-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="82ef4-188">Vous êtes invité à effectuer cette action, qui entraîne le redémarrage du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="82ef4-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="82ef4-189">La sortie suivante s'affiche.</span><span class="sxs-lookup"><span data-stu-id="82ef4-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="82ef4-190">Essayons maintenant d’arrêter le processus WINLOGON sans recevoir d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="82ef4-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="82ef4-191">N’oubliez pas que cette entrée de commande utilise le paramètre `Force` pour remplacer l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="82ef4-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="82ef4-192">La sortie suivante s'affiche.</span><span class="sxs-lookup"><span data-stu-id="82ef4-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="82ef4-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82ef4-193">See Also</span></span>

[<span data-ttu-id="82ef4-194">Ajout de paramètres qui traitent l’entrée de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="82ef4-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="82ef4-195">[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="82ef4-195">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="82ef4-196">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="82ef4-196">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="82ef4-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="82ef4-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="82ef4-198">Exemples d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="82ef4-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)