---
ms.date: 09/13/2016
ms.topic: reference
title: Création d’une applet de commande qui modifie le système
description: Création d’une applet de commande qui modifie le système
ms.openlocfilehash: 757f2c97bb4b5dcf2fb633cd35fe52bc5f6c5cf9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355542"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="db21f-103">Création d’une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="db21f-103">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="db21f-104">Parfois, une applet de commande doit modifier l’état d’exécution du système, et pas seulement l’état du runtime Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db21f-104">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="db21f-105">Dans ce cas, l’applet de commande doit permettre à l’utilisateur de confirmer si la modification doit être apportée ou non.</span><span class="sxs-lookup"><span data-stu-id="db21f-105">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="db21f-106">Pour prendre en charge la confirmation, une applet de commande doit faire deux choses.</span><span class="sxs-lookup"><span data-stu-id="db21f-106">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="db21f-107">Déclarez que l’applet de commande prend en charge la confirmation quand vous spécifiez l’attribut [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) en définissant le mot clé SupportsShouldProcess sur `true` .</span><span class="sxs-lookup"><span data-stu-id="db21f-107">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="db21f-108">Appelez [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pendant l’exécution de l’applet de commande (comme indiqué dans l’exemple suivant).</span><span class="sxs-lookup"><span data-stu-id="db21f-108">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="db21f-109">En prenant en charge la confirmation, une applet de commande expose les `Confirm` `WhatIf` paramètres et fournis par Windows PowerShell, ainsi que les instructions de développement des applets de commande (pour plus d’informations sur les instructions de développement des applets de commande, consultez [instructions de développement d’applets](./cmdlet-development-guidelines.md)de commande).</span><span class="sxs-lookup"><span data-stu-id="db21f-109">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="db21f-110">Modification du système</span><span class="sxs-lookup"><span data-stu-id="db21f-110">Changing the System</span></span>

<span data-ttu-id="db21f-111">L’acte de « modification du système » fait référence à toute applet de commande qui modifie potentiellement l’état du système en dehors de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db21f-111">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="db21f-112">Par exemple, l’arrêt d’un processus, l’activation ou la désactivation d’un compte d’utilisateur, ou l’ajout d’une ligne à une table de base de données sont toutes des modifications apportées au système qui doivent être confirmées.</span><span class="sxs-lookup"><span data-stu-id="db21f-112">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span>
<span data-ttu-id="db21f-113">En revanche, les opérations qui lisent les données ou établissent des connexions temporaires ne modifient pas le système et ne nécessitent généralement pas de confirmation.</span><span class="sxs-lookup"><span data-stu-id="db21f-113">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="db21f-114">La confirmation n’est pas non plus nécessaire pour les actions dont l’effet est limité à dans le runtime Windows PowerShell, tel que `set-variable` .</span><span class="sxs-lookup"><span data-stu-id="db21f-114">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="db21f-115">Les applets de commande qui peuvent ou ne peuvent pas effectuer de modification permanente doivent déclarer `SupportsShouldProcess` et appeler [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) uniquement si elles sont sur le lieu d’effectuer une modification permanente.</span><span class="sxs-lookup"><span data-stu-id="db21f-115">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="db21f-116">La confirmation ShouldProcess s’applique uniquement aux applets de commande.</span><span class="sxs-lookup"><span data-stu-id="db21f-116">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="db21f-117">Si une commande ou un script modifie l’état d’exécution d’un système en appelant directement des méthodes ou des propriétés .NET, ou en appelant des applications en dehors de Windows PowerShell, cette forme de confirmation n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="db21f-117">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="db21f-118">Applet de commande StopProc</span><span class="sxs-lookup"><span data-stu-id="db21f-118">The StopProc Cmdlet</span></span>

<span data-ttu-id="db21f-119">Cette rubrique décrit une applet de commande Stop-Proc qui tente d’arrêter des processus qui sont récupérés à l’aide de l’applet de commande Get-Proc (décrite dans [création de votre première applet](./creating-a-cmdlet-without-parameters.md)de commande).</span><span class="sxs-lookup"><span data-stu-id="db21f-119">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="db21f-120">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="db21f-120">Defining the Cmdlet</span></span>

<span data-ttu-id="db21f-121">La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db21f-121">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="db21f-122">Étant donné que vous écrivez une applet de commande pour modifier le système, elle doit être nommée en conséquence.</span><span class="sxs-lookup"><span data-stu-id="db21f-122">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="db21f-123">Cette applet de commande arrête les processus système. par conséquent, le nom du verbe choisi ici est « Stop », défini par la classe [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , avec le nom « proc » pour indiquer que l’applet de commande arrête les processus.</span><span class="sxs-lookup"><span data-stu-id="db21f-123">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="db21f-124">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="db21f-124">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="db21f-125">Voici la définition de classe pour cette applet de commande Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="db21f-125">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="db21f-126">Sachez que dans la Déclaration [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , le `SupportsShouldProcess` mot clé d’attribut a la valeur `true` pour permettre à l’applet de commande d’effectuer des appels à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="db21f-126">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>
<span data-ttu-id="db21f-127">Si ce mot clé n’est pas défini, les `Confirm` `WhatIf` paramètres et ne sont pas disponibles pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="db21f-127">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="db21f-128">Actions extrêmement destructrices</span><span class="sxs-lookup"><span data-stu-id="db21f-128">Extremely Destructive Actions</span></span>

<span data-ttu-id="db21f-129">Certaines opérations sont extrêmement destructrices, telles que le reformatage d’une partition de disque dur active.</span><span class="sxs-lookup"><span data-stu-id="db21f-129">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="db21f-130">Dans ce cas, l’applet de commande doit être définie `ConfirmImpact`  =  `ConfirmImpact.High` lors de la déclaration de l’attribut [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="db21f-130">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="db21f-131">Ce paramètre force l’applet de commande à demander la confirmation de l’utilisateur même si l’utilisateur n’a pas spécifié le `Confirm` paramètre.</span><span class="sxs-lookup"><span data-stu-id="db21f-131">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="db21f-132">Toutefois, les développeurs d’applets de commande doivent éviter de les utiliser `ConfirmImpact` pour les opérations qui sont simplement potentiellement destructrices, telles que la suppression d’un compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="db21f-132">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="db21f-133">N’oubliez pas que si `ConfirmImpact` a la valeur [System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) 
 **High**.</span><span class="sxs-lookup"><span data-stu-id="db21f-133">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact)
**High**.</span></span>

<span data-ttu-id="db21f-134">De même, certaines opérations ont peu de chances d’être destructrices, bien qu’elles modifient en théorie l’état d’exécution d’un système en dehors de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db21f-134">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="db21f-135">Ces applets de commande peuvent `ConfirmImpact` être définies sur [System. Management. Automation. ConfirmImpact. Low](/dotnet/api/system.management.automation.confirmimpact).</span><span class="sxs-lookup"><span data-stu-id="db21f-135">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact).</span></span>
<span data-ttu-id="db21f-136">Cela permet de contourner les demandes de confirmation lorsque l’utilisateur a demandé à confirmer uniquement les opérations à impact moyen et à impact élevé.</span><span class="sxs-lookup"><span data-stu-id="db21f-136">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="db21f-137">Définition des paramètres pour la modification du système</span><span class="sxs-lookup"><span data-stu-id="db21f-137">Defining Parameters for System Modification</span></span>

<span data-ttu-id="db21f-138">Cette section décrit comment définir les paramètres de l’applet de commande, y compris ceux qui sont nécessaires pour prendre en charge la modification du système.</span><span class="sxs-lookup"><span data-stu-id="db21f-138">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="db21f-139">Consultez [Ajout de paramètres qui traitent l’entrée de la ligne de](./adding-parameters-that-process-command-line-input.md) commande si vous avez besoin d’informations générales sur la définition des paramètres.</span><span class="sxs-lookup"><span data-stu-id="db21f-139">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="db21f-140">L’applet de commande Stop-Proc définit trois paramètres : `Name` , `Force` et `PassThru` .</span><span class="sxs-lookup"><span data-stu-id="db21f-140">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="db21f-141">Le `Name` paramètre correspond à la `Name` propriété de l’objet de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="db21f-141">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="db21f-142">Sachez que le `Name` paramètre de cet exemple est obligatoire, car l’applet de commande échouera s’il n’a pas de processus nommé à arrêter.</span><span class="sxs-lookup"><span data-stu-id="db21f-142">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="db21f-143">Le `Force` paramètre permet à l’utilisateur de substituer des appels à [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)de commande. ShouldContinue.</span><span class="sxs-lookup"><span data-stu-id="db21f-143">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>
<span data-ttu-id="db21f-144">En fait, toute applet de commande qui appelle [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) doit avoir un `Force` paramètre de sorte que lorsque `Force` est spécifié, l’applet de commande ignore l’appel à [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) et poursuit l’opération.</span><span class="sxs-lookup"><span data-stu-id="db21f-144">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="db21f-145">N’oubliez pas que cela n’affecte pas les appels à [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)de commande. ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="db21f-145">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="db21f-146">Le `PassThru` paramètre permet à l’utilisateur d’indiquer si l’applet de commande passe un objet de sortie via le pipeline, dans ce cas, après l’arrêt d’un processus.</span><span class="sxs-lookup"><span data-stu-id="db21f-146">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="db21f-147">N’oubliez pas que ce paramètre est lié à l’applet de commande elle-même et non à une propriété de l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="db21f-147">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="db21f-148">Voici la déclaration du paramètre pour l’applet de commande Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="db21f-148">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="db21f-149">Substitution d’une méthode de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="db21f-149">Overriding an Input Processing Method</span></span>

<span data-ttu-id="db21f-150">L’applet de commande doit remplacer une méthode de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="db21f-150">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="db21f-151">Le code suivant illustre la substitution [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) utilisée dans l’exemple d’applet de commande Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="db21f-151">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="db21f-152">Pour chaque nom de processus demandé, cette méthode garantit que le processus n’est pas un processus spécial, tente d’arrêter le processus, puis envoie un objet de sortie si le `PassThru` paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="db21f-152">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="db21f-153">Appel de la méthode ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="db21f-153">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="db21f-154">La méthode de traitement d’entrée de votre applet de commande doit appeler la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pour confirmer l’exécution d’une opération avant qu’une modification (par exemple, la suppression de fichiers) soit apportée à l’état d’exécution du système.</span><span class="sxs-lookup"><span data-stu-id="db21f-154">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="db21f-155">Cela permet au runtime Windows PowerShell de fournir les comportements « WhatIf » et « Confirm » corrects dans l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="db21f-155">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="db21f-156">Si une applet de commande indique qu’elle prend en charge doit traiter et ne parvient pas à effectuer l’appel [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , l’utilisateur peut modifier le système de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="db21f-156">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="db21f-157">L’appel à [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime Windows PowerShell en tenant compte des paramètres de ligne de commande ou des variables de préférence pour déterminer ce qui doit être affiché à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="db21f-157">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="db21f-158">L’exemple suivant montre l’appel à [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) dans l’applet de commande Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="db21f-158">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="db21f-159">Appel de la méthode ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="db21f-159">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="db21f-160">L’appel à la méthode [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) envoie un message secondaire à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="db21f-160">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="db21f-161">Cet appel est effectué après l’appel à [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) retourne `true` et si le `Force` paramètre n’a pas la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="db21f-161">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="db21f-162">L’utilisateur peut ensuite fournir des commentaires pour indiquer si l’opération doit être poursuivie.</span><span class="sxs-lookup"><span data-stu-id="db21f-162">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="db21f-163">Votre applet de commande appelle [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) en guise de vérification supplémentaire des modifications système potentiellement dangereuses ou lorsque vous souhaitez fournir des options Oui-à-tout et non-tout à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="db21f-163">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="db21f-164">L’exemple suivant illustre l’appel à [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) dans l’applet de commande Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="db21f-164">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="db21f-165">Arrêt du traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="db21f-165">Stopping Input Processing</span></span>

<span data-ttu-id="db21f-166">La méthode de traitement d’entrée d’une applet de commande qui effectue des modifications du système doit permettre d’arrêter le traitement des entrées.</span><span class="sxs-lookup"><span data-stu-id="db21f-166">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="db21f-167">Dans le cas de cette applet de commande Stop-Proc, un appel est effectué à partir de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) vers la méthode [System. Diagnostics. Process. Kill \*](/dotnet/api/System.Diagnostics.Process.Kill) .</span><span class="sxs-lookup"><span data-stu-id="db21f-167">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="db21f-168">Étant donné que le `PassThru` paramètre a la valeur `true` , [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) appelle également [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) pour envoyer l’objet processus au pipeline.</span><span class="sxs-lookup"><span data-stu-id="db21f-168">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="db21f-169">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="db21f-169">Code Sample</span></span>

<span data-ttu-id="db21f-170">Pour obtenir l’exemple de code C# complet, consultez [exemple StopProcessSample01](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="db21f-170">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="db21f-171">Définition des types d’objets et de la mise en forme</span><span class="sxs-lookup"><span data-stu-id="db21f-171">Defining Object Types and Formatting</span></span>

<span data-ttu-id="db21f-172">Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="db21f-172">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="db21f-173">Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db21f-173">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="db21f-174">Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="db21f-174">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="db21f-175">Génération de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="db21f-175">Building the Cmdlet</span></span>

<span data-ttu-id="db21f-176">Après l’implémentation d’une applet de commande, celle-ci doit être inscrite auprès de Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db21f-176">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="db21f-177">Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="db21f-177">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="db21f-178">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="db21f-178">Testing the Cmdlet</span></span>

<span data-ttu-id="db21f-179">Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="db21f-179">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="db21f-180">Voici plusieurs tests qui testent l’applet de commande Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="db21f-180">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="db21f-181">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="db21f-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="db21f-182">Démarrez Windows PowerShell et utilisez l’applet de commande Stop-Proc pour arrêter le traitement, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="db21f-182">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="db21f-183">Étant donné que l’applet de commande spécifie le `Name` paramètre comme obligatoire, l’applet de commande interroge le paramètre.</span><span class="sxs-lookup"><span data-stu-id="db21f-183">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="db21f-184">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="db21f-184">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="db21f-185">Nous allons maintenant utiliser l’applet de commande pour arrêter le processus nommé « NOTEPAD ».</span><span class="sxs-lookup"><span data-stu-id="db21f-185">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="db21f-186">L’applet de commande vous demande de confirmer l’action.</span><span class="sxs-lookup"><span data-stu-id="db21f-186">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

    <span data-ttu-id="db21f-187">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="db21f-187">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="db21f-188">Utilisez Stop-Proc comme indiqué pour arrêter le processus critique nommé « WINLOGON ».</span><span class="sxs-lookup"><span data-stu-id="db21f-188">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="db21f-189">Vous êtes invité à effectuer cette action, qui entraîne le redémarrage du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="db21f-189">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

    <span data-ttu-id="db21f-190">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="db21f-190">The following output appears.</span></span>

    ```Output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="db21f-191">Essayons maintenant d’arrêter le processus WINLOGON sans recevoir d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="db21f-191">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="db21f-192">N’oubliez pas que cette entrée de commande utilise le `Force` paramètre pour remplacer l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="db21f-192">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

    <span data-ttu-id="db21f-193">La sortie suivante apparaît.</span><span class="sxs-lookup"><span data-stu-id="db21f-193">The following output appears.</span></span>

    ```Output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="db21f-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db21f-194">See Also</span></span>

[<span data-ttu-id="db21f-195">Ajout de paramètres qui traitent Command-Line entrée</span><span class="sxs-lookup"><span data-stu-id="db21f-195">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="db21f-196">[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="db21f-196">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="db21f-197">[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="db21f-197">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="db21f-198">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="db21f-198">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="db21f-199">Exemples d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="db21f-199">Cmdlet Samples</span></span>](./cmdlet-samples.md)
