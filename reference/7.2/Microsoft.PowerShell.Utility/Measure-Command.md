---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 0c2346dc7177e091c0921cd4775422938305e2be
ms.sourcegitcommit: 165d10405d9db3a68c417a239d3181378fd02b9b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "99596105"
---
# <span data-ttu-id="78812-102">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="78812-102">Measure-Command</span></span>

## <span data-ttu-id="78812-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="78812-103">SYNOPSIS</span></span>
<span data-ttu-id="78812-104">Mesure le temps nécessaire pour exécuter des applets de commande et des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="78812-104">Measures the time it takes to run script blocks and cmdlets.</span></span>

## <span data-ttu-id="78812-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="78812-105">SYNTAX</span></span>

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="78812-106">Description</span><span class="sxs-lookup"><span data-stu-id="78812-106">DESCRIPTION</span></span>

<span data-ttu-id="78812-107">L' `Measure-Command` applet de commande exécute un bloc de script ou une applet de commande en interne, le temps d’exécution de l’opération et retourne la durée d’exécution.</span><span class="sxs-lookup"><span data-stu-id="78812-107">The `Measure-Command` cmdlet runs a script block or cmdlet internally, times the execution of the operation, and returns the execution time.</span></span>

> [!NOTE]
> <span data-ttu-id="78812-108">Les blocs de script s’exécutent `Measure-Command` dans l’étendue actuelle, et non dans une portée enfant.</span><span class="sxs-lookup"><span data-stu-id="78812-108">Script blocks run by `Measure-Command` run in the current scope, not a child scope.</span></span>

## <span data-ttu-id="78812-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="78812-109">EXAMPLES</span></span>

### <span data-ttu-id="78812-110">Exemple 1 : mesurer une commande</span><span class="sxs-lookup"><span data-stu-id="78812-110">Example 1: Measure a command</span></span>

<span data-ttu-id="78812-111">Cet exemple mesure le temps nécessaire à l’exécution d’une `Get-EventLog` commande qui obtient les événements dans le journal des événements Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78812-111">This example measures the time it takes to run a `Get-EventLog` command that gets the events in the Windows PowerShell event log.</span></span>

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### <span data-ttu-id="78812-112">Exemple 2 : Comparaison de deux sorties à partir de Measure-Command</span><span class="sxs-lookup"><span data-stu-id="78812-112">Example 2: Compare two outputs from Measure-Command</span></span>

<span data-ttu-id="78812-113">La première commande mesure le temps nécessaire pour traiter une `Get-ChildItem` commande récursive qui utilise le paramètre **path** pour obtenir uniquement les `.txt` fichiers du `C:\Windows` répertoire et de ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="78812-113">The first command measures the time it takes to process a recursive `Get-ChildItem` command that uses the **Path** parameter to get only `.txt` files in the `C:\Windows` directory and its subdirectories.</span></span>

<span data-ttu-id="78812-114">La deuxième commande mesure le temps nécessaire pour traiter une `Get-ChildItem` commande récursive qui utilise le paramètre spécifique au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="78812-114">The second command measures the time it takes to process a recursive `Get-ChildItem` command that uses the provider-specific \` parameter.</span></span>

<span data-ttu-id="78812-115">Ces commandes montrent la valeur de l’utilisation d’un filtre spécifique au fournisseur dans les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78812-115">These commands show the value of using a provider-specific filter in PowerShell commands.</span></span>

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### <span data-ttu-id="78812-116">Exemple 3 : entrée de canalisation dans Measure-Command</span><span class="sxs-lookup"><span data-stu-id="78812-116">Example 3: Piping input to Measure-Command</span></span>

<span data-ttu-id="78812-117">Les objets qui sont dirigés vers `Measure-Command` sont disponibles pour le bloc de script qui est passé au paramètre d' **expression** .</span><span class="sxs-lookup"><span data-stu-id="78812-117">Objects that are piped to `Measure-Command` are available to the script block that is passed to the **Expression** parameter.</span></span> <span data-ttu-id="78812-118">Le bloc de script est exécuté une fois pour chaque objet sur le pipeline.</span><span class="sxs-lookup"><span data-stu-id="78812-118">The script block is executed once for each object on the pipeline.</span></span>

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### <span data-ttu-id="78812-119">Exemple 4 : affichage de la sortie de la commande mesurée</span><span class="sxs-lookup"><span data-stu-id="78812-119">Example 4: Displaying output of measured command</span></span>

<span data-ttu-id="78812-120">Pour afficher la sortie de l’expression dans, `Measure-Command` vous pouvez utiliser un canal vers `Out-Default` .</span><span class="sxs-lookup"><span data-stu-id="78812-120">To display output of expression in `Measure-Command` you can use a pipe to `Out-Default`.</span></span>

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### <span data-ttu-id="78812-121">Exemple 5 : mesure de l’exécution dans une étendue enfant</span><span class="sxs-lookup"><span data-stu-id="78812-121">Example 5: Measuring execution in a child scope</span></span>

<span data-ttu-id="78812-122">`Measure-Command` exécute le bloc de script dans l’étendue actuelle, afin que le bloc de script puisse modifier les valeurs dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="78812-122">`Measure-Command` runs the script block in the current scope, so the script block can modify values in the current scope.</span></span> <span data-ttu-id="78812-123">Pour éviter toute modification de l’étendue actuelle, vous devez encapsuler le bloc de script entre accolades ( `{}` ) et utiliser l’opérateur d’appel ( `&` ) pour exécuter le bloc dans une portée enfant.</span><span class="sxs-lookup"><span data-stu-id="78812-123">To avoid changes to the current scope, you must wrap the script block in braces (`{}`) and use the invocation operator (`&`) to execute the block in a child scope.</span></span>

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

<span data-ttu-id="78812-124">Pour plus d’informations sur l’opérateur d’appel, consultez [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).</span><span class="sxs-lookup"><span data-stu-id="78812-124">For more information about the invocation operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).</span></span>

## <span data-ttu-id="78812-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="78812-125">PARAMETERS</span></span>

### <span data-ttu-id="78812-126">-Expression</span><span class="sxs-lookup"><span data-stu-id="78812-126">-Expression</span></span>

<span data-ttu-id="78812-127">Spécifie l'expression à chronométrer.</span><span class="sxs-lookup"><span data-stu-id="78812-127">Specifies the expression that is being timed.</span></span> <span data-ttu-id="78812-128">Mettez l’expression entre accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="78812-128">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="78812-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="78812-129">-InputObject</span></span>

<span data-ttu-id="78812-130">Les objets liés au paramètre **InputObject** sont des entrées facultatives pour le bloc de script passé au paramètre **expression** .</span><span class="sxs-lookup"><span data-stu-id="78812-130">Objects bound to the **InputObject** parameter are optional input for the script block passed to the **Expression** parameter.</span></span> <span data-ttu-id="78812-131">Dans le bloc de script, `$_` peut être utilisé pour référencer l’objet actuel dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="78812-131">Inside the script block, `$_` can be used to reference the current object in the pipeline.</span></span>

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

### <span data-ttu-id="78812-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="78812-132">CommonParameters</span></span>

<span data-ttu-id="78812-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="78812-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="78812-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="78812-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="78812-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="78812-135">INPUTS</span></span>

### <span data-ttu-id="78812-136">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="78812-136">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="78812-137">Vous pouvez diriger un objet vers `Measure-Command` .</span><span class="sxs-lookup"><span data-stu-id="78812-137">You can pipe an object to `Measure-Command`.</span></span>

## <span data-ttu-id="78812-138">SORTIES</span><span class="sxs-lookup"><span data-stu-id="78812-138">OUTPUTS</span></span>

### <span data-ttu-id="78812-139">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="78812-139">System.TimeSpan</span></span>

<span data-ttu-id="78812-140">`Measure-Command` retourne un objet d’intervalle de temps qui représente le résultat.</span><span class="sxs-lookup"><span data-stu-id="78812-140">`Measure-Command` returns a time span object that represents the result.</span></span>

## <span data-ttu-id="78812-141">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="78812-141">NOTES</span></span>

## <span data-ttu-id="78812-142">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="78812-142">RELATED LINKS</span></span>

[<span data-ttu-id="78812-143">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="78812-143">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="78812-144">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="78812-144">Trace-Command</span></span>](Trace-Command.md)

