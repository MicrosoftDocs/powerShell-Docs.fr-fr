---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: afc08b263d75f8a728ce6d64cc7ede0a639df196
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595494"
---
# <span data-ttu-id="8934d-102">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="8934d-102">Trace-Command</span></span>

## <span data-ttu-id="8934d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8934d-103">SYNOPSIS</span></span>
<span data-ttu-id="8934d-104">Configure et démarre un suivi de la commande ou de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8934d-104">Configures and starts a trace of the specified expression or command.</span></span>

## <span data-ttu-id="8934d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="8934d-105">SYNTAX</span></span>

### <span data-ttu-id="8934d-106">expressionSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8934d-106">expressionSet (Default)</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### <span data-ttu-id="8934d-107">commandSet</span><span class="sxs-lookup"><span data-stu-id="8934d-107">commandSet</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## <span data-ttu-id="8934d-108">Description</span><span class="sxs-lookup"><span data-stu-id="8934d-108">DESCRIPTION</span></span>
<span data-ttu-id="8934d-109">L' `Trace-Command` applet de commande configure et démarre une trace de l’expression ou de la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8934d-109">The `Trace-Command` cmdlet configures and starts a trace of the specified expression or command.</span></span>
<span data-ttu-id="8934d-110">Elle fonctionne comme Set-TraceSource, si ce n'est qu'elle s'applique uniquement à la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8934d-110">It works like Set-TraceSource, except that it applies only to the specified command.</span></span>

## <span data-ttu-id="8934d-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="8934d-111">EXAMPLES</span></span>

### <span data-ttu-id="8934d-112">Exemple 1 : suivre le traitement des métadonnées, la liaison de paramètre et une expression</span><span class="sxs-lookup"><span data-stu-id="8934d-112">Example 1: Trace metadata processing, parameter binding, and an expression</span></span>

<span data-ttu-id="8934d-113">Cet exemple démarre une trace du traitement des métadonnées, de la liaison de paramètres et de la création et de la destruction des applets de commande de l' `Get-Process Notepad` expression.</span><span class="sxs-lookup"><span data-stu-id="8934d-113">This example starts a trace of metadata processing, parameter binding, and cmdlet creation and destruction of the `Get-Process Notepad` expression.</span></span>

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

<span data-ttu-id="8934d-114">Elle utilise le paramètre **Name** pour spécifier les sources de suivi, le paramètre **expression** pour spécifier la commande et le paramètre **PSHost** pour envoyer la sortie vers la console.</span><span class="sxs-lookup"><span data-stu-id="8934d-114">It uses the **Name** parameter to specify the trace sources, the **Expression** parameter to specify the command, and the **PSHost** parameter to send the output to the console.</span></span> <span data-ttu-id="8934d-115">Comme elle ne spécifie pas d’options de suivi ni d’options d’écouteur, la commande utilise les valeurs par défaut :</span><span class="sxs-lookup"><span data-stu-id="8934d-115">Because it does not specify any tracing options or listener options, the command uses the defaults:</span></span>

- <span data-ttu-id="8934d-116">Tout pour les options de suivi</span><span class="sxs-lookup"><span data-stu-id="8934d-116">All for the tracing options</span></span>
- <span data-ttu-id="8934d-117">Aucun pour les options d’écouteur</span><span class="sxs-lookup"><span data-stu-id="8934d-117">None for the listener options</span></span>

### <span data-ttu-id="8934d-118">Exemple 2 : suivre les actions des opérations ParameterBinding</span><span class="sxs-lookup"><span data-stu-id="8934d-118">Example 2: Trace the actions of ParameterBinding operations</span></span>

<span data-ttu-id="8934d-119">Cet exemple effectue le suivi des actions des opérations **ParameterBinding** de PowerShell pendant qu’il traite une `Get-Alias` expression qui accepte les entrées du pipeline.</span><span class="sxs-lookup"><span data-stu-id="8934d-119">This example traces the actions of the **ParameterBinding** operations of PowerShell while it processes a `Get-Alias` expression that takes input from the pipeline.</span></span>

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

<span data-ttu-id="8934d-120">Dans `Trace-Command` , le paramètre **InputObject** passe un objet à l’expression en cours de traitement au cours de la trace.</span><span class="sxs-lookup"><span data-stu-id="8934d-120">In `Trace-Command`, the **InputObject** parameter passes an object to the expression that is being processed during the trace.</span></span>

<span data-ttu-id="8934d-121">La première commande stocke la chaîne `i*` dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="8934d-121">The first command stores the string `i*` in the `$A` variable.</span></span> <span data-ttu-id="8934d-122">La deuxième commande utilise l' `Trace-Command` applet de commande avec la source de suivi ParameterBinding.</span><span class="sxs-lookup"><span data-stu-id="8934d-122">The second command uses the `Trace-Command` cmdlet with the ParameterBinding trace source.</span></span> <span data-ttu-id="8934d-123">Le paramètre **PSHost** envoie la sortie vers la console.</span><span class="sxs-lookup"><span data-stu-id="8934d-123">The **PSHost** parameter sends the output to the console.</span></span>

<span data-ttu-id="8934d-124">L’expression en cours de traitement est `Get-Alias $Input` , où la `$Input` variable est associée au paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="8934d-124">The expression being processed is `Get-Alias $Input`, where the `$Input` variable is associated with the **InputObject** parameter.</span></span> <span data-ttu-id="8934d-125">Le paramètre **InputObject** passe la variable `$A` à l’expression.</span><span class="sxs-lookup"><span data-stu-id="8934d-125">The **InputObject** parameter passes the variable `$A` to the expression.</span></span> <span data-ttu-id="8934d-126">En effet, la commande en cours de traitement pendant la trace est `Get-Alias -InputObject $A" or "$A | Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="8934d-126">In effect, the command being processed during the trace is `Get-Alias -InputObject $A" or "$A | Get-Alias`.</span></span>

## <span data-ttu-id="8934d-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8934d-127">PARAMETERS</span></span>

### <span data-ttu-id="8934d-128">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="8934d-128">-ArgumentList</span></span>

<span data-ttu-id="8934d-129">Spécifie les paramètres et les valeurs de paramètre pour la commande faisant l'objet d'un suivi.</span><span class="sxs-lookup"><span data-stu-id="8934d-129">Specifies the parameters and parameter values for the command being traced.</span></span> <span data-ttu-id="8934d-130">L'alias d'**ArgumentList** est **Args**.</span><span class="sxs-lookup"><span data-stu-id="8934d-130">The alias for **ArgumentList** is **Args**.</span></span> <span data-ttu-id="8934d-131">Cette fonctionnalité est particulièrement utile pour déboguer des paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="8934d-131">This feature is especially useful for debugging dynamic parameters.</span></span>

<span data-ttu-id="8934d-132">Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="8934d-132">For more information about the behavior of **ArgumentList**, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-133">-Command</span><span class="sxs-lookup"><span data-stu-id="8934d-133">-Command</span></span>

<span data-ttu-id="8934d-134">Spécifie une commande qui est en cours de traitement au cours du suivi.</span><span class="sxs-lookup"><span data-stu-id="8934d-134">Specifies a command that is being processed during the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-135">-Débogueur</span><span class="sxs-lookup"><span data-stu-id="8934d-135">-Debugger</span></span>

<span data-ttu-id="8934d-136">Indique que l’applet de commande envoie la sortie de trace au débogueur.</span><span class="sxs-lookup"><span data-stu-id="8934d-136">Indicates that the cmdlet sends the trace output to the debugger.</span></span> <span data-ttu-id="8934d-137">Vous pouvez afficher la sortie dans n'importe quel débogueur en mode noyau ou en mode utilisateur, ou dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8934d-137">You can view the output in any user-mode or kernel mode debugger or in Visual Studio.</span></span> <span data-ttu-id="8934d-138">Ce paramètre sélectionne également l'écouteur de suivi par défaut.</span><span class="sxs-lookup"><span data-stu-id="8934d-138">This parameter also selects the default trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-139">-Expression</span><span class="sxs-lookup"><span data-stu-id="8934d-139">-Expression</span></span>

<span data-ttu-id="8934d-140">Spécifie l'expression qui est en cours de traitement au cours du suivi.</span><span class="sxs-lookup"><span data-stu-id="8934d-140">Specifies the expression that is being processed during the trace.</span></span> <span data-ttu-id="8934d-141">Mettez l’expression entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="8934d-141">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-142">-FilePath</span><span class="sxs-lookup"><span data-stu-id="8934d-142">-FilePath</span></span>

<span data-ttu-id="8934d-143">Spécifie un fichier auquel l’applet de commande envoie la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="8934d-143">Specifies a file that the cmdlet sends the trace output to.</span></span> <span data-ttu-id="8934d-144">Ce paramètre sélectionne également l'écouteur de suivi de fichier.</span><span class="sxs-lookup"><span data-stu-id="8934d-144">This parameter also selects the file trace listener.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-145">-Force</span><span class="sxs-lookup"><span data-stu-id="8934d-145">-Force</span></span>

<span data-ttu-id="8934d-146">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8934d-146">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="8934d-147">Utilisé avec le paramètre **filePath** .</span><span class="sxs-lookup"><span data-stu-id="8934d-147">Used with the **FilePath** parameter.</span></span> <span data-ttu-id="8934d-148">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8934d-148">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-149">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8934d-149">-InputObject</span></span>

<span data-ttu-id="8934d-150">Spécifie l’entrée de l’expression en cours de traitement au cours de la trace.</span><span class="sxs-lookup"><span data-stu-id="8934d-150">Specifies input to the expression that is being processed during the trace.</span></span> <span data-ttu-id="8934d-151">Vous pouvez entrer une variable qui représente l'entrée que l'expression accepte ou passer un objet via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8934d-151">You can enter a variable that represents the input that the expression accepts, or pass an object through the pipeline.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-152">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="8934d-152">-ListenerOption</span></span>

<span data-ttu-id="8934d-153">Spécifie des données facultatives pour le préfixe de chaque message de trace dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="8934d-153">Specifies optional data to the prefix of each trace message in the output.</span></span> <span data-ttu-id="8934d-154">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="8934d-154">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8934d-155">None</span><span class="sxs-lookup"><span data-stu-id="8934d-155">None</span></span>
- <span data-ttu-id="8934d-156">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="8934d-156">LogicalOperationStack</span></span>
- <span data-ttu-id="8934d-157">DateTime</span><span class="sxs-lookup"><span data-stu-id="8934d-157">DateTime</span></span>
- <span data-ttu-id="8934d-158">Timestamp</span><span class="sxs-lookup"><span data-stu-id="8934d-158">Timestamp</span></span>
- <span data-ttu-id="8934d-159">ProcessId</span><span class="sxs-lookup"><span data-stu-id="8934d-159">ProcessId</span></span>
- <span data-ttu-id="8934d-160">ThreadId</span><span class="sxs-lookup"><span data-stu-id="8934d-160">ThreadId</span></span>
- <span data-ttu-id="8934d-161">Pile des appels</span><span class="sxs-lookup"><span data-stu-id="8934d-161">Callstack</span></span>

<span data-ttu-id="8934d-162">**None** est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8934d-162">**None** is the default.</span></span>

<span data-ttu-id="8934d-163">Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "ThreadID,ProcessID".</span><span class="sxs-lookup"><span data-stu-id="8934d-163">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-164">-Name</span><span class="sxs-lookup"><span data-stu-id="8934d-164">-Name</span></span>

<span data-ttu-id="8934d-165">Spécifie un tableau de composants PowerShell suivis.</span><span class="sxs-lookup"><span data-stu-id="8934d-165">Specifies an array of PowerShell components that are traced.</span></span> <span data-ttu-id="8934d-166">Entrez le nom de la source de suivi de chaque composant.</span><span class="sxs-lookup"><span data-stu-id="8934d-166">Enter the name of the trace source of each component.</span></span> <span data-ttu-id="8934d-167">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="8934d-167">Wildcards are permitted.</span></span> <span data-ttu-id="8934d-168">Pour rechercher les sources de suivi sur votre ordinateur, tapez `Get-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="8934d-168">To find the trace sources on your computer, type `Get-TraceSource`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-169">-Option</span><span class="sxs-lookup"><span data-stu-id="8934d-169">-Option</span></span>

<span data-ttu-id="8934d-170">Détermine le type des événements qui font l'objet d'un suivi.</span><span class="sxs-lookup"><span data-stu-id="8934d-170">Determines the type of events that are traced.</span></span> <span data-ttu-id="8934d-171">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="8934d-171">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8934d-172">None</span><span class="sxs-lookup"><span data-stu-id="8934d-172">None</span></span>
- <span data-ttu-id="8934d-173">Constructeur</span><span class="sxs-lookup"><span data-stu-id="8934d-173">Constructor</span></span>
- <span data-ttu-id="8934d-174">Dispose</span><span class="sxs-lookup"><span data-stu-id="8934d-174">Dispose</span></span>
- <span data-ttu-id="8934d-175">Finaliseur</span><span class="sxs-lookup"><span data-stu-id="8934d-175">Finalizer</span></span>
- <span data-ttu-id="8934d-176">Méthode</span><span class="sxs-lookup"><span data-stu-id="8934d-176">Method</span></span>
- <span data-ttu-id="8934d-177">Propriété</span><span class="sxs-lookup"><span data-stu-id="8934d-177">Property</span></span>
- <span data-ttu-id="8934d-178">Délégués</span><span class="sxs-lookup"><span data-stu-id="8934d-178">Delegates</span></span>
- <span data-ttu-id="8934d-179">Événements</span><span class="sxs-lookup"><span data-stu-id="8934d-179">Events</span></span>
- <span data-ttu-id="8934d-180">Exception</span><span class="sxs-lookup"><span data-stu-id="8934d-180">Exception</span></span>
- <span data-ttu-id="8934d-181">Verrouillage</span><span class="sxs-lookup"><span data-stu-id="8934d-181">Lock</span></span>
- <span data-ttu-id="8934d-182">Error</span><span class="sxs-lookup"><span data-stu-id="8934d-182">Error</span></span>
- <span data-ttu-id="8934d-183">Erreurs</span><span class="sxs-lookup"><span data-stu-id="8934d-183">Errors</span></span>
- <span data-ttu-id="8934d-184">Avertissement</span><span class="sxs-lookup"><span data-stu-id="8934d-184">Warning</span></span>
- <span data-ttu-id="8934d-185">Commentaires</span><span class="sxs-lookup"><span data-stu-id="8934d-185">Verbose</span></span>
- <span data-ttu-id="8934d-186">WriteLine</span><span class="sxs-lookup"><span data-stu-id="8934d-186">WriteLine</span></span>
- <span data-ttu-id="8934d-187">Données</span><span class="sxs-lookup"><span data-stu-id="8934d-187">Data</span></span>
- <span data-ttu-id="8934d-188">Scope (Étendue)</span><span class="sxs-lookup"><span data-stu-id="8934d-188">Scope</span></span>
- <span data-ttu-id="8934d-189">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="8934d-189">ExecutionFlow</span></span>
- <span data-ttu-id="8934d-190">Assert</span><span class="sxs-lookup"><span data-stu-id="8934d-190">Assert</span></span>
- <span data-ttu-id="8934d-191">Tous</span><span class="sxs-lookup"><span data-stu-id="8934d-191">All</span></span>

<span data-ttu-id="8934d-192">« All » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8934d-192">All is the default.</span></span>

<span data-ttu-id="8934d-193">Les valeurs suivantes sont des combinaisons d'autres valeurs :</span><span class="sxs-lookup"><span data-stu-id="8934d-193">The following values are combinations of other values:</span></span>

- <span data-ttu-id="8934d-194">ExecutionFlow : (Constructor, dispose, Finalizer, Method, Delegates, Events et Scope)</span><span class="sxs-lookup"><span data-stu-id="8934d-194">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="8934d-195">Données : (Constructor, dispose, Finalizer, Property, verbose et WriteLine)</span><span class="sxs-lookup"><span data-stu-id="8934d-195">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="8934d-196">Erreurs : (erreur et exception).</span><span class="sxs-lookup"><span data-stu-id="8934d-196">Errors: (Error and Exception).</span></span>

<span data-ttu-id="8934d-197">Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "Constructor,Dispose".</span><span class="sxs-lookup"><span data-stu-id="8934d-197">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-198">-PSHost</span><span class="sxs-lookup"><span data-stu-id="8934d-198">-PSHost</span></span>

<span data-ttu-id="8934d-199">Indique que l’applet de commande envoie la sortie de suivi à l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8934d-199">Indicates that the cmdlet sends the trace output to the PowerShell host.</span></span> <span data-ttu-id="8934d-200">Ce paramètre sélectionne également l'écouteur de suivi de PSHost.</span><span class="sxs-lookup"><span data-stu-id="8934d-200">This parameter also selects the PSHost trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8934d-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8934d-201">CommonParameters</span></span>

<span data-ttu-id="8934d-202">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8934d-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8934d-203">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8934d-203">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8934d-204">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="8934d-204">INPUTS</span></span>

### <span data-ttu-id="8934d-205">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8934d-205">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8934d-206">Vous pouvez diriger les objets qui représentent l’entrée vers l’expression vers `Trace-Command` .</span><span class="sxs-lookup"><span data-stu-id="8934d-206">You can pipe objects that represent input to the expression to `Trace-Command`.</span></span>

## <span data-ttu-id="8934d-207">SORTIES</span><span class="sxs-lookup"><span data-stu-id="8934d-207">OUTPUTS</span></span>

### <span data-ttu-id="8934d-208">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8934d-208">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8934d-209">Retourne le suivi de la commande dans le flux de débogage.</span><span class="sxs-lookup"><span data-stu-id="8934d-209">Returns the command trace in the debug stream.</span></span>

## <span data-ttu-id="8934d-210">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="8934d-210">NOTES</span></span>

- <span data-ttu-id="8934d-211">Le suivi est une méthode que les développeurs utilisent pour déboguer et affiner les programmes.</span><span class="sxs-lookup"><span data-stu-id="8934d-211">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="8934d-212">Pendant le suivi, le programme génère des messages détaillés sur chaque étape du traitement interne.</span><span class="sxs-lookup"><span data-stu-id="8934d-212">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

- <span data-ttu-id="8934d-213">Les applets de commande PowerShell Tracing sont conçues pour aider les développeurs PowerShell, mais elles sont disponibles pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8934d-213">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span> <span data-ttu-id="8934d-214">Elles vous permettent de surveiller quasiment chaque aspect de la fonctionnalité de l'interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="8934d-214">They let you monitor nearly every aspect of the functionality of the shell.</span></span>

- <span data-ttu-id="8934d-215">Pour rechercher les composants PowerShell activés pour le suivi, tapez `Get-Help Get-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="8934d-215">To find the PowerShell components that are enabled for tracing, type `Get-Help Get-TraceSource`.</span></span>

  <span data-ttu-id="8934d-216">Une source de suivi est la partie de chaque composant PowerShell qui gère le suivi et génère des messages de suivi pour le composant.</span><span class="sxs-lookup"><span data-stu-id="8934d-216">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span> <span data-ttu-id="8934d-217">Pour suivre un composant, vous identifiez sa source de suivi.</span><span class="sxs-lookup"><span data-stu-id="8934d-217">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="8934d-218">Un écouteur de suivi reçoit la sortie de la trace et l’affiche à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8934d-218">A trace listener receives the output of the trace and displays it to the user.</span></span> <span data-ttu-id="8934d-219">Vous pouvez choisir d’envoyer les données de trace à un débogueur en mode utilisateur ou en mode noyau, à l’hôte ou à la console, à un fichier ou à un écouteur personnalisé dérivé de la classe **System. Diagnostics. TraceListener** .</span><span class="sxs-lookup"><span data-stu-id="8934d-219">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the host or console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

- <span data-ttu-id="8934d-220">Lorsque vous utilisez le jeu de paramètres commandSet, PowerShell traite la commande comme elle serait traitée dans un pipeline.</span><span class="sxs-lookup"><span data-stu-id="8934d-220">When you use the commandSet parameter set, PowerShell processes the command just as it would be processed in a pipeline.</span></span> <span data-ttu-id="8934d-221">Par exemple, la découverte de commande n'est pas répétée pour chaque objet entrant.</span><span class="sxs-lookup"><span data-stu-id="8934d-221">For example, command discovery is not repeated for each incoming object.</span></span>

- <span data-ttu-id="8934d-222">Les noms des paramètres **Name**, **expression**, **option** et **Command** sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="8934d-222">The names of the **Name**, **Expression**, **Option**, and **Command** parameters are optional.</span></span> <span data-ttu-id="8934d-223">Si vous omettez les noms de paramètres, les valeurs des paramètres sans nom doivent apparaître dans cet ordre : **nom**, **expression**, **option** ou **nom**, **commande**, **option**.</span><span class="sxs-lookup"><span data-stu-id="8934d-223">If you omit the parameter names, the unnamed parameter values must appear in this order: **Name**, **Expression**, **Option** or **Name**, **Command**, **Option**.</span></span> <span data-ttu-id="8934d-224">Si vous incluez les noms de paramètres, les paramètres peuvent apparaître dans tout ordre.</span><span class="sxs-lookup"><span data-stu-id="8934d-224">If you include the parameter names, the parameters can appear in any order.</span></span>

## <span data-ttu-id="8934d-225">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="8934d-225">RELATED LINKS</span></span>

[<span data-ttu-id="8934d-226">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="8934d-226">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="8934d-227">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="8934d-227">Measure-Command</span></span>](Measure-Command.md)

[<span data-ttu-id="8934d-228">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="8934d-228">Set-TraceSource</span></span>](Set-TraceSource.md)

