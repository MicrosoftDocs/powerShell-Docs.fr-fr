---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 6e7fd1c6eb3551906b4dd9d947b5e551cd05d30a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597991"
---
# <span data-ttu-id="a891d-102">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="a891d-102">Set-TraceSource</span></span>

## <span data-ttu-id="a891d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a891d-103">SYNOPSIS</span></span>
<span data-ttu-id="a891d-104">Configure, démarre et arrête un suivi des composants PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a891d-104">Configures, starts, and stops a trace of PowerShell components.</span></span>

## <span data-ttu-id="a891d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="a891d-105">SYNTAX</span></span>

### <span data-ttu-id="a891d-106">optionsSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a891d-106">optionsSet (Default)</span></span>

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="a891d-107">removeAllListenersSet</span><span class="sxs-lookup"><span data-stu-id="a891d-107">removeAllListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="a891d-108">removeFileListenersSet</span><span class="sxs-lookup"><span data-stu-id="a891d-108">removeFileListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="a891d-109">Description</span><span class="sxs-lookup"><span data-stu-id="a891d-109">DESCRIPTION</span></span>

<span data-ttu-id="a891d-110">L’applet de commande **Set-TraceSource** configure, démarre et arrête une trace d’un composant PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a891d-110">The **Set-TraceSource** cmdlet configures, starts, and stops a trace of a PowerShell component.</span></span>
<span data-ttu-id="a891d-111">Vous pouvez l'utiliser pour spécifier quels composants seront tracés et où la sortie du suivi est envoyée.</span><span class="sxs-lookup"><span data-stu-id="a891d-111">You can use it to specify which components will be traced and where the tracing output is sent.</span></span>

## <span data-ttu-id="a891d-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a891d-112">EXAMPLES</span></span>

### <span data-ttu-id="a891d-113">Exemple 1 : tracer le composant ParameterBinding</span><span class="sxs-lookup"><span data-stu-id="a891d-113">Example 1: Trace the ParameterBinding component</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

<span data-ttu-id="a891d-114">Cette commande démarre le suivi pour le composant ParameterBinding de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a891d-114">This command starts tracing for the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="a891d-115">Elle utilise le paramètre *Name* pour spécifier la source de suivi, le paramètre *option* pour sélectionner les événements de trace ExecutionFlow et le paramètre *PSHost* pour sélectionner l’écouteur hôte PowerShell, qui envoie la sortie vers la console.</span><span class="sxs-lookup"><span data-stu-id="a891d-115">It uses the *Name* parameter to specify the trace source, the *Option* parameter to select the ExecutionFlow trace events, and the *PSHost* parameter to select the PowerShell host listener, which sends the output to the console.</span></span>
<span data-ttu-id="a891d-116">Le paramètre *ListenerOption* ajoute les valeurs ProcessId et timestamp au préfixe du message de suivi.</span><span class="sxs-lookup"><span data-stu-id="a891d-116">The *ListenerOption* parameter adds the ProcessID and TimeStamp values to the trace message prefix.</span></span>

### <span data-ttu-id="a891d-117">Exemple 2 : arrêter une trace</span><span class="sxs-lookup"><span data-stu-id="a891d-117">Example 2: Stop a trace</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

<span data-ttu-id="a891d-118">Cette commande arrête la trace du composant ParameterBinding de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a891d-118">This command stops the trace of the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="a891d-119">Elle utilise le paramètre *Name* pour identifier le composant qui a été suivi et le paramètre *RemoveListener* pour identifier l’écouteur de suivi.</span><span class="sxs-lookup"><span data-stu-id="a891d-119">It uses the *Name* parameter to identify the component that was being traced and the *RemoveListener* parameter to identify the trace listener.</span></span>

## <span data-ttu-id="a891d-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a891d-120">PARAMETERS</span></span>

### <span data-ttu-id="a891d-121">-Débogueur</span><span class="sxs-lookup"><span data-stu-id="a891d-121">-Debugger</span></span>

<span data-ttu-id="a891d-122">Indique que l’applet de commande envoie la sortie de trace au débogueur.</span><span class="sxs-lookup"><span data-stu-id="a891d-122">Indicates that the cmdlet sends the trace output to the debugger.</span></span>
<span data-ttu-id="a891d-123">Vous pouvez afficher la sortie dans n'importe quel débogueur en mode noyau ou en mode utilisateur, ou bien dans Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a891d-123">You can view the output in any user-mode or kernel mode debugger or in Microsoft Visual Studio.</span></span>
<span data-ttu-id="a891d-124">Ce paramètre sélectionne également l'écouteur de suivi par défaut.</span><span class="sxs-lookup"><span data-stu-id="a891d-124">This parameter also selects the default trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a891d-125">-FilePath</span><span class="sxs-lookup"><span data-stu-id="a891d-125">-FilePath</span></span>

<span data-ttu-id="a891d-126">Spécifie un fichier auquel cette applet de commande envoie la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="a891d-126">Specifies a file that this cmdlet sends the trace output to.</span></span>
<span data-ttu-id="a891d-127">Ce paramètre sélectionne également l'écouteur de suivi de fichier.</span><span class="sxs-lookup"><span data-stu-id="a891d-127">This parameter also selects the file trace listener.</span></span>
<span data-ttu-id="a891d-128">Si vous utilisez ce paramètre pour démarrer le suivi, utilisez le paramètre *RemoveFileListener* pour arrêter la trace.</span><span class="sxs-lookup"><span data-stu-id="a891d-128">If you use this parameter to start the trace, use the *RemoveFileListener* parameter to stop the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a891d-129">-Force</span><span class="sxs-lookup"><span data-stu-id="a891d-129">-Force</span></span>

<span data-ttu-id="a891d-130">Indique que l’applet de commande remplace un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="a891d-130">Indicates that the cmdlet overwrites a read-only file.</span></span>
<span data-ttu-id="a891d-131">Utilisez avec le paramètre *filePath* .</span><span class="sxs-lookup"><span data-stu-id="a891d-131">Use with the *FilePath* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a891d-132">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="a891d-132">-ListenerOption</span></span>

<span data-ttu-id="a891d-133">Spécifie des données facultatives pour le préfixe de chaque message de trace dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="a891d-133">Specifies optional data to the prefix of each trace message in the output.</span></span>
<span data-ttu-id="a891d-134">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="a891d-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a891d-135">None</span><span class="sxs-lookup"><span data-stu-id="a891d-135">None</span></span>
- <span data-ttu-id="a891d-136">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="a891d-136">LogicalOperationStack</span></span>
- <span data-ttu-id="a891d-137">DateTime</span><span class="sxs-lookup"><span data-stu-id="a891d-137">DateTime</span></span>
- <span data-ttu-id="a891d-138">Timestamp</span><span class="sxs-lookup"><span data-stu-id="a891d-138">Timestamp</span></span>
- <span data-ttu-id="a891d-139">ProcessId</span><span class="sxs-lookup"><span data-stu-id="a891d-139">ProcessId</span></span>
- <span data-ttu-id="a891d-140">ThreadId</span><span class="sxs-lookup"><span data-stu-id="a891d-140">ThreadId</span></span>
- <span data-ttu-id="a891d-141">Pile des appels</span><span class="sxs-lookup"><span data-stu-id="a891d-141">Callstack</span></span>

<span data-ttu-id="a891d-142">None est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a891d-142">None is the default.</span></span>

<span data-ttu-id="a891d-143">Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "ThreadID,ProcessID".</span><span class="sxs-lookup"><span data-stu-id="a891d-143">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a891d-144">-Name</span><span class="sxs-lookup"><span data-stu-id="a891d-144">-Name</span></span>

<span data-ttu-id="a891d-145">Spécifie les composants qui sont suivis.</span><span class="sxs-lookup"><span data-stu-id="a891d-145">Specifies which components are traced.</span></span>
<span data-ttu-id="a891d-146">Entrez le nom de la source de suivi de chaque composant.</span><span class="sxs-lookup"><span data-stu-id="a891d-146">Enter the name of the trace source of each component.</span></span>
<span data-ttu-id="a891d-147">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="a891d-147">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="a891d-148">-Option</span><span class="sxs-lookup"><span data-stu-id="a891d-148">-Option</span></span>

<span data-ttu-id="a891d-149">Spécifie le type des événements qui sont suivis.</span><span class="sxs-lookup"><span data-stu-id="a891d-149">Specifies the type of events that are traced.</span></span>
<span data-ttu-id="a891d-150">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="a891d-150">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a891d-151">None</span><span class="sxs-lookup"><span data-stu-id="a891d-151">None</span></span>
- <span data-ttu-id="a891d-152">Constructeur</span><span class="sxs-lookup"><span data-stu-id="a891d-152">Constructor</span></span>
- <span data-ttu-id="a891d-153">Dispose</span><span class="sxs-lookup"><span data-stu-id="a891d-153">Dispose</span></span>
- <span data-ttu-id="a891d-154">Finaliseur</span><span class="sxs-lookup"><span data-stu-id="a891d-154">Finalizer</span></span>
- <span data-ttu-id="a891d-155">Méthode</span><span class="sxs-lookup"><span data-stu-id="a891d-155">Method</span></span>
- <span data-ttu-id="a891d-156">Propriété</span><span class="sxs-lookup"><span data-stu-id="a891d-156">Property</span></span>
- <span data-ttu-id="a891d-157">Délégués</span><span class="sxs-lookup"><span data-stu-id="a891d-157">Delegates</span></span>
- <span data-ttu-id="a891d-158">Événements</span><span class="sxs-lookup"><span data-stu-id="a891d-158">Events</span></span>
- <span data-ttu-id="a891d-159">Exception</span><span class="sxs-lookup"><span data-stu-id="a891d-159">Exception</span></span>
- <span data-ttu-id="a891d-160">Verrouillage</span><span class="sxs-lookup"><span data-stu-id="a891d-160">Lock</span></span>
- <span data-ttu-id="a891d-161">Error</span><span class="sxs-lookup"><span data-stu-id="a891d-161">Error</span></span>
- <span data-ttu-id="a891d-162">Erreurs</span><span class="sxs-lookup"><span data-stu-id="a891d-162">Errors</span></span>
- <span data-ttu-id="a891d-163">Avertissement</span><span class="sxs-lookup"><span data-stu-id="a891d-163">Warning</span></span>
- <span data-ttu-id="a891d-164">Commentaires</span><span class="sxs-lookup"><span data-stu-id="a891d-164">Verbose</span></span>
- <span data-ttu-id="a891d-165">WriteLine</span><span class="sxs-lookup"><span data-stu-id="a891d-165">WriteLine</span></span>
- <span data-ttu-id="a891d-166">Données</span><span class="sxs-lookup"><span data-stu-id="a891d-166">Data</span></span>
- <span data-ttu-id="a891d-167">Scope (Étendue)</span><span class="sxs-lookup"><span data-stu-id="a891d-167">Scope</span></span>
- <span data-ttu-id="a891d-168">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="a891d-168">ExecutionFlow</span></span>
- <span data-ttu-id="a891d-169">Assert</span><span class="sxs-lookup"><span data-stu-id="a891d-169">Assert</span></span>
- <span data-ttu-id="a891d-170">Tous</span><span class="sxs-lookup"><span data-stu-id="a891d-170">All</span></span>

<span data-ttu-id="a891d-171">« All » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a891d-171">All is the default.</span></span>

<span data-ttu-id="a891d-172">Les valeurs suivantes sont des combinaisons d'autres valeurs :</span><span class="sxs-lookup"><span data-stu-id="a891d-172">The following values are combinations of other values:</span></span>

- <span data-ttu-id="a891d-173">ExecutionFlow : (Constructor, dispose, Finalizer, Method, Delegates, Events et Scope)</span><span class="sxs-lookup"><span data-stu-id="a891d-173">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="a891d-174">Données : (Constructor, dispose, Finalizer, Property, verbose et WriteLine)</span><span class="sxs-lookup"><span data-stu-id="a891d-174">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="a891d-175">Erreurs : (erreur et exception).</span><span class="sxs-lookup"><span data-stu-id="a891d-175">Errors: (Error and Exception).</span></span>

<span data-ttu-id="a891d-176">Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "Constructor,Dispose".</span><span class="sxs-lookup"><span data-stu-id="a891d-176">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a891d-177">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a891d-177">-PassThru</span></span>

<span data-ttu-id="a891d-178">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="a891d-178">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="a891d-179">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="a891d-179">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a891d-180">-PSHost</span><span class="sxs-lookup"><span data-stu-id="a891d-180">-PSHost</span></span>

<span data-ttu-id="a891d-181">indique que cette applet de commande envoie la sortie de suivi à l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a891d-181">ndicates that this cmdlet sends the trace output to the PowerShell host.</span></span>
<span data-ttu-id="a891d-182">Ce paramètre sélectionne également l'écouteur de suivi de PSHost.</span><span class="sxs-lookup"><span data-stu-id="a891d-182">This parameter also selects the PSHost trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a891d-183">-RemoveFileListener</span><span class="sxs-lookup"><span data-stu-id="a891d-183">-RemoveFileListener</span></span>

<span data-ttu-id="a891d-184">Arrête le suivi en supprimant l'écouteur de suivi de fichier associé au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="a891d-184">Stops the trace by removing the file trace listener associated with the specified file.</span></span>
<span data-ttu-id="a891d-185">Entrez le chemin d'accès et le nom du fichier de sortie du suivi.</span><span class="sxs-lookup"><span data-stu-id="a891d-185">Enter the path and file name of the trace output file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a891d-186">-RemoveListener</span><span class="sxs-lookup"><span data-stu-id="a891d-186">-RemoveListener</span></span>

<span data-ttu-id="a891d-187">Arrête le suivi en supprimant l'écouteur de suivi.</span><span class="sxs-lookup"><span data-stu-id="a891d-187">Stops the trace by removing the trace listener.</span></span>

<span data-ttu-id="a891d-188">Utilisez les valeurs suivantes avec *RemoveListener*:</span><span class="sxs-lookup"><span data-stu-id="a891d-188">Use the following values with *RemoveListener*:</span></span>

- <span data-ttu-id="a891d-189">Pour supprimer PSHost (console), tapez `Host` .</span><span class="sxs-lookup"><span data-stu-id="a891d-189">To remove PSHost (console), type `Host`.</span></span>
- <span data-ttu-id="a891d-190">Pour supprimer le débogueur, tapez `Debug` .</span><span class="sxs-lookup"><span data-stu-id="a891d-190">To remove Debugger, type `Debug`.</span></span>
- <span data-ttu-id="a891d-191">Pour supprimer tous les écouteurs de suivi, tapez `*` .</span><span class="sxs-lookup"><span data-stu-id="a891d-191">To remove all trace listeners, type `*`.</span></span>

<span data-ttu-id="a891d-192">Pour supprimer l’écouteur de suivi de fichier, utilisez le paramètre *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="a891d-192">To remove the file trace listener, use the *RemoveFileListener* parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a891d-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a891d-193">CommonParameters</span></span>

<span data-ttu-id="a891d-194">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a891d-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a891d-195">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a891d-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a891d-196">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a891d-196">INPUTS</span></span>

### <span data-ttu-id="a891d-197">System.String</span><span class="sxs-lookup"><span data-stu-id="a891d-197">System.String</span></span>

<span data-ttu-id="a891d-198">Vous pouvez diriger une chaîne qui contient un nom vers **Set-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="a891d-198">You can pipe a string that contains a name to **Set-TraceSource**.</span></span>

## <span data-ttu-id="a891d-199">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a891d-199">OUTPUTS</span></span>

### <span data-ttu-id="a891d-200">None ou System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="a891d-200">None or System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="a891d-201">Quand vous utilisez le paramètre *PassThru* , **Set-TraceSource** génère un objet **System. Management. Automation. PSTraceSource** qui représente la session de trace.</span><span class="sxs-lookup"><span data-stu-id="a891d-201">When you use the *PassThru* parameter, **Set-TraceSource** generates a **System.Management.Automation.PSTraceSource** object representing the trace session.</span></span>
<span data-ttu-id="a891d-202">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="a891d-202">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a891d-203">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a891d-203">NOTES</span></span>

* <span data-ttu-id="a891d-204">Le suivi est une méthode que les développeurs utilisent pour déboguer et affiner les programmes.</span><span class="sxs-lookup"><span data-stu-id="a891d-204">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="a891d-205">Pendant le suivi, le programme génère des messages détaillés sur chaque étape du traitement interne.</span><span class="sxs-lookup"><span data-stu-id="a891d-205">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

  <span data-ttu-id="a891d-206">Les applets de commande PowerShell Tracing sont conçues pour aider les développeurs PowerShell, mais elles sont disponibles pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="a891d-206">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span>
<span data-ttu-id="a891d-207">Ils vous permettent de surveiller presque tous les aspects de la fonctionnalité de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a891d-207">They let you monitor nearly every aspect of the functionality of PowerShell.</span></span>

  <span data-ttu-id="a891d-208">Une source de suivi est la partie de chaque composant PowerShell qui gère le suivi et génère des messages de suivi pour le composant.</span><span class="sxs-lookup"><span data-stu-id="a891d-208">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span>
<span data-ttu-id="a891d-209">Pour suivre un composant, vous identifiez sa source de suivi.</span><span class="sxs-lookup"><span data-stu-id="a891d-209">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="a891d-210">Un écouteur de suivi reçoit la sortie de la trace et l’affiche à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a891d-210">A trace listener receives the output of the trace and displays it to the user.</span></span>
<span data-ttu-id="a891d-211">Vous pouvez choisir d’envoyer les données de trace à un débogueur en mode utilisateur ou en mode noyau, à la console, à un fichier ou à un écouteur personnalisé dérivé de la classe **System. Diagnostics. TraceListener** .</span><span class="sxs-lookup"><span data-stu-id="a891d-211">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

* <span data-ttu-id="a891d-212">Pour démarrer une trace, utilisez le paramètre *Name* pour spécifier une source de suivi et les paramètres *filePath*, *Debugger* ou *PSHost* pour spécifier un écouteur (une destination pour la sortie).</span><span class="sxs-lookup"><span data-stu-id="a891d-212">To start a trace, use the *Name* parameter to specify a trace source and the *FilePath*, *Debugger*, or *PSHost* parameters to specify a listener (a destination for the output).</span></span> <span data-ttu-id="a891d-213">Utilisez le paramètre *options* pour déterminer les types d’événements qui sont suivis et le paramètre *ListenerOption* pour configurer la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="a891d-213">Use the *Options* parameter to determine the types of events that are traced and the *ListenerOption* parameter to configure the trace output.</span></span>
* <span data-ttu-id="a891d-214">Pour modifier la configuration d’une trace, entrez une commande **Set-TraceSource** comme vous le feriez pour démarrer une trace.</span><span class="sxs-lookup"><span data-stu-id="a891d-214">To change the configuration of a trace, enter a **Set-TraceSource** command as you would to start a trace.</span></span> <span data-ttu-id="a891d-215">PowerShell reconnaît que la source de suivi est déjà en cours de suivi.</span><span class="sxs-lookup"><span data-stu-id="a891d-215">PowerShell recognizes that the trace source is already being traced.</span></span> <span data-ttu-id="a891d-216">Elle arrête le suivi, ajoute la nouvelle configuration, puis démarre ou redémarre le suivi.</span><span class="sxs-lookup"><span data-stu-id="a891d-216">It stops the trace, adds the new configuration, and starts or restarts the trace.</span></span>
* <span data-ttu-id="a891d-217">Pour arrêter une trace, utilisez le paramètre *RemoveListener* .</span><span class="sxs-lookup"><span data-stu-id="a891d-217">To stop a trace, use the *RemoveListener* parameter.</span></span> <span data-ttu-id="a891d-218">Pour arrêter une trace qui utilise l’écouteur de fichiers (une trace démarrée à l’aide du paramètre *filePath* ), utilisez le paramètre *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="a891d-218">To stop a trace that uses the file listener (a trace started by using the *FilePath* parameter), use the *RemoveFileListener* parameter.</span></span> <span data-ttu-id="a891d-219">Quand vous supprimez l'écouteur, le suivi s'arrête.</span><span class="sxs-lookup"><span data-stu-id="a891d-219">When you remove the listener, the trace stops.</span></span>
* <span data-ttu-id="a891d-220">Pour déterminer les composants qui peuvent être suivis, utilisez Get-TraceSource.</span><span class="sxs-lookup"><span data-stu-id="a891d-220">To determine which components can be traced, use Get-TraceSource.</span></span> <span data-ttu-id="a891d-221">Les sources de suivi pour chaque module sont chargées automatiquement lorsque le composant est en cours d’utilisation, et elles s’affichent dans la sortie de la **récupération** de l’élément.</span><span class="sxs-lookup"><span data-stu-id="a891d-221">The trace sources for each module are loaded automatically when the component is in use, and they appear in the output of **Get-TraceSource**.</span></span>

## <span data-ttu-id="a891d-222">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a891d-222">RELATED LINKS</span></span>

[<span data-ttu-id="a891d-223">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="a891d-223">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="a891d-224">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="a891d-224">Trace-Command</span></span>](Trace-Command.md)

