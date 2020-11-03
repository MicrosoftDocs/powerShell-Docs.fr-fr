---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: 00c267b5db630944dbccd35a30ea614d13193af8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203113"
---
# <span data-ttu-id="13eb4-103">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="13eb4-103">Trace-Command</span></span>

## <span data-ttu-id="13eb4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="13eb4-104">SYNOPSIS</span></span>
<span data-ttu-id="13eb4-105">Configure et démarre un suivi de la commande ou de l'expression spécifiée.</span><span class="sxs-lookup"><span data-stu-id="13eb4-105">Configures and starts a trace of the specified expression or command.</span></span>

## <span data-ttu-id="13eb4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="13eb4-106">SYNTAX</span></span>

### <span data-ttu-id="13eb4-107">expressionSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="13eb4-107">expressionSet (Default)</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### <span data-ttu-id="13eb4-108">commandSet</span><span class="sxs-lookup"><span data-stu-id="13eb4-108">commandSet</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## <span data-ttu-id="13eb4-109">Description</span><span class="sxs-lookup"><span data-stu-id="13eb4-109">DESCRIPTION</span></span>
<span data-ttu-id="13eb4-110">L' `Trace-Command` applet de commande configure et démarre une trace de l’expression ou de la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="13eb4-110">The `Trace-Command` cmdlet configures and starts a trace of the specified expression or command.</span></span>
<span data-ttu-id="13eb4-111">Elle fonctionne comme Set-TraceSource, si ce n'est qu'elle s'applique uniquement à la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="13eb4-111">It works like Set-TraceSource, except that it applies only to the specified command.</span></span>

## <span data-ttu-id="13eb4-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="13eb4-112">EXAMPLES</span></span>

### <span data-ttu-id="13eb4-113">Exemple 1 : suivre le traitement des métadonnées, la liaison de paramètre et une expression</span><span class="sxs-lookup"><span data-stu-id="13eb4-113">Example 1: Trace metadata processing, parameter binding, and an expression</span></span>

<span data-ttu-id="13eb4-114">Cet exemple démarre une trace du traitement des métadonnées, de la liaison de paramètres et de la création et de la destruction des applets de commande de l' `Get-Process Notepad` expression.</span><span class="sxs-lookup"><span data-stu-id="13eb4-114">This example starts a trace of metadata processing, parameter binding, and cmdlet creation and destruction of the `Get-Process Notepad` expression.</span></span>

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

<span data-ttu-id="13eb4-115">Elle utilise le paramètre **Name** pour spécifier les sources de suivi, le paramètre **expression** pour spécifier la commande et le paramètre **PSHost** pour envoyer la sortie vers la console.</span><span class="sxs-lookup"><span data-stu-id="13eb4-115">It uses the **Name** parameter to specify the trace sources, the **Expression** parameter to specify the command, and the **PSHost** parameter to send the output to the console.</span></span> <span data-ttu-id="13eb4-116">Comme elle ne spécifie pas d’options de suivi ni d’options d’écouteur, la commande utilise les valeurs par défaut :</span><span class="sxs-lookup"><span data-stu-id="13eb4-116">Because it does not specify any tracing options or listener options, the command uses the defaults:</span></span>

- <span data-ttu-id="13eb4-117">Tout pour les options de suivi</span><span class="sxs-lookup"><span data-stu-id="13eb4-117">All for the tracing options</span></span>
- <span data-ttu-id="13eb4-118">Aucun pour les options d’écouteur</span><span class="sxs-lookup"><span data-stu-id="13eb4-118">None for the listener options</span></span>

### <span data-ttu-id="13eb4-119">Exemple 2 : suivre les actions des opérations ParameterBinding</span><span class="sxs-lookup"><span data-stu-id="13eb4-119">Example 2: Trace the actions of ParameterBinding operations</span></span>

<span data-ttu-id="13eb4-120">Cet exemple effectue le suivi des actions des opérations **ParameterBinding** de PowerShell pendant qu’il traite une `Get-Alias` expression qui accepte les entrées du pipeline.</span><span class="sxs-lookup"><span data-stu-id="13eb4-120">This example traces the actions of the **ParameterBinding** operations of PowerShell while it processes a `Get-Alias` expression that takes input from the pipeline.</span></span>

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

<span data-ttu-id="13eb4-121">Dans `Trace-Command` , le paramètre **InputObject** passe un objet à l’expression en cours de traitement au cours de la trace.</span><span class="sxs-lookup"><span data-stu-id="13eb4-121">In `Trace-Command`, the **InputObject** parameter passes an object to the expression that is being processed during the trace.</span></span>

<span data-ttu-id="13eb4-122">La première commande stocke la chaîne `i*` dans la `$A` variable.</span><span class="sxs-lookup"><span data-stu-id="13eb4-122">The first command stores the string `i*` in the `$A` variable.</span></span> <span data-ttu-id="13eb4-123">La deuxième commande utilise l' `Trace-Command` applet de commande avec la source de suivi ParameterBinding.</span><span class="sxs-lookup"><span data-stu-id="13eb4-123">The second command uses the `Trace-Command` cmdlet with the ParameterBinding trace source.</span></span> <span data-ttu-id="13eb4-124">Le paramètre **PSHost** envoie la sortie vers la console.</span><span class="sxs-lookup"><span data-stu-id="13eb4-124">The **PSHost** parameter sends the output to the console.</span></span>

<span data-ttu-id="13eb4-125">L’expression en cours de traitement est `Get-Alias $Input` , où la `$Input` variable est associée au paramètre **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="13eb4-125">The expression being processed is `Get-Alias $Input`, where the `$Input` variable is associated with the **InputObject** parameter.</span></span> <span data-ttu-id="13eb4-126">Le paramètre **InputObject** passe la variable `$A` à l’expression.</span><span class="sxs-lookup"><span data-stu-id="13eb4-126">The **InputObject** parameter passes the variable `$A` to the expression.</span></span> <span data-ttu-id="13eb4-127">En effet, la commande en cours de traitement pendant la trace est `Get-Alias -InputObject $A" or "$A | Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="13eb4-127">In effect, the command being processed during the trace is `Get-Alias -InputObject $A" or "$A | Get-Alias`.</span></span>

## <span data-ttu-id="13eb4-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="13eb4-128">PARAMETERS</span></span>

### <span data-ttu-id="13eb4-129">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="13eb4-129">-ArgumentList</span></span>

<span data-ttu-id="13eb4-130">Spécifie les paramètres et les valeurs de paramètre pour la commande faisant l'objet d'un suivi.</span><span class="sxs-lookup"><span data-stu-id="13eb4-130">Specifies the parameters and parameter values for the command being traced.</span></span> <span data-ttu-id="13eb4-131">L'alias d' **ArgumentList** est **Args** .</span><span class="sxs-lookup"><span data-stu-id="13eb4-131">The alias for **ArgumentList** is **Args** .</span></span> <span data-ttu-id="13eb4-132">Cette fonctionnalité est particulièrement utile pour déboguer des paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="13eb4-132">This feature is especially useful for debugging dynamic parameters.</span></span>

<span data-ttu-id="13eb4-133">Pour plus d’informations sur le comportement de **argumentlist** , consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="13eb4-133">For more information about the behavior of **ArgumentList** , see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="13eb4-134">-Command</span><span class="sxs-lookup"><span data-stu-id="13eb4-134">-Command</span></span>

<span data-ttu-id="13eb4-135">Spécifie une commande qui est en cours de traitement au cours du suivi.</span><span class="sxs-lookup"><span data-stu-id="13eb4-135">Specifies a command that is being processed during the trace.</span></span>

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

### <span data-ttu-id="13eb4-136">-Débogueur</span><span class="sxs-lookup"><span data-stu-id="13eb4-136">-Debugger</span></span>

<span data-ttu-id="13eb4-137">Indique que l’applet de commande envoie la sortie de trace au débogueur.</span><span class="sxs-lookup"><span data-stu-id="13eb4-137">Indicates that the cmdlet sends the trace output to the debugger.</span></span> <span data-ttu-id="13eb4-138">Vous pouvez afficher la sortie dans n'importe quel débogueur en mode noyau ou en mode utilisateur, ou dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="13eb4-138">You can view the output in any user-mode or kernel mode debugger or in Visual Studio.</span></span> <span data-ttu-id="13eb4-139">Ce paramètre sélectionne également l'écouteur de suivi par défaut.</span><span class="sxs-lookup"><span data-stu-id="13eb4-139">This parameter also selects the default trace listener.</span></span>

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

### <span data-ttu-id="13eb4-140">-Expression</span><span class="sxs-lookup"><span data-stu-id="13eb4-140">-Expression</span></span>

<span data-ttu-id="13eb4-141">Spécifie l'expression qui est en cours de traitement au cours du suivi.</span><span class="sxs-lookup"><span data-stu-id="13eb4-141">Specifies the expression that is being processed during the trace.</span></span> <span data-ttu-id="13eb4-142">Mettez l’expression entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="13eb4-142">Enclose the expression in braces (`{}`).</span></span>

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

### <span data-ttu-id="13eb4-143">-FilePath</span><span class="sxs-lookup"><span data-stu-id="13eb4-143">-FilePath</span></span>

<span data-ttu-id="13eb4-144">Spécifie un fichier auquel l’applet de commande envoie la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="13eb4-144">Specifies a file that the cmdlet sends the trace output to.</span></span> <span data-ttu-id="13eb4-145">Ce paramètre sélectionne également l'écouteur de suivi de fichier.</span><span class="sxs-lookup"><span data-stu-id="13eb4-145">This parameter also selects the file trace listener.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13eb4-146">-Force</span><span class="sxs-lookup"><span data-stu-id="13eb4-146">-Force</span></span>

<span data-ttu-id="13eb4-147">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="13eb4-147">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="13eb4-148">Utilisé avec le paramètre **filePath** .</span><span class="sxs-lookup"><span data-stu-id="13eb4-148">Used with the **FilePath** parameter.</span></span> <span data-ttu-id="13eb4-149">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="13eb4-149">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="13eb4-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="13eb4-150">-InputObject</span></span>

<span data-ttu-id="13eb4-151">Spécifie l’entrée de l’expression en cours de traitement au cours de la trace.</span><span class="sxs-lookup"><span data-stu-id="13eb4-151">Specifies input to the expression that is being processed during the trace.</span></span> <span data-ttu-id="13eb4-152">Vous pouvez entrer une variable qui représente l'entrée que l'expression accepte ou passer un objet via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="13eb4-152">You can enter a variable that represents the input that the expression accepts, or pass an object through the pipeline.</span></span>

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

### <span data-ttu-id="13eb4-153">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="13eb4-153">-ListenerOption</span></span>

<span data-ttu-id="13eb4-154">Spécifie des données facultatives pour le préfixe de chaque message de trace dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="13eb4-154">Specifies optional data to the prefix of each trace message in the output.</span></span> <span data-ttu-id="13eb4-155">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="13eb4-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="13eb4-156">Aucun</span><span class="sxs-lookup"><span data-stu-id="13eb4-156">None</span></span>
- <span data-ttu-id="13eb4-157">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="13eb4-157">LogicalOperationStack</span></span>
- <span data-ttu-id="13eb4-158">DateTime</span><span class="sxs-lookup"><span data-stu-id="13eb4-158">DateTime</span></span>
- <span data-ttu-id="13eb4-159">Timestamp</span><span class="sxs-lookup"><span data-stu-id="13eb4-159">Timestamp</span></span>
- <span data-ttu-id="13eb4-160">ProcessId</span><span class="sxs-lookup"><span data-stu-id="13eb4-160">ProcessId</span></span>
- <span data-ttu-id="13eb4-161">ThreadId</span><span class="sxs-lookup"><span data-stu-id="13eb4-161">ThreadId</span></span>
- <span data-ttu-id="13eb4-162">Pile des appels</span><span class="sxs-lookup"><span data-stu-id="13eb4-162">Callstack</span></span>

<span data-ttu-id="13eb4-163">**None** est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="13eb4-163">**None** is the default.</span></span>

<span data-ttu-id="13eb4-164">Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "ThreadID,ProcessID".</span><span class="sxs-lookup"><span data-stu-id="13eb4-164">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

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

### <span data-ttu-id="13eb4-165">-Name</span><span class="sxs-lookup"><span data-stu-id="13eb4-165">-Name</span></span>

<span data-ttu-id="13eb4-166">Spécifie un tableau de composants PowerShell suivis.</span><span class="sxs-lookup"><span data-stu-id="13eb4-166">Specifies an array of PowerShell components that are traced.</span></span> <span data-ttu-id="13eb4-167">Entrez le nom de la source de suivi de chaque composant.</span><span class="sxs-lookup"><span data-stu-id="13eb4-167">Enter the name of the trace source of each component.</span></span> <span data-ttu-id="13eb4-168">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="13eb4-168">Wildcards are permitted.</span></span> <span data-ttu-id="13eb4-169">Pour rechercher les sources de suivi sur votre ordinateur, tapez `Get-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="13eb4-169">To find the trace sources on your computer, type `Get-TraceSource`.</span></span>

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

### <span data-ttu-id="13eb4-170">-Option</span><span class="sxs-lookup"><span data-stu-id="13eb4-170">-Option</span></span>

<span data-ttu-id="13eb4-171">Détermine le type des événements qui font l'objet d'un suivi.</span><span class="sxs-lookup"><span data-stu-id="13eb4-171">Determines the type of events that are traced.</span></span> <span data-ttu-id="13eb4-172">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="13eb4-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="13eb4-173">Aucun</span><span class="sxs-lookup"><span data-stu-id="13eb4-173">None</span></span>
- <span data-ttu-id="13eb4-174">Constructeur</span><span class="sxs-lookup"><span data-stu-id="13eb4-174">Constructor</span></span>
- <span data-ttu-id="13eb4-175">Dispose</span><span class="sxs-lookup"><span data-stu-id="13eb4-175">Dispose</span></span>
- <span data-ttu-id="13eb4-176">Finaliseur</span><span class="sxs-lookup"><span data-stu-id="13eb4-176">Finalizer</span></span>
- <span data-ttu-id="13eb4-177">Méthode</span><span class="sxs-lookup"><span data-stu-id="13eb4-177">Method</span></span>
- <span data-ttu-id="13eb4-178">Propriété</span><span class="sxs-lookup"><span data-stu-id="13eb4-178">Property</span></span>
- <span data-ttu-id="13eb4-179">Délégués</span><span class="sxs-lookup"><span data-stu-id="13eb4-179">Delegates</span></span>
- <span data-ttu-id="13eb4-180">Événements</span><span class="sxs-lookup"><span data-stu-id="13eb4-180">Events</span></span>
- <span data-ttu-id="13eb4-181">Exception</span><span class="sxs-lookup"><span data-stu-id="13eb4-181">Exception</span></span>
- <span data-ttu-id="13eb4-182">Verrouillage</span><span class="sxs-lookup"><span data-stu-id="13eb4-182">Lock</span></span>
- <span data-ttu-id="13eb4-183">Erreur</span><span class="sxs-lookup"><span data-stu-id="13eb4-183">Error</span></span>
- <span data-ttu-id="13eb4-184">Erreurs</span><span class="sxs-lookup"><span data-stu-id="13eb4-184">Errors</span></span>
- <span data-ttu-id="13eb4-185">Avertissement</span><span class="sxs-lookup"><span data-stu-id="13eb4-185">Warning</span></span>
- <span data-ttu-id="13eb4-186">Commentaires</span><span class="sxs-lookup"><span data-stu-id="13eb4-186">Verbose</span></span>
- <span data-ttu-id="13eb4-187">WriteLine</span><span class="sxs-lookup"><span data-stu-id="13eb4-187">WriteLine</span></span>
- <span data-ttu-id="13eb4-188">Données</span><span class="sxs-lookup"><span data-stu-id="13eb4-188">Data</span></span>
- <span data-ttu-id="13eb4-189">Étendue</span><span class="sxs-lookup"><span data-stu-id="13eb4-189">Scope</span></span>
- <span data-ttu-id="13eb4-190">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="13eb4-190">ExecutionFlow</span></span>
- <span data-ttu-id="13eb4-191">Assert</span><span class="sxs-lookup"><span data-stu-id="13eb4-191">Assert</span></span>
- <span data-ttu-id="13eb4-192">Tous</span><span class="sxs-lookup"><span data-stu-id="13eb4-192">All</span></span>

<span data-ttu-id="13eb4-193">« All » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="13eb4-193">All is the default.</span></span>

<span data-ttu-id="13eb4-194">Les valeurs suivantes sont des combinaisons d'autres valeurs :</span><span class="sxs-lookup"><span data-stu-id="13eb4-194">The following values are combinations of other values:</span></span>

- <span data-ttu-id="13eb4-195">ExecutionFlow : (Constructor, dispose, Finalizer, Method, Delegates, Events et Scope)</span><span class="sxs-lookup"><span data-stu-id="13eb4-195">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="13eb4-196">Données : (Constructor, dispose, Finalizer, Property, verbose et WriteLine)</span><span class="sxs-lookup"><span data-stu-id="13eb4-196">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="13eb4-197">Erreurs : (erreur et exception).</span><span class="sxs-lookup"><span data-stu-id="13eb4-197">Errors: (Error and Exception).</span></span>

<span data-ttu-id="13eb4-198">Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "Constructor,Dispose".</span><span class="sxs-lookup"><span data-stu-id="13eb4-198">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

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

### <span data-ttu-id="13eb4-199">-PSHost</span><span class="sxs-lookup"><span data-stu-id="13eb4-199">-PSHost</span></span>

<span data-ttu-id="13eb4-200">Indique que l’applet de commande envoie la sortie de suivi à l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13eb4-200">Indicates that the cmdlet sends the trace output to the PowerShell host.</span></span> <span data-ttu-id="13eb4-201">Ce paramètre sélectionne également l'écouteur de suivi de PSHost.</span><span class="sxs-lookup"><span data-stu-id="13eb4-201">This parameter also selects the PSHost trace listener.</span></span>

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

### <span data-ttu-id="13eb4-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="13eb4-202">CommonParameters</span></span>

<span data-ttu-id="13eb4-203">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="13eb4-203">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="13eb4-204">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="13eb4-204">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="13eb4-205">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="13eb4-205">INPUTS</span></span>

### <span data-ttu-id="13eb4-206">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="13eb4-206">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="13eb4-207">Vous pouvez diriger les objets qui représentent l’entrée vers l’expression vers `Trace-Command` .</span><span class="sxs-lookup"><span data-stu-id="13eb4-207">You can pipe objects that represent input to the expression to `Trace-Command`.</span></span>

## <span data-ttu-id="13eb4-208">SORTIES</span><span class="sxs-lookup"><span data-stu-id="13eb4-208">OUTPUTS</span></span>

### <span data-ttu-id="13eb4-209">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="13eb4-209">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="13eb4-210">Retourne le suivi de la commande dans le flux de débogage.</span><span class="sxs-lookup"><span data-stu-id="13eb4-210">Returns the command trace in the debug stream.</span></span>

## <span data-ttu-id="13eb4-211">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="13eb4-211">NOTES</span></span>

- <span data-ttu-id="13eb4-212">Le suivi est une méthode que les développeurs utilisent pour déboguer et affiner les programmes.</span><span class="sxs-lookup"><span data-stu-id="13eb4-212">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="13eb4-213">Pendant le suivi, le programme génère des messages détaillés sur chaque étape du traitement interne.</span><span class="sxs-lookup"><span data-stu-id="13eb4-213">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

- <span data-ttu-id="13eb4-214">Les applets de commande PowerShell Tracing sont conçues pour aider les développeurs PowerShell, mais elles sont disponibles pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="13eb4-214">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span> <span data-ttu-id="13eb4-215">Elles vous permettent de surveiller quasiment chaque aspect de la fonctionnalité de l'interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="13eb4-215">They let you monitor nearly every aspect of the functionality of the shell.</span></span>

- <span data-ttu-id="13eb4-216">Pour rechercher les composants PowerShell activés pour le suivi, tapez `Get-Help Get-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="13eb4-216">To find the PowerShell components that are enabled for tracing, type `Get-Help Get-TraceSource`.</span></span>

  <span data-ttu-id="13eb4-217">Une source de suivi est la partie de chaque composant PowerShell qui gère le suivi et génère des messages de suivi pour le composant.</span><span class="sxs-lookup"><span data-stu-id="13eb4-217">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span> <span data-ttu-id="13eb4-218">Pour suivre un composant, vous identifiez sa source de suivi.</span><span class="sxs-lookup"><span data-stu-id="13eb4-218">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="13eb4-219">Un écouteur de suivi reçoit la sortie de la trace et l’affiche à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="13eb4-219">A trace listener receives the output of the trace and displays it to the user.</span></span> <span data-ttu-id="13eb4-220">Vous pouvez choisir d’envoyer les données de trace à un débogueur en mode utilisateur ou en mode noyau, à l’hôte ou à la console, à un fichier ou à un écouteur personnalisé dérivé de la classe **System. Diagnostics. TraceListener** .</span><span class="sxs-lookup"><span data-stu-id="13eb4-220">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the host or console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

- <span data-ttu-id="13eb4-221">Lorsque vous utilisez le jeu de paramètres commandSet, PowerShell traite la commande comme elle serait traitée dans un pipeline.</span><span class="sxs-lookup"><span data-stu-id="13eb4-221">When you use the commandSet parameter set, PowerShell processes the command just as it would be processed in a pipeline.</span></span> <span data-ttu-id="13eb4-222">Par exemple, la découverte de commande n'est pas répétée pour chaque objet entrant.</span><span class="sxs-lookup"><span data-stu-id="13eb4-222">For example, command discovery is not repeated for each incoming object.</span></span>

- <span data-ttu-id="13eb4-223">Les noms des paramètres **Name** , **expression** , **option** et **Command** sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="13eb4-223">The names of the **Name** , **Expression** , **Option** , and **Command** parameters are optional.</span></span> <span data-ttu-id="13eb4-224">Si vous omettez les noms de paramètres, les valeurs des paramètres sans nom doivent apparaître dans cet ordre : **nom** , **expression** , **option** ou **nom** , **commande** , **option** .</span><span class="sxs-lookup"><span data-stu-id="13eb4-224">If you omit the parameter names, the unnamed parameter values must appear in this order: **Name** , **Expression** , **Option** or **Name** , **Command** , **Option** .</span></span> <span data-ttu-id="13eb4-225">Si vous incluez les noms de paramètres, les paramètres peuvent apparaître dans tout ordre.</span><span class="sxs-lookup"><span data-stu-id="13eb4-225">If you include the parameter names, the parameters can appear in any order.</span></span>

## <span data-ttu-id="13eb4-226">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="13eb4-226">RELATED LINKS</span></span>

[<span data-ttu-id="13eb4-227">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="13eb4-227">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="13eb4-228">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="13eb4-228">Measure-Command</span></span>](Measure-Command.md)

[<span data-ttu-id="13eb4-229">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="13eb4-229">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="13eb4-230">Show-Command</span><span class="sxs-lookup"><span data-stu-id="13eb4-230">Show-Command</span></span>](Show-Command.md)
