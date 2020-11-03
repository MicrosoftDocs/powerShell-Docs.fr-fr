---
description: Décrit comment les fonctions qui spécifient l' `CmdletBinding` attribut peuvent utiliser les méthodes et les propriétés disponibles pour les applets de commande compilées.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 260dab1937715da34b9191ff2765dee7d2ac3ec5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208037"
---
# <a name="about-functions-advanced-methods"></a><span data-ttu-id="30561-104">À propos des méthodes avancées des fonctions</span><span class="sxs-lookup"><span data-stu-id="30561-104">About Functions Advanced Methods</span></span>

## <a name="short-description"></a><span data-ttu-id="30561-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="30561-105">Short description</span></span>

<span data-ttu-id="30561-106">Décrit comment les fonctions qui spécifient l' `CmdletBinding` attribut peuvent utiliser les méthodes et les propriétés disponibles pour les applets de commande compilées.</span><span class="sxs-lookup"><span data-stu-id="30561-106">Describes how functions that specify the `CmdletBinding` attribute can use the methods and properties that are available to compiled cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="30561-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="30561-107">Long description</span></span>

<span data-ttu-id="30561-108">Les fonctions qui spécifient l' `CmdletBinding` attribut peuvent accéder à un certain nombre de méthodes et de propriétés via la `$PSCmdlet` variable.</span><span class="sxs-lookup"><span data-stu-id="30561-108">Functions that specify the `CmdletBinding` attribute can access a number of methods and properties through the `$PSCmdlet` variable.</span></span> <span data-ttu-id="30561-109">Ces méthodes incluent les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="30561-109">These methods include the following methods:</span></span>

- <span data-ttu-id="30561-110">Les méthodes de traitement d’entrée utilisées par les applets de commande pour effectuer leur travail.</span><span class="sxs-lookup"><span data-stu-id="30561-110">Input-processing methods that compiled cmdlets use to do their work.</span></span>
- <span data-ttu-id="30561-111">`ShouldProcess`Méthodes et `ShouldContinue` utilisées pour obtenir des commentaires de la part de l’utilisateur avant l’exécution d’une action.</span><span class="sxs-lookup"><span data-stu-id="30561-111">The `ShouldProcess` and `ShouldContinue` methods that are used to get user feedback before an action is performed.</span></span>
- <span data-ttu-id="30561-112">`ThrowTerminatingError`Méthode permettant de générer des enregistrements d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="30561-112">The `ThrowTerminatingError` method for generating error records.</span></span>
- <span data-ttu-id="30561-113">Plusieurs `Write` méthodes qui retournent des types de sortie différents.</span><span class="sxs-lookup"><span data-stu-id="30561-113">Several `Write` methods that return different types of output.</span></span>

<span data-ttu-id="30561-114">Toutes les méthodes et propriétés de la classe **PSCmdlet** sont disponibles pour les fonctions avancées.</span><span class="sxs-lookup"><span data-stu-id="30561-114">All the methods and properties of the **PSCmdlet** class are available to advanced functions.</span></span> <span data-ttu-id="30561-115">Pour plus d’informations, consultez [System. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span><span class="sxs-lookup"><span data-stu-id="30561-115">For more information, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="30561-116">Pour plus d’informations sur l' `CmdletBinding` attribut, consultez [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span><span class="sxs-lookup"><span data-stu-id="30561-116">For more information about the `CmdletBinding` attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>
<span data-ttu-id="30561-117">Pour la classe **CmdletBindingAttribute** , consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdletbindingattribute)de commande. CmdletBindingAttribute.</span><span class="sxs-lookup"><span data-stu-id="30561-117">For the **CmdletBindingAttribute** class, see [System.Management.Automation.Cmdlet.CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute).</span></span>

### <a name="input-processing-methods"></a><span data-ttu-id="30561-118">Méthodes de traitement d’entrée</span><span class="sxs-lookup"><span data-stu-id="30561-118">Input processing methods</span></span>

<span data-ttu-id="30561-119">Les méthodes décrites dans cette section sont appelées méthodes de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="30561-119">The methods described in this section are referred to as the input processing methods.</span></span> <span data-ttu-id="30561-120">Pour les fonctions, ces trois méthodes sont représentées par les `Begin` `Process` blocs, et `End` de la fonction.</span><span class="sxs-lookup"><span data-stu-id="30561-120">For functions, these three methods are represented by the `Begin`, `Process`, and `End` blocks of the function.</span></span> <span data-ttu-id="30561-121">Vous n’êtes pas obligé d’utiliser ces blocs dans vos fonctions.</span><span class="sxs-lookup"><span data-stu-id="30561-121">You aren't required to use any of these blocks in your functions.</span></span>

> [!NOTE]
> <span data-ttu-id="30561-122">Ces blocs sont également disponibles pour les fonctions qui n’utilisent pas l' `CmdletBinding` attribut.</span><span class="sxs-lookup"><span data-stu-id="30561-122">These blocks are also available to functions that don't use the `CmdletBinding` attribute.</span></span>

#### <a name="begin"></a><span data-ttu-id="30561-123">Début</span><span class="sxs-lookup"><span data-stu-id="30561-123">Begin</span></span>

<span data-ttu-id="30561-124">Ce bloc est utilisé pour fournir un prétraitement unique facultatif pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="30561-124">This block is used to provide optional one-time preprocessing for the function.</span></span>
<span data-ttu-id="30561-125">Le runtime PowerShell utilise le code de ce bloc une fois pour chaque instance de la fonction dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="30561-125">The PowerShell runtime uses the code in this block once for each instance of the function in the pipeline.</span></span>

#### <a name="process"></a><span data-ttu-id="30561-126">Process</span><span class="sxs-lookup"><span data-stu-id="30561-126">Process</span></span>

<span data-ttu-id="30561-127">Ce bloc est utilisé pour fournir un traitement d’enregistrement par enregistrement pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="30561-127">This block is used to provide record-by-record processing for the function.</span></span> <span data-ttu-id="30561-128">Vous pouvez utiliser un `Process` bloc sans définir les autres blocs.</span><span class="sxs-lookup"><span data-stu-id="30561-128">You can use a `Process` block without defining the other blocks.</span></span> <span data-ttu-id="30561-129">Le nombre d' `Process` exécutions de bloc dépend de la façon dont vous utilisez la fonction et de l’entrée que la fonction reçoit.</span><span class="sxs-lookup"><span data-stu-id="30561-129">The number of `Process` block executions depends on how you use the function and what input the function receives.</span></span>

<span data-ttu-id="30561-130">La variable automatique `$_` ou `$PSItem` contient l’objet actuel dans le pipeline à utiliser dans le `Process` bloc.</span><span class="sxs-lookup"><span data-stu-id="30561-130">The automatic variable `$_` or `$PSItem` contains the current object in the pipeline for use in the `Process` block.</span></span> <span data-ttu-id="30561-131">La `$input` variable automatique contient un énumérateur qui est uniquement disponible pour les fonctions et les blocs de script.</span><span class="sxs-lookup"><span data-stu-id="30561-131">The `$input` automatic variable contains an enumerator that's only available to functions and script blocks.</span></span>
<span data-ttu-id="30561-132">Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="30561-132">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="30561-133">L’appel de la fonction au début, ou à l’extérieur d’un pipeline, exécute le `Process` bloc une fois.</span><span class="sxs-lookup"><span data-stu-id="30561-133">Calling the function at the beginning, or outside of a pipeline, executes the `Process` block once.</span></span>
- <span data-ttu-id="30561-134">Dans un pipeline, le `Process` bloc s’exécute une fois pour chaque objet d’entrée qui atteint la fonction.</span><span class="sxs-lookup"><span data-stu-id="30561-134">Within a pipeline, the `Process` block executes once for each input object that reaches the function.</span></span>
- <span data-ttu-id="30561-135">Si l’entrée de pipeline qui atteint la fonction est vide, le `Process` bloc ne s’exécute **pas** .</span><span class="sxs-lookup"><span data-stu-id="30561-135">If the pipeline input that reaches the function is empty, the `Process` block **does not** execute.</span></span>
  - <span data-ttu-id="30561-136">Les `Begin` `End` blocs et s’exécutent toujours.</span><span class="sxs-lookup"><span data-stu-id="30561-136">The `Begin` and `End` blocks still execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30561-137">Si un paramètre de fonction est défini pour accepter l’entrée de pipeline et qu’un `Process` bloc n’est pas défini, le traitement d’enregistrement par enregistrement échoue.</span><span class="sxs-lookup"><span data-stu-id="30561-137">If a function parameter is set to accept pipeline input, and a `Process` block isn't defined, record-by-record processing will fail.</span></span> <span data-ttu-id="30561-138">Dans ce cas, votre fonction ne s’exécutera qu’une seule fois, quelle que soit l’entrée.</span><span class="sxs-lookup"><span data-stu-id="30561-138">In this case, your function will only execute once, regardless of the input.</span></span>

#### <a name="end"></a><span data-ttu-id="30561-139">End</span><span class="sxs-lookup"><span data-stu-id="30561-139">End</span></span>

<span data-ttu-id="30561-140">Ce bloc est utilisé pour fournir un traitement unique facultatif pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="30561-140">This block is used to provide optional one-time post-processing for the function.</span></span>

<span data-ttu-id="30561-141">L’exemple suivant montre le plan d’une fonction qui contient un bloc pour le prétraitement à usage `Begin` unique, un `Process` bloc pour le traitement des enregistrements multiples et un `End` bloc pour le traitement unique à la fois.</span><span class="sxs-lookup"><span data-stu-id="30561-141">The following example shows the outline of a function that contains a `Begin` block for one-time preprocessing, a `Process` block for multiple record processing, and an `End` block for one-time post-processing.</span></span>

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> <span data-ttu-id="30561-142">`Begin`Si vous utilisez un `End` bloc ou, vous devez définir les trois blocs.</span><span class="sxs-lookup"><span data-stu-id="30561-142">Using either a `Begin` or `End` block requires that you define all three blocks.</span></span> <span data-ttu-id="30561-143">Lorsque vous utilisez les trois blocs, tout le code PowerShell doit se trouver à l’intérieur de l’un des blocs.</span><span class="sxs-lookup"><span data-stu-id="30561-143">When using all three blocks, all PowerShell code must be inside one of the blocks.</span></span>

### <a name="confirmation-methods"></a><span data-ttu-id="30561-144">Méthodes de confirmation</span><span class="sxs-lookup"><span data-stu-id="30561-144">Confirmation methods</span></span>

#### <a name="shouldprocess"></a><span data-ttu-id="30561-145">ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="30561-145">ShouldProcess</span></span>

<span data-ttu-id="30561-146">Cette méthode est appelée pour demander la confirmation de l’utilisateur avant que la fonction exécute une action qui modifie le système.</span><span class="sxs-lookup"><span data-stu-id="30561-146">This method is called to request confirmation from the user before the function performs an action that would change the system.</span></span> <span data-ttu-id="30561-147">La fonction peut continuer en fonction de la valeur booléenne retournée par la méthode.</span><span class="sxs-lookup"><span data-stu-id="30561-147">The function can continue based on the Boolean value returned by the method.</span></span> <span data-ttu-id="30561-148">Cette méthode ne peut être appelée qu’à partir du `Process{}` bloc de la fonction.</span><span class="sxs-lookup"><span data-stu-id="30561-148">This method can only be called only from within the `Process{}` block of the function.</span></span> <span data-ttu-id="30561-149">L' `CmdletBinding` attribut doit également déclarer que la fonction prend en charge `ShouldProcess` (comme indiqué dans l’exemple précédent).</span><span class="sxs-lookup"><span data-stu-id="30561-149">The `CmdletBinding` attribute must also declare that the function supports `ShouldProcess` (as shown in the previous example).</span></span>

<span data-ttu-id="30561-150">Pour plus d’informations sur cette méthode, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.shouldprocess)de commande. ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="30561-150">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess).</span></span>

<span data-ttu-id="30561-151">Pour plus d’informations sur la demande de confirmation, consultez [demande de confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span><span class="sxs-lookup"><span data-stu-id="30561-151">For more information about how to request confirmation, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

#### <a name="shouldcontinue"></a><span data-ttu-id="30561-152">ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="30561-152">ShouldContinue</span></span>

<span data-ttu-id="30561-153">Cette méthode est appelée pour demander un deuxième message de confirmation.</span><span class="sxs-lookup"><span data-stu-id="30561-153">This method is called to request a second confirmation message.</span></span> <span data-ttu-id="30561-154">Elle doit être appelée lorsque la `ShouldProcess` méthode retourne `$true` .</span><span class="sxs-lookup"><span data-stu-id="30561-154">It should be called when the `ShouldProcess` method returns `$true`.</span></span> <span data-ttu-id="30561-155">Pour plus d’informations sur cette méthode, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.shouldcontinue)de commande. ShouldContinue.</span><span class="sxs-lookup"><span data-stu-id="30561-155">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).</span></span>

### <a name="error-methods"></a><span data-ttu-id="30561-156">Méthodes d’erreur</span><span class="sxs-lookup"><span data-stu-id="30561-156">Error methods</span></span>

<span data-ttu-id="30561-157">Les fonctions peuvent appeler deux méthodes différentes lorsque des erreurs se produisent.</span><span class="sxs-lookup"><span data-stu-id="30561-157">Functions can call two different methods when errors occur.</span></span> <span data-ttu-id="30561-158">Lorsqu’une erreur sans fin d’exécution se produit, la fonction doit appeler la `WriteError` méthode, qui est décrite dans la `Write` section Méthodes.</span><span class="sxs-lookup"><span data-stu-id="30561-158">When a non-terminating error occurs, the function should call the `WriteError` method, which is described in the `Write` methods section.</span></span> <span data-ttu-id="30561-159">Lorsqu’une erreur se termine et que la fonction ne peut pas continuer, elle doit appeler la `ThrowTerminatingError` méthode.</span><span class="sxs-lookup"><span data-stu-id="30561-159">When a terminating error occurs and the function can't continue, it should call the `ThrowTerminatingError` method.</span></span> <span data-ttu-id="30561-160">Vous pouvez également utiliser l' `Throw` instruction pour les erreurs de fin et l’applet de commande [write-error](xref:Microsoft.PowerShell.Utility.Write-Error) pour les erreurs sans fin d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="30561-160">You can also use the `Throw` statement for terminating errors and the [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error) cmdlet for non-terminating errors.</span></span>

<span data-ttu-id="30561-161">Pour plus d’informations, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror)de commande. ThrowTerminatingError.</span><span class="sxs-lookup"><span data-stu-id="30561-161">For more information, see [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror).</span></span>

### <a name="write-methods"></a><span data-ttu-id="30561-162">Méthodes d’écriture</span><span class="sxs-lookup"><span data-stu-id="30561-162">Write methods</span></span>

<span data-ttu-id="30561-163">Une fonction peut appeler les méthodes suivantes pour retourner différents types de sortie.</span><span class="sxs-lookup"><span data-stu-id="30561-163">A function can call the following methods to return different types of output.</span></span>
<span data-ttu-id="30561-164">Notez que tous les résultats ne sont pas transmis à la commande suivante dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="30561-164">Notice that not all the output goes to the next command in the pipeline.</span></span> <span data-ttu-id="30561-165">Vous pouvez également utiliser les différentes `Write` applets de commande, telles que `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="30561-165">You can also use the various `Write` cmdlets, such as `Write-Error`.</span></span>

#### <a name="writecommanddetail"></a><span data-ttu-id="30561-166">WriteCommandDetail</span><span class="sxs-lookup"><span data-stu-id="30561-166">WriteCommandDetail</span></span>

<span data-ttu-id="30561-167">Pour plus d’informations sur la `WriteCommandDetails` méthode, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.writecommanddetail)de commande. WriteCommandDetail.</span><span class="sxs-lookup"><span data-stu-id="30561-167">For information about the `WriteCommandDetails` method, see [System.Management.Automation.Cmdlet.WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail).</span></span>

#### <a name="writedebug"></a><span data-ttu-id="30561-168">WriteDebug</span><span class="sxs-lookup"><span data-stu-id="30561-168">WriteDebug</span></span>

<span data-ttu-id="30561-169">Pour fournir des informations qui peuvent être utilisées pour résoudre les problèmes d’une fonction, faites en sorte que la fonction appelle la `WriteDebug` méthode.</span><span class="sxs-lookup"><span data-stu-id="30561-169">To provide information that can be used to troubleshoot a function, make the function call the `WriteDebug` method.</span></span> <span data-ttu-id="30561-170">La `WriteDebug` méthode affiche des messages de débogage à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="30561-170">The `WriteDebug` method displays debug messages to the user.</span></span> <span data-ttu-id="30561-171">Pour plus d’informations, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.writedebug)de commande. WriteDebug.</span><span class="sxs-lookup"><span data-stu-id="30561-171">For more information, see [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug).</span></span>

#### <a name="writeerror"></a><span data-ttu-id="30561-172">WriteError</span><span class="sxs-lookup"><span data-stu-id="30561-172">WriteError</span></span>

<span data-ttu-id="30561-173">Les fonctions doivent appeler cette méthode lorsque des erreurs sans fin d’exécution se produisent et que la fonction est conçue pour poursuivre le traitement des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="30561-173">Functions should call this method when non-terminating errors occur and the function is designed to continue processing records.</span></span> <span data-ttu-id="30561-174">Pour plus d’informations, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.writeerror)de commande. WriteError.</span><span class="sxs-lookup"><span data-stu-id="30561-174">For more information, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror).</span></span>

> [!NOTE]
> <span data-ttu-id="30561-175">Si une erreur se termine, la fonction doit appeler la méthode [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) .</span><span class="sxs-lookup"><span data-stu-id="30561-175">If a terminating error occurs, the function should call the [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) method.</span></span>

#### <a name="writeobject"></a><span data-ttu-id="30561-176">WriteObject</span><span class="sxs-lookup"><span data-stu-id="30561-176">WriteObject</span></span>

<span data-ttu-id="30561-177">La `WriteObject` méthode permet à la fonction d’envoyer un objet à la commande suivante dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="30561-177">The `WriteObject` method allows the function to send an object to the next command in the pipeline.</span></span> <span data-ttu-id="30561-178">Dans la plupart des cas, `WriteObject` est la méthode à utiliser lorsque la fonction retourne des données.</span><span class="sxs-lookup"><span data-stu-id="30561-178">In most cases, `WriteObject` is the method to use when the function returns data.</span></span> <span data-ttu-id="30561-179">Pour plus d’informations, consultez [System. Management. Automation. PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject).</span><span class="sxs-lookup"><span data-stu-id="30561-179">For more information, see [System.Management.Automation.PSCmdlet.WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject).</span></span>

#### <a name="writeprogress"></a><span data-ttu-id="30561-180">WriteProgress</span><span class="sxs-lookup"><span data-stu-id="30561-180">WriteProgress</span></span>

<span data-ttu-id="30561-181">Pour les fonctions avec des actions dont l’exécution prend beaucoup de temps, cette méthode permet à la fonction d’appeler la `WriteProgress` méthode afin d’afficher les informations de progression.</span><span class="sxs-lookup"><span data-stu-id="30561-181">For functions with actions that take a long time to complete, this method allows the function to call the `WriteProgress` method so that progress information is displayed.</span></span> <span data-ttu-id="30561-182">Par exemple, vous pouvez afficher le pourcentage effectué.</span><span class="sxs-lookup"><span data-stu-id="30561-182">For example, you can display the percent completed.</span></span>
<span data-ttu-id="30561-183">Pour plus d’informations, consultez [System. Management. Automation. PSCmdlet. WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress).</span><span class="sxs-lookup"><span data-stu-id="30561-183">For more information, see [System.Management.Automation.PSCmdlet.WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress).</span></span>

#### <a name="writeverbose"></a><span data-ttu-id="30561-184">WriteVerbose</span><span class="sxs-lookup"><span data-stu-id="30561-184">WriteVerbose</span></span>

<span data-ttu-id="30561-185">Pour fournir des informations détaillées sur ce que fait la fonction, faites en sorte que la fonction appelle la `WriteVerbose` méthode pour afficher des messages détaillés à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="30561-185">To provide detailed information about what the function is doing, make the function call the `WriteVerbose` method to display verbose messages to the user.</span></span> <span data-ttu-id="30561-186">Par défaut, les messages détaillés ne sont pas affichés.</span><span class="sxs-lookup"><span data-stu-id="30561-186">By default, verbose messages aren't displayed.</span></span> <span data-ttu-id="30561-187">Pour plus d’informations, consultez [System. Management. Automation. PSCmdlet. WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose).</span><span class="sxs-lookup"><span data-stu-id="30561-187">For more information, see [System.Management.Automation.PSCmdlet.WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose).</span></span>

#### <a name="writewarning"></a><span data-ttu-id="30561-188">WriteWarning</span><span class="sxs-lookup"><span data-stu-id="30561-188">WriteWarning</span></span>

<span data-ttu-id="30561-189">Pour fournir des informations sur les conditions qui peuvent entraîner des résultats inattendus, faites en sorte que la fonction appelle la méthode WriteWarning pour afficher des messages d’avertissement à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="30561-189">To provide information about conditions that may cause unexpected results, make the function call the WriteWarning method to display warning messages to the user.</span></span> <span data-ttu-id="30561-190">Par défaut, les messages d’avertissement s’affichent.</span><span class="sxs-lookup"><span data-stu-id="30561-190">By default, warning messages are displayed.</span></span> <span data-ttu-id="30561-191">Pour plus d’informations, consultez [System. Management. Automation. PSCmdlet. WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning).</span><span class="sxs-lookup"><span data-stu-id="30561-191">For more information, see [System.Management.Automation.PSCmdlet.WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning).</span></span>

> [!NOTE]
> <span data-ttu-id="30561-192">Vous pouvez également afficher des messages d’avertissement en configurant la `$WarningPreference` variable ou à l’aide des `Verbose` options de ligne de commande et `Debug` .</span><span class="sxs-lookup"><span data-stu-id="30561-192">You can also display warning messages by configuring the `$WarningPreference` variable or by using the `Verbose` and `Debug` command-line options.</span></span> <span data-ttu-id="30561-193">Pour plus d’informations sur la `$WarningPreference` variable, consultez [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="30561-193">for more information about the `$WarningPreference` variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="other-methods-and-properties"></a><span data-ttu-id="30561-194">Autres méthodes et propriétés</span><span class="sxs-lookup"><span data-stu-id="30561-194">Other methods and properties</span></span>

<span data-ttu-id="30561-195">Pour plus d’informations sur les autres méthodes et propriétés accessibles via la `$PSCmdlet` variable, consultez [System. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span><span class="sxs-lookup"><span data-stu-id="30561-195">For information about the other methods and properties that can be accessed through the `$PSCmdlet` variable, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="30561-196">Par exemple, la propriété [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) vous permet de voir le jeu de paramètres en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="30561-196">For example, the [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) property allows you to see the parameter set that is being used.</span></span> <span data-ttu-id="30561-197">Les jeux de paramètres vous permettent de créer une fonction qui exécute différentes tâches en fonction des paramètres spécifiés lors de l’exécution de la fonction.</span><span class="sxs-lookup"><span data-stu-id="30561-197">Parameter sets allow you to create a function that performs different tasks based on the parameters that are specified when the function is run.</span></span>

## <a name="see-also"></a><span data-ttu-id="30561-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30561-198">See also</span></span>

[<span data-ttu-id="30561-199">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="30561-199">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="30561-200">about_Functions</span><span class="sxs-lookup"><span data-stu-id="30561-200">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="30561-201">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="30561-201">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="30561-202">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="30561-202">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="30561-203">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="30561-203">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="30561-204">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="30561-204">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="30561-205">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="30561-205">about_Preference_Variables</span></span>](about_Preference_Variables.md)
