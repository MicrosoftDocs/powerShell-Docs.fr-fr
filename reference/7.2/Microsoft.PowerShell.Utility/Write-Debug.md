---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 3d23f76dbf8e1c9a21805a4914038c8c4f319852
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596518"
---
# <span data-ttu-id="48455-102">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="48455-102">Write-Debug</span></span>

## <span data-ttu-id="48455-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="48455-103">SYNOPSIS</span></span>
<span data-ttu-id="48455-104">Écrit un message de débogage dans la console.</span><span class="sxs-lookup"><span data-stu-id="48455-104">Writes a debug message to the console.</span></span>

## <span data-ttu-id="48455-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="48455-105">SYNTAX</span></span>

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="48455-106">Description</span><span class="sxs-lookup"><span data-stu-id="48455-106">DESCRIPTION</span></span>

<span data-ttu-id="48455-107">L' `Write-Debug` applet de commande écrit des messages de débogage sur l’hôte à partir d’un script ou d’une commande.</span><span class="sxs-lookup"><span data-stu-id="48455-107">The `Write-Debug` cmdlet writes debug messages to the host from a script or command.</span></span>

<span data-ttu-id="48455-108">Par défaut, les messages de débogage ne s’affichent pas dans la console, mais vous pouvez les afficher à l’aide du paramètre **Debug** ou de la `$DebugPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="48455-108">By default, debug messages are not displayed in the console, but you can display them by using the **Debug** parameter or the `$DebugPreference` variable.</span></span>

## <span data-ttu-id="48455-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="48455-109">EXAMPLES</span></span>

### <span data-ttu-id="48455-110">Exemple 1 : comprendre $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="48455-110">Example 1: Understand $DebugPreference</span></span>

<span data-ttu-id="48455-111">Cet exemple écrit un message de débogage.</span><span class="sxs-lookup"><span data-stu-id="48455-111">This example writes a debug message.</span></span>

```powershell
Write-Debug "Cannot open file."
```

<span data-ttu-id="48455-112">La valeur par défaut de `$DebugPreference` est **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="48455-112">The default value of `$DebugPreference` is **SilentlyContinue**.</span></span> <span data-ttu-id="48455-113">Par conséquent, le message ne s’affiche pas dans la console.</span><span class="sxs-lookup"><span data-stu-id="48455-113">Therefore, the message is not displayed in the console.</span></span>

### <span data-ttu-id="48455-114">Exemple 2 : modifier la valeur de $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="48455-114">Example 2: Change the value of $DebugPreference</span></span>

<span data-ttu-id="48455-115">Cet exemple montre l’effet de la modification de la valeur de la `$DebugPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="48455-115">This example shows the effect of changing the value of the `$DebugPreference` variable.</span></span> <span data-ttu-id="48455-116">Tout d’abord, nous affichons la valeur actuelle de `$DebugPreference` et nous tentons d’écrire un message de débogage.</span><span class="sxs-lookup"><span data-stu-id="48455-116">First, we display the current value of `$DebugPreference` and attempt to write a debug message.</span></span> <span data-ttu-id="48455-117">Ensuite, nous modifions la valeur de `$DebugPreference` pour **Continuer**, ce qui permet d’afficher les messages de débogage.</span><span class="sxs-lookup"><span data-stu-id="48455-117">Then we change the value of `$DebugPreference` to **Continue**, which allows debug messages to be displayed.</span></span>

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

<span data-ttu-id="48455-118">Pour plus d’informations sur `$DebugPreference` , consultez [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span><span class="sxs-lookup"><span data-stu-id="48455-118">For more information about `$DebugPreference`, see [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span></span>

### <span data-ttu-id="48455-119">Exemple 3 : utiliser le paramètre Debug pour remplacer $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="48455-119">Example 3: Use the Debug parameter to override $DebugPreference</span></span>

<span data-ttu-id="48455-120">La `Test-Debug` fonction écrit la valeur de la `$DebugPreference` variable dans l’hôte PowerShell et dans le flux de débogage.</span><span class="sxs-lookup"><span data-stu-id="48455-120">The `Test-Debug` function writes the value of the `$DebugPreference` variable to the PowerShell host and to the Debug stream.</span></span> <span data-ttu-id="48455-121">Dans cet exemple, nous utilisons le paramètre **Debug** pour remplacer la `$DebugPreference` valeur.</span><span class="sxs-lookup"><span data-stu-id="48455-121">In this example, we use the **Debug** parameter to override the `$DebugPreference` value.</span></span>

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

<span data-ttu-id="48455-122">Notez que la valeur de `$DebugPreference` change quand vous utilisez le paramètre **Debug** .</span><span class="sxs-lookup"><span data-stu-id="48455-122">Notice that the value of `$DebugPreference` changes when you use the **Debug** parameter.</span></span> <span data-ttu-id="48455-123">Cette modification affecte uniquement l’étendue de la fonction.</span><span class="sxs-lookup"><span data-stu-id="48455-123">This change only affects the scope of the function.</span></span> <span data-ttu-id="48455-124">La valeur n’est pas affectée en dehors de la fonction.</span><span class="sxs-lookup"><span data-stu-id="48455-124">The value is not affected outside the function.</span></span>

<span data-ttu-id="48455-125">Pour plus d’informations sur le paramètre commun de **débogage** , consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="48455-125">For more information about the **Debug** common parameter, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="48455-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="48455-126">PARAMETERS</span></span>

### <span data-ttu-id="48455-127">-Message</span><span class="sxs-lookup"><span data-stu-id="48455-127">-Message</span></span>

<span data-ttu-id="48455-128">Spécifie le message de débogage à envoyer à la console.</span><span class="sxs-lookup"><span data-stu-id="48455-128">Specifies the debug message to send to the console.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="48455-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="48455-129">CommonParameters</span></span>

<span data-ttu-id="48455-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="48455-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="48455-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="48455-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="48455-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="48455-132">INPUTS</span></span>

### <span data-ttu-id="48455-133">System.String</span><span class="sxs-lookup"><span data-stu-id="48455-133">System.String</span></span>

<span data-ttu-id="48455-134">Vous pouvez diriger une chaîne qui contient un message de débogage vers `Write-Debug` .</span><span class="sxs-lookup"><span data-stu-id="48455-134">You can pipe a string that contains a debug message to `Write-Debug`.</span></span>

## <span data-ttu-id="48455-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="48455-135">OUTPUTS</span></span>

### <span data-ttu-id="48455-136">None</span><span class="sxs-lookup"><span data-stu-id="48455-136">None</span></span>

<span data-ttu-id="48455-137">`Write-Debug` écrit uniquement dans le flux de débogage.</span><span class="sxs-lookup"><span data-stu-id="48455-137">`Write-Debug` only writes to the debug stream.</span></span> <span data-ttu-id="48455-138">Il n’écrit pas d’objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="48455-138">It does not write any objects to the pipeline.</span></span>

## <span data-ttu-id="48455-139">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="48455-139">NOTES</span></span>

## <span data-ttu-id="48455-140">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="48455-140">RELATED LINKS</span></span>

[<span data-ttu-id="48455-141">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="48455-141">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="48455-142">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="48455-142">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="48455-143">Write-Error</span><span class="sxs-lookup"><span data-stu-id="48455-143">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="48455-144">Write-Host</span><span class="sxs-lookup"><span data-stu-id="48455-144">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="48455-145">Write-Output</span><span class="sxs-lookup"><span data-stu-id="48455-145">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="48455-146">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="48455-146">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="48455-147">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="48455-147">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="48455-148">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="48455-148">Write-Warning</span></span>](Write-Warning.md)
