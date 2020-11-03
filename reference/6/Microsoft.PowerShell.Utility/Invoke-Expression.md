---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: 575f696d74e6a7aa7cf864cbb559f15a25ac1a66
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203769"
---
# <span data-ttu-id="c4c00-103">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="c4c00-103">Invoke-Expression</span></span>

## <span data-ttu-id="c4c00-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c4c00-104">SYNOPSIS</span></span>
<span data-ttu-id="c4c00-105">Exécute des commandes ou des expressions sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c4c00-105">Runs commands or expressions on the local computer.</span></span>

## <span data-ttu-id="c4c00-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c4c00-106">SYNTAX</span></span>

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## <span data-ttu-id="c4c00-107">Description</span><span class="sxs-lookup"><span data-stu-id="c4c00-107">DESCRIPTION</span></span>

<span data-ttu-id="c4c00-108">L' `Invoke-Expression` applet de commande évalue ou exécute une chaîne spécifiée en tant que commande et retourne les résultats de l’expression ou de la commande.</span><span class="sxs-lookup"><span data-stu-id="c4c00-108">The `Invoke-Expression` cmdlet evaluates or runs a specified string as a command and returns the results of the expression or command.</span></span> <span data-ttu-id="c4c00-109">Sans `Invoke-Expression` , une chaîne envoyée à la ligne de commande est retournée (en écho) inchangée.</span><span class="sxs-lookup"><span data-stu-id="c4c00-109">Without `Invoke-Expression`, a string submitted at the command line is returned (echoed) unchanged.</span></span>

<span data-ttu-id="c4c00-110">Les expressions sont évaluées et exécutées dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="c4c00-110">Expressions are evaluated and run in the current scope.</span></span> <span data-ttu-id="c4c00-111">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="c4c00-111">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="c4c00-112">Prenez des précautions raisonnables lors de l’utilisation `Invoke-Expression` de l’applet de commande dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="c4c00-112">Take reasonable precautions when using the `Invoke-Expression` cmdlet in scripts.</span></span> <span data-ttu-id="c4c00-113">Lorsque vous utilisez `Invoke-Expression` pour exécuter une commande entrée par l’utilisateur, vérifiez que la commande peut être exécutée en toute sécurité avant de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="c4c00-113">When using `Invoke-Expression` to run a command that the user enters, verify that the command is safe to run before running it.</span></span> <span data-ttu-id="c4c00-114">En général, il est préférable de concevoir votre script avec des options d'entrée prédéfinies, plutôt que d'autoriser des entrées libres.</span><span class="sxs-lookup"><span data-stu-id="c4c00-114">In general, it is best to design your script with predefined input options, rather than allowing freeform input.</span></span>

## <span data-ttu-id="c4c00-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c4c00-115">EXAMPLES</span></span>

### <span data-ttu-id="c4c00-116">Exemple 1 : évaluer une expression</span><span class="sxs-lookup"><span data-stu-id="c4c00-116">Example 1: Evaluate an expression</span></span>

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

<span data-ttu-id="c4c00-117">Cet exemple illustre l’utilisation de `Invoke-Expression` pour évaluer une expression.</span><span class="sxs-lookup"><span data-stu-id="c4c00-117">This example demonstrates the use of `Invoke-Expression` to evaluate an expression.</span></span> <span data-ttu-id="c4c00-118">Sans `Invoke-Expression` , l’expression est imprimée, mais pas évaluée.</span><span class="sxs-lookup"><span data-stu-id="c4c00-118">Without `Invoke-Expression`, the expression is printed, but not evaluated.</span></span>

<span data-ttu-id="c4c00-119">La première commande attribue une valeur `Get-Process` (une chaîne) à la `$Command` variable.</span><span class="sxs-lookup"><span data-stu-id="c4c00-119">The first command assigns a value of `Get-Process` (a string) to the `$Command` variable.</span></span>

<span data-ttu-id="c4c00-120">La deuxième commande illustre le résultat de l'entrée du nom de la variable sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c00-120">The second command shows the effect of typing the variable name at the command line.</span></span> <span data-ttu-id="c4c00-121">PowerShell renvoie la chaîne.</span><span class="sxs-lookup"><span data-stu-id="c4c00-121">PowerShell echoes the string.</span></span>

<span data-ttu-id="c4c00-122">La troisième commande utilise `Invoke-Expression` pour évaluer la chaîne.</span><span class="sxs-lookup"><span data-stu-id="c4c00-122">The third command uses `Invoke-Expression` to evaluate the string.</span></span>

### <span data-ttu-id="c4c00-123">Exemple 2 : exécuter un script sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="c4c00-123">Example 2: Run a script on the local computer</span></span>

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

<span data-ttu-id="c4c00-124">Ces commandes utilisent `Invoke-Expression` pour exécuter un script, TestScript.ps1, sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c4c00-124">These commands use `Invoke-Expression` to run a script, TestScript.ps1, on the local computer.</span></span> <span data-ttu-id="c4c00-125">Les deux commandes sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="c4c00-125">The two commands are equivalent.</span></span> <span data-ttu-id="c4c00-126">La première utilise le paramètre **Command** pour spécifier la commande à exécuter.</span><span class="sxs-lookup"><span data-stu-id="c4c00-126">The first uses the **Command** parameter to specify the command to run.</span></span>
<span data-ttu-id="c4c00-127">La seconde utilise un opérateur de pipeline ( `|` ) pour envoyer la chaîne de commande à `Invoke-Expression` .</span><span class="sxs-lookup"><span data-stu-id="c4c00-127">The second uses a pipeline operator (`|`) to send the command string to `Invoke-Expression`.</span></span>

### <span data-ttu-id="c4c00-128">Exemple 3 : exécuter une commande dans une variable</span><span class="sxs-lookup"><span data-stu-id="c4c00-128">Example 3: Run a command in a variable</span></span>

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

<span data-ttu-id="c4c00-129">Cet exemple exécute une chaîne de commande enregistrée dans la `$Command` variable.</span><span class="sxs-lookup"><span data-stu-id="c4c00-129">This example runs a command string that is saved in the `$Command` variable.</span></span>

<span data-ttu-id="c4c00-130">La chaîne de commande est placée entre guillemets simples, car elle comprend une variable, `$_` , qui représente l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="c4c00-130">The command string is enclosed in single quotation marks because it includes a variable, `$_`, which represents the current object.</span></span> <span data-ttu-id="c4c00-131">S’il est placé entre guillemets doubles, la `$_` variable est remplacée par sa valeur avant d’être enregistrée dans la `$Command` variable.</span><span class="sxs-lookup"><span data-stu-id="c4c00-131">If it were enclosed in double quotation marks, the `$_` variable would be replaced by its value before it was saved in the `$Command` variable.</span></span>

### <span data-ttu-id="c4c00-132">Exemple 4 : obtenir et exécuter un exemple d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="c4c00-132">Example 4: Get and run a cmdlet Help example</span></span>

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

<span data-ttu-id="c4c00-133">Cette commande récupère et exécute le premier exemple de la `Get-EventLog` rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c00-133">This command retrieves and runs the first example in the `Get-EventLog` cmdlet Help topic.</span></span>

<span data-ttu-id="c4c00-134">Pour exécuter un exemple d’une autre applet de commande, remplacez la valeur de la `$Cmdlet_name` variable par le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4c00-134">To run an example of a different cmdlet, change the value of the `$Cmdlet_name` variable to the name of the cmdlet.</span></span> <span data-ttu-id="c4c00-135">Et, remplacez la `$Example_number` variable par l’exemple de numéro que vous souhaitez exécuter.</span><span class="sxs-lookup"><span data-stu-id="c4c00-135">And, change the `$Example_number` variable to the example number you want to run.</span></span> <span data-ttu-id="c4c00-136">La commande échoue si le numéro de l’exemple n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c4c00-136">The command fails if the example number is not valid.</span></span>

## <span data-ttu-id="c4c00-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c4c00-137">PARAMETERS</span></span>

### <span data-ttu-id="c4c00-138">-Command</span><span class="sxs-lookup"><span data-stu-id="c4c00-138">-Command</span></span>

<span data-ttu-id="c4c00-139">Spécifie la commande ou l'expression à exécuter.</span><span class="sxs-lookup"><span data-stu-id="c4c00-139">Specifies the command or expression to run.</span></span> <span data-ttu-id="c4c00-140">Tapez la commande ou l'expression, ou entrez une variable qui contient la commande ou l'expression.</span><span class="sxs-lookup"><span data-stu-id="c4c00-140">Type the command or expression or enter a variable that contains the command or expression.</span></span> <span data-ttu-id="c4c00-141">Le paramètre **Command** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c4c00-141">The **Command** parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c4c00-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4c00-142">CommonParameters</span></span>

<span data-ttu-id="c4c00-143">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c4c00-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4c00-144">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="c4c00-144">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c4c00-145">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c4c00-145">INPUTS</span></span>

### <span data-ttu-id="c4c00-146">System. String ou PSObject</span><span class="sxs-lookup"><span data-stu-id="c4c00-146">System.String or PSObject</span></span>

<span data-ttu-id="c4c00-147">Vous pouvez diriger un objet qui représente la commande vers `Invoke-Expression` .</span><span class="sxs-lookup"><span data-stu-id="c4c00-147">You can pipe an object that represents the command to `Invoke-Expression`.</span></span>
<span data-ttu-id="c4c00-148">Utilisez la `$Input` variable Automatic pour représenter les objets d’entrée de la commande.</span><span class="sxs-lookup"><span data-stu-id="c4c00-148">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="c4c00-149">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c4c00-149">OUTPUTS</span></span>

### <span data-ttu-id="c4c00-150">PSObject</span><span class="sxs-lookup"><span data-stu-id="c4c00-150">PSObject</span></span>

<span data-ttu-id="c4c00-151">Retourne la sortie générée par la commande appelée (la valeur du paramètre de **commande** ).</span><span class="sxs-lookup"><span data-stu-id="c4c00-151">Returns the output that is generated by the invoked command (the value of the **Command** parameter).</span></span>

## <span data-ttu-id="c4c00-152">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c4c00-152">NOTES</span></span>

<span data-ttu-id="c4c00-153">Dans la plupart des cas, vous appelez des expressions à l’aide de l’opérateur d’appel de PowerShell et obtenez les mêmes résultats.</span><span class="sxs-lookup"><span data-stu-id="c4c00-153">In most cases, you invoke expressions using PowerShell's call operator and achieve the same results.</span></span>
<span data-ttu-id="c4c00-154">L’opérateur d’appel est une méthode plus sûre.</span><span class="sxs-lookup"><span data-stu-id="c4c00-154">The call operator is a safer method.</span></span> <span data-ttu-id="c4c00-155">Pour plus d’informations, consultez [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-).</span><span class="sxs-lookup"><span data-stu-id="c4c00-155">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-).</span></span>

## <span data-ttu-id="c4c00-156">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c4c00-156">RELATED LINKS</span></span>

[<span data-ttu-id="c4c00-157">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="c4c00-157">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="c4c00-158">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="c4c00-158">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)
