---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: cef166404af546c35ccc3b0ffed4174515f74c15
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203133"
---
# <span data-ttu-id="850d6-103">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="850d6-103">Set-TraceSource</span></span>

## <span data-ttu-id="850d6-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="850d6-104">SYNOPSIS</span></span>
<span data-ttu-id="850d6-105">Configure, démarre et arrête un suivi des composants PowerShell.</span><span class="sxs-lookup"><span data-stu-id="850d6-105">Configures, starts, and stops a trace of PowerShell components.</span></span>

## <span data-ttu-id="850d6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="850d6-106">SYNTAX</span></span>

### <span data-ttu-id="850d6-107">optionsSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="850d6-107">optionsSet (Default)</span></span>

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="850d6-108">removeAllListenersSet</span><span class="sxs-lookup"><span data-stu-id="850d6-108">removeAllListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="850d6-109">removeFileListenersSet</span><span class="sxs-lookup"><span data-stu-id="850d6-109">removeFileListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="850d6-110">Description</span><span class="sxs-lookup"><span data-stu-id="850d6-110">DESCRIPTION</span></span>

<span data-ttu-id="850d6-111">L’applet de commande **Set-TraceSource** configure, démarre et arrête une trace d’un composant PowerShell.</span><span class="sxs-lookup"><span data-stu-id="850d6-111">The **Set-TraceSource** cmdlet configures, starts, and stops a trace of a PowerShell component.</span></span>
<span data-ttu-id="850d6-112">Vous pouvez l'utiliser pour spécifier quels composants seront tracés et où la sortie du suivi est envoyée.</span><span class="sxs-lookup"><span data-stu-id="850d6-112">You can use it to specify which components will be traced and where the tracing output is sent.</span></span>

## <span data-ttu-id="850d6-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="850d6-113">EXAMPLES</span></span>

### <span data-ttu-id="850d6-114">Exemple 1 : tracer le composant ParameterBinding</span><span class="sxs-lookup"><span data-stu-id="850d6-114">Example 1: Trace the ParameterBinding component</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

<span data-ttu-id="850d6-115">Cette commande démarre le suivi pour le composant ParameterBinding de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="850d6-115">This command starts tracing for the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="850d6-116">Elle utilise le paramètre *Name* pour spécifier la source de suivi, le paramètre *option* pour sélectionner les événements de trace ExecutionFlow et le paramètre *PSHost* pour sélectionner l’écouteur hôte PowerShell, qui envoie la sortie vers la console.</span><span class="sxs-lookup"><span data-stu-id="850d6-116">It uses the *Name* parameter to specify the trace source, the *Option* parameter to select the ExecutionFlow trace events, and the *PSHost* parameter to select the PowerShell host listener, which sends the output to the console.</span></span>
<span data-ttu-id="850d6-117">Le paramètre *ListenerOption* ajoute les valeurs ProcessId et timestamp au préfixe du message de suivi.</span><span class="sxs-lookup"><span data-stu-id="850d6-117">The *ListenerOption* parameter adds the ProcessID and TimeStamp values to the trace message prefix.</span></span>

### <span data-ttu-id="850d6-118">Exemple 2 : arrêter une trace</span><span class="sxs-lookup"><span data-stu-id="850d6-118">Example 2: Stop a trace</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

<span data-ttu-id="850d6-119">Cette commande arrête la trace du composant ParameterBinding de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="850d6-119">This command stops the trace of the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="850d6-120">Elle utilise le paramètre *Name* pour identifier le composant qui a été suivi et le paramètre *RemoveListener* pour identifier l’écouteur de suivi.</span><span class="sxs-lookup"><span data-stu-id="850d6-120">It uses the *Name* parameter to identify the component that was being traced and the *RemoveListener* parameter to identify the trace listener.</span></span>

## <span data-ttu-id="850d6-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="850d6-121">PARAMETERS</span></span>

### <span data-ttu-id="850d6-122">-Débogueur</span><span class="sxs-lookup"><span data-stu-id="850d6-122">-Debugger</span></span>

<span data-ttu-id="850d6-123">Indique que l’applet de commande envoie la sortie de trace au débogueur.</span><span class="sxs-lookup"><span data-stu-id="850d6-123">Indicates that the cmdlet sends the trace output to the debugger.</span></span>
<span data-ttu-id="850d6-124">Vous pouvez afficher la sortie dans n'importe quel débogueur en mode noyau ou en mode utilisateur, ou bien dans Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="850d6-124">You can view the output in any user-mode or kernel mode debugger or in Microsoft Visual Studio.</span></span>
<span data-ttu-id="850d6-125">Ce paramètre sélectionne également l'écouteur de suivi par défaut.</span><span class="sxs-lookup"><span data-stu-id="850d6-125">This parameter also selects the default trace listener.</span></span>

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

### <span data-ttu-id="850d6-126">-FilePath</span><span class="sxs-lookup"><span data-stu-id="850d6-126">-FilePath</span></span>

<span data-ttu-id="850d6-127">Spécifie un fichier auquel cette applet de commande envoie la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="850d6-127">Specifies a file that this cmdlet sends the trace output to.</span></span>
<span data-ttu-id="850d6-128">Ce paramètre sélectionne également l'écouteur de suivi de fichier.</span><span class="sxs-lookup"><span data-stu-id="850d6-128">This parameter also selects the file trace listener.</span></span>
<span data-ttu-id="850d6-129">Si vous utilisez ce paramètre pour démarrer le suivi, utilisez le paramètre *RemoveFileListener* pour arrêter la trace.</span><span class="sxs-lookup"><span data-stu-id="850d6-129">If you use this parameter to start the trace, use the *RemoveFileListener* parameter to stop the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="850d6-130">-Force</span><span class="sxs-lookup"><span data-stu-id="850d6-130">-Force</span></span>

<span data-ttu-id="850d6-131">Indique que l’applet de commande remplace un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="850d6-131">Indicates that the cmdlet overwrites a read-only file.</span></span>
<span data-ttu-id="850d6-132">Utilisez avec le paramètre *filePath* .</span><span class="sxs-lookup"><span data-stu-id="850d6-132">Use with the *FilePath* parameter.</span></span>

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

### <span data-ttu-id="850d6-133">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="850d6-133">-ListenerOption</span></span>

<span data-ttu-id="850d6-134">Spécifie des données facultatives pour le préfixe de chaque message de trace dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="850d6-134">Specifies optional data to the prefix of each trace message in the output.</span></span>
<span data-ttu-id="850d6-135">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="850d6-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="850d6-136">Aucun</span><span class="sxs-lookup"><span data-stu-id="850d6-136">None</span></span>
- <span data-ttu-id="850d6-137">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="850d6-137">LogicalOperationStack</span></span>
- <span data-ttu-id="850d6-138">DateTime</span><span class="sxs-lookup"><span data-stu-id="850d6-138">DateTime</span></span>
- <span data-ttu-id="850d6-139">Timestamp</span><span class="sxs-lookup"><span data-stu-id="850d6-139">Timestamp</span></span>
- <span data-ttu-id="850d6-140">ProcessId</span><span class="sxs-lookup"><span data-stu-id="850d6-140">ProcessId</span></span>
- <span data-ttu-id="850d6-141">ThreadId</span><span class="sxs-lookup"><span data-stu-id="850d6-141">ThreadId</span></span>
- <span data-ttu-id="850d6-142">Pile des appels</span><span class="sxs-lookup"><span data-stu-id="850d6-142">Callstack</span></span>

<span data-ttu-id="850d6-143">None est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="850d6-143">None is the default.</span></span>

<span data-ttu-id="850d6-144">Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "ThreadID,ProcessID".</span><span class="sxs-lookup"><span data-stu-id="850d6-144">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

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

### <span data-ttu-id="850d6-145">-Name</span><span class="sxs-lookup"><span data-stu-id="850d6-145">-Name</span></span>

<span data-ttu-id="850d6-146">Spécifie les composants qui sont suivis.</span><span class="sxs-lookup"><span data-stu-id="850d6-146">Specifies which components are traced.</span></span>
<span data-ttu-id="850d6-147">Entrez le nom de la source de suivi de chaque composant.</span><span class="sxs-lookup"><span data-stu-id="850d6-147">Enter the name of the trace source of each component.</span></span>
<span data-ttu-id="850d6-148">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="850d6-148">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="850d6-149">-Option</span><span class="sxs-lookup"><span data-stu-id="850d6-149">-Option</span></span>

<span data-ttu-id="850d6-150">Spécifie le type des événements qui sont suivis.</span><span class="sxs-lookup"><span data-stu-id="850d6-150">Specifies the type of events that are traced.</span></span>
<span data-ttu-id="850d6-151">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="850d6-151">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="850d6-152">Aucun</span><span class="sxs-lookup"><span data-stu-id="850d6-152">None</span></span>
- <span data-ttu-id="850d6-153">Constructeur</span><span class="sxs-lookup"><span data-stu-id="850d6-153">Constructor</span></span>
- <span data-ttu-id="850d6-154">Dispose</span><span class="sxs-lookup"><span data-stu-id="850d6-154">Dispose</span></span>
- <span data-ttu-id="850d6-155">Finaliseur</span><span class="sxs-lookup"><span data-stu-id="850d6-155">Finalizer</span></span>
- <span data-ttu-id="850d6-156">Méthode</span><span class="sxs-lookup"><span data-stu-id="850d6-156">Method</span></span>
- <span data-ttu-id="850d6-157">Propriété</span><span class="sxs-lookup"><span data-stu-id="850d6-157">Property</span></span>
- <span data-ttu-id="850d6-158">Délégués</span><span class="sxs-lookup"><span data-stu-id="850d6-158">Delegates</span></span>
- <span data-ttu-id="850d6-159">Événements</span><span class="sxs-lookup"><span data-stu-id="850d6-159">Events</span></span>
- <span data-ttu-id="850d6-160">Exception</span><span class="sxs-lookup"><span data-stu-id="850d6-160">Exception</span></span>
- <span data-ttu-id="850d6-161">Verrouillage</span><span class="sxs-lookup"><span data-stu-id="850d6-161">Lock</span></span>
- <span data-ttu-id="850d6-162">Erreur</span><span class="sxs-lookup"><span data-stu-id="850d6-162">Error</span></span>
- <span data-ttu-id="850d6-163">Erreurs</span><span class="sxs-lookup"><span data-stu-id="850d6-163">Errors</span></span>
- <span data-ttu-id="850d6-164">Avertissement</span><span class="sxs-lookup"><span data-stu-id="850d6-164">Warning</span></span>
- <span data-ttu-id="850d6-165">Commentaires</span><span class="sxs-lookup"><span data-stu-id="850d6-165">Verbose</span></span>
- <span data-ttu-id="850d6-166">WriteLine</span><span class="sxs-lookup"><span data-stu-id="850d6-166">WriteLine</span></span>
- <span data-ttu-id="850d6-167">Données</span><span class="sxs-lookup"><span data-stu-id="850d6-167">Data</span></span>
- <span data-ttu-id="850d6-168">Étendue</span><span class="sxs-lookup"><span data-stu-id="850d6-168">Scope</span></span>
- <span data-ttu-id="850d6-169">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="850d6-169">ExecutionFlow</span></span>
- <span data-ttu-id="850d6-170">Assert</span><span class="sxs-lookup"><span data-stu-id="850d6-170">Assert</span></span>
- <span data-ttu-id="850d6-171">Tous</span><span class="sxs-lookup"><span data-stu-id="850d6-171">All</span></span>

<span data-ttu-id="850d6-172">« All » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="850d6-172">All is the default.</span></span>

<span data-ttu-id="850d6-173">Les valeurs suivantes sont des combinaisons d'autres valeurs :</span><span class="sxs-lookup"><span data-stu-id="850d6-173">The following values are combinations of other values:</span></span>

- <span data-ttu-id="850d6-174">ExecutionFlow : (Constructor, dispose, Finalizer, Method, Delegates, Events et Scope)</span><span class="sxs-lookup"><span data-stu-id="850d6-174">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="850d6-175">Données : (Constructor, dispose, Finalizer, Property, verbose et WriteLine)</span><span class="sxs-lookup"><span data-stu-id="850d6-175">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="850d6-176">Erreurs : (erreur et exception).</span><span class="sxs-lookup"><span data-stu-id="850d6-176">Errors: (Error and Exception).</span></span>

<span data-ttu-id="850d6-177">Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "Constructor,Dispose".</span><span class="sxs-lookup"><span data-stu-id="850d6-177">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

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

### <span data-ttu-id="850d6-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="850d6-178">-PassThru</span></span>

<span data-ttu-id="850d6-179">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="850d6-179">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="850d6-180">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="850d6-180">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="850d6-181">-PSHost</span><span class="sxs-lookup"><span data-stu-id="850d6-181">-PSHost</span></span>

<span data-ttu-id="850d6-182">indique que cette applet de commande envoie la sortie de suivi à l’hôte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="850d6-182">ndicates that this cmdlet sends the trace output to the PowerShell host.</span></span>
<span data-ttu-id="850d6-183">Ce paramètre sélectionne également l'écouteur de suivi de PSHost.</span><span class="sxs-lookup"><span data-stu-id="850d6-183">This parameter also selects the PSHost trace listener.</span></span>

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

### <span data-ttu-id="850d6-184">-RemoveFileListener</span><span class="sxs-lookup"><span data-stu-id="850d6-184">-RemoveFileListener</span></span>

<span data-ttu-id="850d6-185">Arrête le suivi en supprimant l'écouteur de suivi de fichier associé au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="850d6-185">Stops the trace by removing the file trace listener associated with the specified file.</span></span>
<span data-ttu-id="850d6-186">Entrez le chemin d'accès et le nom du fichier de sortie du suivi.</span><span class="sxs-lookup"><span data-stu-id="850d6-186">Enter the path and file name of the trace output file.</span></span>

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

### <span data-ttu-id="850d6-187">-RemoveListener</span><span class="sxs-lookup"><span data-stu-id="850d6-187">-RemoveListener</span></span>

<span data-ttu-id="850d6-188">Arrête le suivi en supprimant l'écouteur de suivi.</span><span class="sxs-lookup"><span data-stu-id="850d6-188">Stops the trace by removing the trace listener.</span></span>

<span data-ttu-id="850d6-189">Utilisez les valeurs suivantes avec *RemoveListener* :</span><span class="sxs-lookup"><span data-stu-id="850d6-189">Use the following values with *RemoveListener* :</span></span>

- <span data-ttu-id="850d6-190">Pour supprimer PSHost (console), tapez `Host` .</span><span class="sxs-lookup"><span data-stu-id="850d6-190">To remove PSHost (console), type `Host`.</span></span>
- <span data-ttu-id="850d6-191">Pour supprimer le débogueur, tapez `Debug` .</span><span class="sxs-lookup"><span data-stu-id="850d6-191">To remove Debugger, type `Debug`.</span></span>
- <span data-ttu-id="850d6-192">Pour supprimer tous les écouteurs de suivi, tapez `*` .</span><span class="sxs-lookup"><span data-stu-id="850d6-192">To remove all trace listeners, type `*`.</span></span>

<span data-ttu-id="850d6-193">Pour supprimer l’écouteur de suivi de fichier, utilisez le paramètre *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="850d6-193">To remove the file trace listener, use the *RemoveFileListener* parameter.</span></span>

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

### <span data-ttu-id="850d6-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="850d6-194">CommonParameters</span></span>

<span data-ttu-id="850d6-195">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="850d6-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="850d6-196">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="850d6-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="850d6-197">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="850d6-197">INPUTS</span></span>

### <span data-ttu-id="850d6-198">System.String</span><span class="sxs-lookup"><span data-stu-id="850d6-198">System.String</span></span>

<span data-ttu-id="850d6-199">Vous pouvez diriger une chaîne qui contient un nom vers **Set-TraceSource** .</span><span class="sxs-lookup"><span data-stu-id="850d6-199">You can pipe a string that contains a name to **Set-TraceSource** .</span></span>

## <span data-ttu-id="850d6-200">SORTIES</span><span class="sxs-lookup"><span data-stu-id="850d6-200">OUTPUTS</span></span>

### <span data-ttu-id="850d6-201">None ou System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="850d6-201">None or System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="850d6-202">Quand vous utilisez le paramètre *PassThru* , **Set-TraceSource** génère un objet **System. Management. Automation. PSTraceSource** qui représente la session de trace.</span><span class="sxs-lookup"><span data-stu-id="850d6-202">When you use the *PassThru* parameter, **Set-TraceSource** generates a **System.Management.Automation.PSTraceSource** object representing the trace session.</span></span>
<span data-ttu-id="850d6-203">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="850d6-203">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="850d6-204">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="850d6-204">NOTES</span></span>

* <span data-ttu-id="850d6-205">Le suivi est une méthode que les développeurs utilisent pour déboguer et affiner les programmes.</span><span class="sxs-lookup"><span data-stu-id="850d6-205">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="850d6-206">Pendant le suivi, le programme génère des messages détaillés sur chaque étape du traitement interne.</span><span class="sxs-lookup"><span data-stu-id="850d6-206">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

  <span data-ttu-id="850d6-207">Les applets de commande PowerShell Tracing sont conçues pour aider les développeurs PowerShell, mais elles sont disponibles pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="850d6-207">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span>
<span data-ttu-id="850d6-208">Ils vous permettent de surveiller presque tous les aspects de la fonctionnalité de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="850d6-208">They let you monitor nearly every aspect of the functionality of PowerShell.</span></span>

  <span data-ttu-id="850d6-209">Une source de suivi est la partie de chaque composant PowerShell qui gère le suivi et génère des messages de suivi pour le composant.</span><span class="sxs-lookup"><span data-stu-id="850d6-209">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span>
<span data-ttu-id="850d6-210">Pour suivre un composant, vous identifiez sa source de suivi.</span><span class="sxs-lookup"><span data-stu-id="850d6-210">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="850d6-211">Un écouteur de suivi reçoit la sortie de la trace et l’affiche à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="850d6-211">A trace listener receives the output of the trace and displays it to the user.</span></span>
<span data-ttu-id="850d6-212">Vous pouvez choisir d’envoyer les données de trace à un débogueur en mode utilisateur ou en mode noyau, à la console, à un fichier ou à un écouteur personnalisé dérivé de la classe **System. Diagnostics. TraceListener** .</span><span class="sxs-lookup"><span data-stu-id="850d6-212">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

* <span data-ttu-id="850d6-213">Pour démarrer une trace, utilisez le paramètre *Name* pour spécifier une source de suivi et les paramètres *filePath* , *Debugger* ou *PSHost* pour spécifier un écouteur (une destination pour la sortie).</span><span class="sxs-lookup"><span data-stu-id="850d6-213">To start a trace, use the *Name* parameter to specify a trace source and the *FilePath* , *Debugger* , or *PSHost* parameters to specify a listener (a destination for the output).</span></span> <span data-ttu-id="850d6-214">Utilisez le paramètre *options* pour déterminer les types d’événements qui sont suivis et le paramètre *ListenerOption* pour configurer la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="850d6-214">Use the *Options* parameter to determine the types of events that are traced and the *ListenerOption* parameter to configure the trace output.</span></span>
* <span data-ttu-id="850d6-215">Pour modifier la configuration d’une trace, entrez une commande **Set-TraceSource** comme vous le feriez pour démarrer une trace.</span><span class="sxs-lookup"><span data-stu-id="850d6-215">To change the configuration of a trace, enter a **Set-TraceSource** command as you would to start a trace.</span></span> <span data-ttu-id="850d6-216">PowerShell reconnaît que la source de suivi est déjà en cours de suivi.</span><span class="sxs-lookup"><span data-stu-id="850d6-216">PowerShell recognizes that the trace source is already being traced.</span></span> <span data-ttu-id="850d6-217">Elle arrête le suivi, ajoute la nouvelle configuration, puis démarre ou redémarre le suivi.</span><span class="sxs-lookup"><span data-stu-id="850d6-217">It stops the trace, adds the new configuration, and starts or restarts the trace.</span></span>
* <span data-ttu-id="850d6-218">Pour arrêter une trace, utilisez le paramètre *RemoveListener* .</span><span class="sxs-lookup"><span data-stu-id="850d6-218">To stop a trace, use the *RemoveListener* parameter.</span></span> <span data-ttu-id="850d6-219">Pour arrêter une trace qui utilise l’écouteur de fichiers (une trace démarrée à l’aide du paramètre *filePath* ), utilisez le paramètre *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="850d6-219">To stop a trace that uses the file listener (a trace started by using the *FilePath* parameter), use the *RemoveFileListener* parameter.</span></span> <span data-ttu-id="850d6-220">Quand vous supprimez l'écouteur, le suivi s'arrête.</span><span class="sxs-lookup"><span data-stu-id="850d6-220">When you remove the listener, the trace stops.</span></span>
* <span data-ttu-id="850d6-221">Pour déterminer les composants qui peuvent être suivis, utilisez Get-TraceSource.</span><span class="sxs-lookup"><span data-stu-id="850d6-221">To determine which components can be traced, use Get-TraceSource.</span></span> <span data-ttu-id="850d6-222">Les sources de suivi pour chaque module sont chargées automatiquement lorsque le composant est en cours d’utilisation, et elles s’affichent dans la sortie de la **récupération** de l’élément.</span><span class="sxs-lookup"><span data-stu-id="850d6-222">The trace sources for each module are loaded automatically when the component is in use, and they appear in the output of **Get-TraceSource** .</span></span>

## <span data-ttu-id="850d6-223">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="850d6-223">RELATED LINKS</span></span>

[<span data-ttu-id="850d6-224">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="850d6-224">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="850d6-225">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="850d6-225">Trace-Command</span></span>](Trace-Command.md)
