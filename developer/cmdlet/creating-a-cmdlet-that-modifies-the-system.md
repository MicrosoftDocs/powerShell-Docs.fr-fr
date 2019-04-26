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
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068425"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="221c8-102">Création d’une applet de commande qui modifie le système</span><span class="sxs-lookup"><span data-stu-id="221c8-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="221c8-103">Parfois, une applet de commande doit modifier l’état en cours d’exécution du système, pas seulement l’état de l’exécution de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="221c8-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="221c8-104">Dans ce cas, l’applet de commande doit autoriser l’utilisateur une possibilité de vérifier s’il faut apporter la modification.</span><span class="sxs-lookup"><span data-stu-id="221c8-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="221c8-105">Pour prendre en charge de confirmation une applet de commande doit faire deux choses.</span><span class="sxs-lookup"><span data-stu-id="221c8-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="221c8-106">Déclarer que l’applet de commande prend en charge la confirmation lorsque vous spécifiez le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut en définissant le mot-clé SupportsShouldProcess sur `true`.</span><span class="sxs-lookup"><span data-stu-id="221c8-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="221c8-107">Appelez [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pendant l’exécution de l’applet de commande (comme indiqué dans l’exemple suivant).</span><span class="sxs-lookup"><span data-stu-id="221c8-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="221c8-108">En prenant en charge la confirmation, une applet de commande expose le `Confirm` et `WhatIf` paramètres qui sont fournies par Windows PowerShell et également répond aux exigences de développement pour les applets de commande (pour plus d’informations sur les directives de développement d’applet de commande, consultez [ Directives de développement d’applet de commande](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="221c8-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="221c8-109">Modification du système</span><span class="sxs-lookup"><span data-stu-id="221c8-109">Changing the System</span></span>

<span data-ttu-id="221c8-110">Le fait de « modification du système » fait référence à une applet de commande qui potentiellement modifie l’état du système en dehors de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="221c8-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="221c8-111">Par exemple, l’arrêt d’un processus, l’activation ou la désactivation d’un compte d’utilisateur ou ajouter une ligne à une table de base de données sont toutes les modifications apportées au système qui doit être confirmé.</span><span class="sxs-lookup"><span data-stu-id="221c8-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="221c8-112">En revanche, les opérations de lire les données ou établissent des connexions temporaires ne modifiez pas le système et ne nécessitent généralement pas de confirmation.</span><span class="sxs-lookup"><span data-stu-id="221c8-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="221c8-113">Confirmation n’est pas également nécessaire pour les actions dont l’effet est limitée au sein du runtime Windows PowerShell, comme `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="221c8-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="221c8-114">Applets de commande qui peut ou peut ne pas faire une modification permanente doit déclarer `SupportsShouldProcess` et appelez [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) uniquement s’ils sont sur le point d’apporter une modification permanente.</span><span class="sxs-lookup"><span data-stu-id="221c8-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="221c8-115">Confirmation de ShouldProcess s’applique uniquement aux applets de commande.</span><span class="sxs-lookup"><span data-stu-id="221c8-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="221c8-116">Si une commande ou un script modifie l’état en cours d’exécution d’un système en appelant directement des propriétés ou méthodes .NET, ou en appelant des applications en dehors de Windows PowerShell, il se peut que cette forme de confirmation ne sera pas disponible.</span><span class="sxs-lookup"><span data-stu-id="221c8-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="221c8-117">L’applet de commande StopProc</span><span class="sxs-lookup"><span data-stu-id="221c8-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="221c8-118">Cette rubrique décrit une applet de commande Stop-Process qui tente d’arrêter les processus qui sont récupérées à l’aide de l’applet de commande Get-Process (décrit dans [création de votre première applet de commande](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="221c8-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="221c8-119">Rubriques de cette section sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="221c8-119">Topics in this section include the following:</span></span>

- [<span data-ttu-id="221c8-120">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="221c8-120">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="221c8-121">Définition des paramètres pour la Modification du système</span><span class="sxs-lookup"><span data-stu-id="221c8-121">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="221c8-122">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="221c8-122">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="221c8-123">Appel de la méthode ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="221c8-123">Calling the ShouldProcess Method</span></span>](#Calling-the-ShouldProcess-Method)

- [<span data-ttu-id="221c8-124">Appel de la méthode ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="221c8-124">Calling the ShouldContinue Method</span></span>](#Calling-the-ShouldContinue-Method)

- [<span data-ttu-id="221c8-125">Arrêt de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="221c8-125">Stopping Input Processing</span></span>](#Stopping-Input-Processing)

- [<span data-ttu-id="221c8-126">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="221c8-126">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="221c8-127">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="221c8-127">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="221c8-128">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="221c8-128">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="221c8-129">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="221c8-129">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="221c8-130">Définition de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="221c8-130">Defining the Cmdlet</span></span>

<span data-ttu-id="221c8-131">La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="221c8-131">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="221c8-132">Étant donné que vous écrivez une applet de commande pour modifier le système, il doit être nommé en conséquence.</span><span class="sxs-lookup"><span data-stu-id="221c8-132">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="221c8-133">Cette applet de commande s’arrête système traite, par conséquent, le nom du verbe choisi ici est « Stop », défini par le [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (classe), avec le nom « Proc » pour indiquer que l’applet de commande arrête le processus.</span><span class="sxs-lookup"><span data-stu-id="221c8-133">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="221c8-134">Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="221c8-134">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="221c8-135">Voici la définition de classe pour cette applet de commande Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="221c8-135">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="221c8-136">N’oubliez pas que, dans le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) déclaration, le `SupportsShouldProcess` mot clé d’attribut est défini sur `true` pour activer l’applet de commande effectuer des appels à [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="221c8-136">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="221c8-137">Sans ce jeu de mot clé, le `Confirm` et `WhatIf` paramètres ne seront pas disponibles à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="221c8-137">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="221c8-138">Actions extrêmement destructeur</span><span class="sxs-lookup"><span data-stu-id="221c8-138">Extremely Destructive Actions</span></span>

<span data-ttu-id="221c8-139">Certaines opérations sont extrêmement destructeur, telles que le reformatage d’une partition de disque dur actif.</span><span class="sxs-lookup"><span data-stu-id="221c8-139">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="221c8-140">Dans ces cas, l’applet de commande doit définir `ConfirmImpact`  =  `ConfirmImpact.High` lorsque vous déclarez le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut.</span><span class="sxs-lookup"><span data-stu-id="221c8-140">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="221c8-141">Ce paramètre force l’applet de commande pour demander la confirmation utilisateur même lorsque l’utilisateur n’a pas spécifié le `Confirm` paramètre.</span><span class="sxs-lookup"><span data-stu-id="221c8-141">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="221c8-142">Toutefois, les développeurs d’applet de commande doivent éviter un abus de `ConfirmImpact` pour les opérations qui sont simplement potentiellement destructrices, telles que la suppression d’un compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="221c8-142">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="221c8-143">Rappelez-vous que si `ConfirmImpact` a la valeur [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span><span class="sxs-lookup"><span data-stu-id="221c8-143">Remember that if `ConfirmImpact` is set to [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span></span>

<span data-ttu-id="221c8-144">De même, certaines opérations sont peu de chances d’être destructive, bien qu’elles modifient en théorie l’état en cours d’exécution d’un système en dehors de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="221c8-144">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="221c8-145">Ces applets de commande peut définir `ConfirmImpact` à [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="221c8-145">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="221c8-146">Cela permettra d’ignorer les demandes de confirmation où l’utilisateur a demandé de confirmer les opérations uniquement moyenne impact et à fort impact.</span><span class="sxs-lookup"><span data-stu-id="221c8-146">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="221c8-147">Définition des paramètres pour la Modification du système</span><span class="sxs-lookup"><span data-stu-id="221c8-147">Defining Parameters for System Modification</span></span>

<span data-ttu-id="221c8-148">Cette section décrit comment définir les paramètres de l’applet de commande, y compris ceux qui sont nécessaires pour la modification d’un système de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="221c8-148">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="221c8-149">Consultez [ajoutant des paramètres de cette entrée de ligne de commande de processus](./adding-parameters-that-process-command-line-input.md) si vous avez besoin des informations générales sur la définition des paramètres.</span><span class="sxs-lookup"><span data-stu-id="221c8-149">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="221c8-150">L’applet de commande Stop-Process définit trois paramètres : `Name`, `Force`, et `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="221c8-150">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="221c8-151">Le `Name` paramètre correspond à la `Name` propriété de l’objet d’entrée du processus.</span><span class="sxs-lookup"><span data-stu-id="221c8-151">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="221c8-152">N’oubliez pas que le `Name` paramètre dans cet exemple est obligatoire, comme l’applet de commande échouera si elle n’a pas d’un processus nommé à arrêter.</span><span class="sxs-lookup"><span data-stu-id="221c8-152">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="221c8-153">Le `Force` paramètre permet à l’utilisateur à remplacer les appels à [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="221c8-153">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="221c8-154">En fait, une applet de commande qui appelle [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) doit avoir un `Force` paramètre afin que lorsque `Force` est spécifié, l’applet de commande ignore l’appel à [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) et poursuit l’opération.</span><span class="sxs-lookup"><span data-stu-id="221c8-154">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="221c8-155">N’oubliez pas que cela n’affecte pas les appels à [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="221c8-155">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="221c8-156">Le `PassThru` paramètre permet à l’utilisateur indiquer si l’applet de commande passe un objet de sortie via le pipeline, dans ce cas, une fois un processus est arrêté.</span><span class="sxs-lookup"><span data-stu-id="221c8-156">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="221c8-157">N’oubliez pas que ce paramètre est lié à l’applet de commande lui-même plutôt qu’à une propriété de l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="221c8-157">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="221c8-158">Voici la déclaration de paramètre pour l’applet de commande Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="221c8-158">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="221c8-159">Substitution d’une méthode de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="221c8-159">Overriding an Input Processing Method</span></span>

<span data-ttu-id="221c8-160">L’applet de commande doit substituer une méthode de traitement des entrées.</span><span class="sxs-lookup"><span data-stu-id="221c8-160">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="221c8-161">Le code suivant illustre la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) utilisé dans l’applet de commande Stop-Process exemple de remplacement.</span><span class="sxs-lookup"><span data-stu-id="221c8-161">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="221c8-162">Pour chaque demandé de nom de processus, cette méthode garantit que le processus n’est pas un processus spécial, qu’il tente d’arrêter le processus et qu’il envoie ensuite un objet de sortie si la `PassThru` est précisé.</span><span class="sxs-lookup"><span data-stu-id="221c8-162">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="221c8-163">Appel de la méthode ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="221c8-163">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="221c8-164">L’entrée de traitement de la méthode de votre applet de commande doit appeler le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pour confirmer l’exécution d’une opération avant une modification (par exemple, une suppression de fichiers) est apportée à l’état en cours d’exécution (méthode) du système.</span><span class="sxs-lookup"><span data-stu-id="221c8-164">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="221c8-165">Cela permet l’exécution de Windows PowerShell pour fournir le comportement correct de « WhatIf » et « Confirmer » au sein de l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="221c8-165">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="221c8-166">Si une applet de commande indique qu’il prend en charge doit traiter et ne parvient pas à rendre le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appeler, l’utilisateur peut modifier le système de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="221c8-166">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="221c8-167">L’appel à [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime de Windows PowerShell en prenant en compte les paramètres de ligne de commande ou les variables de préférence pour déterminer ce qui doit être affiché à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="221c8-167">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="221c8-168">L’exemple suivant illustre l’appel à [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) à partir de la substitution de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode dans l’exemple L’applet de commande Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="221c8-168">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="221c8-169">Appel de la méthode ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="221c8-169">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="221c8-170">L’appel à la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthode envoie un message secondaire à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="221c8-170">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="221c8-171">Cet appel est effectué après l’appel à [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) retourne `true` et si le `Force` paramètre n’a pas été défini `true`.</span><span class="sxs-lookup"><span data-stu-id="221c8-171">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="221c8-172">L’utilisateur peut ensuite fournir des commentaires pour indiquer si l’opération doit être poursuivie.</span><span class="sxs-lookup"><span data-stu-id="221c8-172">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="221c8-173">Vos appels de l’applet de commande [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) une vérification supplémentaire pour les modifications du système potentiellement dangereux ou lorsque vous souhaitez fournir des options Oui à tous et non à tous à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="221c8-173">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="221c8-174">L’exemple suivant illustre l’appel à [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) à partir de la substitution de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode dans l’exemple L’applet de commande Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="221c8-174">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="221c8-175">Arrêt de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="221c8-175">Stopping Input Processing</span></span>

<span data-ttu-id="221c8-176">L’entrée de méthode d’une applet de commande qui effectue des modifications de système de traitement doit fournir un moyen de l’arrêt du traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="221c8-176">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="221c8-177">Dans le cas de cette applet de commande Stop-Process, un appel est effectué à partir de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode à la [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) (méthode).</span><span class="sxs-lookup"><span data-stu-id="221c8-177">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="221c8-178">Étant donné que le `PassThru` paramètre est défini sur `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) appelle également [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) à envoyer l’objet processus au pipeline.</span><span class="sxs-lookup"><span data-stu-id="221c8-178">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="221c8-179">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="221c8-179">Code Sample</span></span>

<span data-ttu-id="221c8-180">Pour l’ensemble C# exemple de code, consultez [StopProcessSample01 exemple](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="221c8-180">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="221c8-181">Définition des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="221c8-181">Defining Object Types and Formatting</span></span>

<span data-ttu-id="221c8-182">Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="221c8-182">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="221c8-183">Par conséquent, peut-être une applet de commande définir son propre type, ou peut-être l’applet de commande étendre un type existant fourni par une autre applet de commande.</span><span class="sxs-lookup"><span data-stu-id="221c8-183">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="221c8-184">Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="221c8-184">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="221c8-185">Création de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="221c8-185">Building the Cmdlet</span></span>

<span data-ttu-id="221c8-186">Après l’implémentation d’une applet de commande, il doit être enregistré avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="221c8-186">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="221c8-187">Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="221c8-187">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="221c8-188">Test de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="221c8-188">Testing the Cmdlet</span></span>

<span data-ttu-id="221c8-189">Lorsque votre applet de commande a été inscrite avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="221c8-189">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="221c8-190">Voici plusieurs tests qui testent l’applet de commande Stop-Process.</span><span class="sxs-lookup"><span data-stu-id="221c8-190">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="221c8-191">Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="221c8-191">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="221c8-192">Démarrez Windows PowerShell et utilisez l’applet de commande Stop-Process pour arrêter le traitement comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="221c8-192">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="221c8-193">Étant donné que l’applet de commande spécifie le `Name` paramètre comme étant obligatoire, les requêtes de l’applet de commande pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="221c8-193">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="221c8-194">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="221c8-194">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="221c8-195">Maintenant nous allons utiliser l’applet de commande pour arrêter le processus nommé « NOTEPAD ».</span><span class="sxs-lookup"><span data-stu-id="221c8-195">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="221c8-196">L’applet de commande vous invite à confirmer l’action.</span><span class="sxs-lookup"><span data-stu-id="221c8-196">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="221c8-197">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="221c8-197">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="221c8-198">Comme indiqué, utilisez Stop-Process pour arrêter le processus critique nommé « WINLOGON ».</span><span class="sxs-lookup"><span data-stu-id="221c8-198">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="221c8-199">Vous êtes invité et un avertissement d’exécution de cette action, car elle entraîne le redémarrage du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="221c8-199">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="221c8-200">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="221c8-200">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="221c8-201">Nous allons maintenant essayez d’arrêter le processus WINLOGON sans recevoir d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="221c8-201">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="221c8-202">N’oubliez pas que cette entrée de la commande utilise le `Force` paramètre pour remplacer l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="221c8-202">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="221c8-203">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="221c8-203">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="221c8-204">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="221c8-204">See Also</span></span>

[<span data-ttu-id="221c8-205">Ajout de paramètres qui traitent l’entrée de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="221c8-205">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="221c8-206">Extension des Types d’objets et mise en forme</span><span class="sxs-lookup"><span data-stu-id="221c8-206">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="221c8-207">Comment inscrire les applets de commande, fournisseurs et héberger des Applications</span><span class="sxs-lookup"><span data-stu-id="221c8-207">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="221c8-208">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="221c8-208">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="221c8-209">Exemples d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="221c8-209">Cmdlet Samples</span></span>](./cmdlet-samples.md)