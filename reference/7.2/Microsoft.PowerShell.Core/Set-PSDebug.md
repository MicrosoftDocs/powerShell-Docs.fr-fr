---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-psdebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSDebug
ms.openlocfilehash: 45764b09bfa1f632fe5c36ca76b32b4a1b54874c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597329"
---
# <span data-ttu-id="c6a47-102">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="c6a47-102">Set-PSDebug</span></span>

## <span data-ttu-id="c6a47-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c6a47-103">SYNOPSIS</span></span>
<span data-ttu-id="c6a47-104">Active et désactive les fonctionnalités de débogage de script, définit le niveau de suivi et bascule en mode strict.</span><span class="sxs-lookup"><span data-stu-id="c6a47-104">Turns script debugging features on and off, sets the trace level, and toggles strict mode.</span></span>

## <span data-ttu-id="c6a47-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c6a47-105">SYNTAX</span></span>

### <span data-ttu-id="c6a47-106">sur</span><span class="sxs-lookup"><span data-stu-id="c6a47-106">on</span></span>

```
Set-PSDebug [-Trace <Int32>] [-Step] [-Strict] [<CommonParameters>]
```

### <span data-ttu-id="c6a47-107">arrêt</span><span class="sxs-lookup"><span data-stu-id="c6a47-107">off</span></span>

```
Set-PSDebug [-Off] [<CommonParameters>]
```

## <span data-ttu-id="c6a47-108">Description</span><span class="sxs-lookup"><span data-stu-id="c6a47-108">DESCRIPTION</span></span>

<span data-ttu-id="c6a47-109">L' `Set-PSDebug` applet de commande active et désactive les fonctionnalités de débogage de script, définit le niveau de suivi et bascule en mode strict.</span><span class="sxs-lookup"><span data-stu-id="c6a47-109">The `Set-PSDebug` cmdlet turns script debugging features on and off, sets the trace level, and toggles strict mode.</span></span> <span data-ttu-id="c6a47-110">Par défaut, les fonctionnalités de débogage PowerShell sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="c6a47-110">By default, the PowerShell debug features are off.</span></span>

<span data-ttu-id="c6a47-111">Lorsque le paramètre **trace** a la valeur `1` , chaque ligne de script est tracée lors de son exécution.</span><span class="sxs-lookup"><span data-stu-id="c6a47-111">When the **Trace** parameter has a value of `1`, each line of script is traced as it runs.</span></span> <span data-ttu-id="c6a47-112">Lorsque le paramètre a la valeur `2` , les attributions de variables, les appels de fonction et les appels de script sont également suivis.</span><span class="sxs-lookup"><span data-stu-id="c6a47-112">When the parameter has a value of `2`, variable assignments, function calls, and script calls are also traced.</span></span> <span data-ttu-id="c6a47-113">Si le paramètre **Step** est spécifié, vous êtes invité à confirmer l’exécution de chaque ligne du script.</span><span class="sxs-lookup"><span data-stu-id="c6a47-113">If the **Step** parameter is specified, you're prompted before each line of the script runs.</span></span>

## <span data-ttu-id="c6a47-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c6a47-114">EXAMPLES</span></span>

### <span data-ttu-id="c6a47-115">Exemple 1 : définir le niveau de suivi</span><span class="sxs-lookup"><span data-stu-id="c6a47-115">Example 1: Set the trace level</span></span>

<span data-ttu-id="c6a47-116">Cet exemple définit le niveau de suivi sur `2` , puis exécute un script qui affiche les nombres 1, 2 et</span><span class="sxs-lookup"><span data-stu-id="c6a47-116">This example sets the trace level to `2`, and then runs a script that displays the numbers 1, 2, and</span></span>
3.

```powershell
Set-PSDebug -Trace 2; foreach ($i in 1..3) {$i}
```

```Output
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in  >>>> 1..3) {$i}
DEBUG:     ! SET $foreach = 'IEnumerator'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '1'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
1
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '2'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
2
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '3'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
3
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $foreach = ''.
```

### <span data-ttu-id="c6a47-117">Exemple 2 : activer l’exécution pas à pas</span><span class="sxs-lookup"><span data-stu-id="c6a47-117">Example 2: Turn on stepping</span></span>

<span data-ttu-id="c6a47-118">Cet exemple active l’exécution pas à pas, puis exécute un script qui affiche les nombres 1, 2 et 3.</span><span class="sxs-lookup"><span data-stu-id="c6a47-118">This example turns on stepping, and then runs a script that displays the numbers 1, 2, and 3.</span></span>

```powershell
Set-PSDebug -Step; foreach ($i in 1..3) {$i}
```

```Output
Continue with this operation?
   1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
DEBUG:    1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
1
2
3
```

### <span data-ttu-id="c6a47-119">Exemple 3 : utiliser le mode strict</span><span class="sxs-lookup"><span data-stu-id="c6a47-119">Example 3: Use strict mode</span></span>

<span data-ttu-id="c6a47-120">Cet exemple met PowerShell en mode strict et tente d’accéder à une variable qui n’a pas de valeur assignée.</span><span class="sxs-lookup"><span data-stu-id="c6a47-120">This example puts PowerShell in strict mode and attempts to access a variable that doesn't have an assigned value.</span></span>

```powershell
Set-PSDebug -Strict; $NewVar
```

```Output
The variable '$NewVar' cannot be retrieved because it has not been set.
At line:1 char:22
+ Set-PSDebug -Strict; $NewVar
```

### <span data-ttu-id="c6a47-121">Exemple 4 : désactiver les fonctionnalités de débogage</span><span class="sxs-lookup"><span data-stu-id="c6a47-121">Example 4: Turn off debug features</span></span>

<span data-ttu-id="c6a47-122">Cet exemple désactive toutes les fonctionnalités de débogage, puis exécute un script qui affiche les nombres 1, 2 et 3.</span><span class="sxs-lookup"><span data-stu-id="c6a47-122">This example turns off all debugging features, and then runs a script that displays the numbers 1, 2, and 3.</span></span>

```powershell
Set-PSDebug -Off; foreach ($i in 1..3) {$i}
```

```Output
1
2
3
```

## <span data-ttu-id="c6a47-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c6a47-123">PARAMETERS</span></span>

### <span data-ttu-id="c6a47-124">-Désactivé</span><span class="sxs-lookup"><span data-stu-id="c6a47-124">-Off</span></span>

<span data-ttu-id="c6a47-125">Désactive toutes les fonctionnalités de débogage du script.</span><span class="sxs-lookup"><span data-stu-id="c6a47-125">Turns off all script debugging features.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: off
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6a47-126">-Étape</span><span class="sxs-lookup"><span data-stu-id="c6a47-126">-Step</span></span>

<span data-ttu-id="c6a47-127">Active l'exécution pas à pas du script.</span><span class="sxs-lookup"><span data-stu-id="c6a47-127">Turns on script stepping.</span></span> <span data-ttu-id="c6a47-128">Avant l’exécution de chaque ligne, PowerShell vous invite à arrêter, continuer ou entrer un nouveau niveau d’interpréteur pour inspecter l’état du script.</span><span class="sxs-lookup"><span data-stu-id="c6a47-128">Before each line runs, PowerShell prompts you to stop, continue, or enter a new interpreter level to inspect the state of the script.</span></span>

<span data-ttu-id="c6a47-129">La spécification du paramètre **Step** définit automatiquement le niveau de trace `1` .</span><span class="sxs-lookup"><span data-stu-id="c6a47-129">Specifying the **Step** parameter automatically sets a trace level of `1`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6a47-130">-Strict</span><span class="sxs-lookup"><span data-stu-id="c6a47-130">-Strict</span></span>

<span data-ttu-id="c6a47-131">Spécifie qu’une valeur doit être assignée aux variables avant d’être référencées dans un script.</span><span class="sxs-lookup"><span data-stu-id="c6a47-131">Specifies that variables must be assigned a value before being referenced in a script.</span></span> <span data-ttu-id="c6a47-132">Si une variable est référencée avant qu’une valeur ne soit affectée, PowerShell retourne une erreur d’exception.</span><span class="sxs-lookup"><span data-stu-id="c6a47-132">If a variable is referenced before a value is assigned, PowerShell returns an exception error.</span></span> <span data-ttu-id="c6a47-133">Ceci équivaut à `Set-StrictMode -Version 1`.</span><span class="sxs-lookup"><span data-stu-id="c6a47-133">This is equivalent to `Set-StrictMode -Version 1`.</span></span> <span data-ttu-id="c6a47-134">Pour plus d’informations, consultez [Set-StrictMode](Set-StrictMode.md).</span><span class="sxs-lookup"><span data-stu-id="c6a47-134">For more information, see [Set-StrictMode](Set-StrictMode.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6a47-135">-Trace</span><span class="sxs-lookup"><span data-stu-id="c6a47-135">-Trace</span></span>

<span data-ttu-id="c6a47-136">Spécifie le niveau de trace pour chaque ligne dans un script.</span><span class="sxs-lookup"><span data-stu-id="c6a47-136">Specifies the trace level for each line in a script.</span></span> <span data-ttu-id="c6a47-137">Chaque ligne est tracée au fur et à mesure de son exécution.</span><span class="sxs-lookup"><span data-stu-id="c6a47-137">Each line is traced as it's run.</span></span>

<span data-ttu-id="c6a47-138">Les valeurs acceptables pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6a47-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c6a47-139">0 : désactivez le suivi de script.</span><span class="sxs-lookup"><span data-stu-id="c6a47-139">0: Turn script tracing off.</span></span>
- <span data-ttu-id="c6a47-140">1 : suivre les lignes de script à mesure qu’elles s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="c6a47-140">1: Trace script lines as they run.</span></span>
- <span data-ttu-id="c6a47-141">2 : suivi des lignes de script, des affectations de variables, des appels de fonction et des scripts.</span><span class="sxs-lookup"><span data-stu-id="c6a47-141">2: Trace script lines, variable assignments, function calls, and scripts.</span></span>

```yaml
Type: System.Int32
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6a47-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c6a47-142">CommonParameters</span></span>

<span data-ttu-id="c6a47-143">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c6a47-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c6a47-144">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c6a47-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c6a47-145">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c6a47-145">INPUTS</span></span>

### <span data-ttu-id="c6a47-146">None</span><span class="sxs-lookup"><span data-stu-id="c6a47-146">None</span></span>

<span data-ttu-id="c6a47-147">Vous ne pouvez pas effectuer de pipeline d’entrée pour cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c6a47-147">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="c6a47-148">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c6a47-148">OUTPUTS</span></span>

### <span data-ttu-id="c6a47-149">None</span><span class="sxs-lookup"><span data-stu-id="c6a47-149">None</span></span>

<span data-ttu-id="c6a47-150">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="c6a47-150">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="c6a47-151">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c6a47-151">NOTES</span></span>

## <span data-ttu-id="c6a47-152">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c6a47-152">RELATED LINKS</span></span>

[<span data-ttu-id="c6a47-153">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="c6a47-153">about_Debuggers</span></span>](./About/about_Debuggers.md)

[<span data-ttu-id="c6a47-154">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="c6a47-154">Debug-Process</span></span>](../Microsoft.PowerShell.Management/Debug-Process.md)

[<span data-ttu-id="c6a47-155">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c6a47-155">Set-PSBreakpoint</span></span>](../Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)

[<span data-ttu-id="c6a47-156">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="c6a47-156">Set-StrictMode</span></span>](Set-StrictMode.md)

[<span data-ttu-id="c6a47-157">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="c6a47-157">Write-Debug</span></span>](../Microsoft.PowerShell.Utility/Write-Debug.md)

