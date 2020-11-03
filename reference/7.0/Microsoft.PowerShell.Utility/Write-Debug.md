---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 3217a3c67c262f8061963fd1302c6782620e270d
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208505"
---
# <span data-ttu-id="b6c0c-103">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="b6c0c-103">Write-Debug</span></span>

## <span data-ttu-id="b6c0c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b6c0c-104">SYNOPSIS</span></span>
<span data-ttu-id="b6c0c-105">Écrit un message de débogage dans la console.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-105">Writes a debug message to the console.</span></span>

## <span data-ttu-id="b6c0c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b6c0c-106">SYNTAX</span></span>

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="b6c0c-107">Description</span><span class="sxs-lookup"><span data-stu-id="b6c0c-107">DESCRIPTION</span></span>

<span data-ttu-id="b6c0c-108">L' `Write-Debug` applet de commande écrit des messages de débogage sur l’hôte à partir d’un script ou d’une commande.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-108">The `Write-Debug` cmdlet writes debug messages to the host from a script or command.</span></span>

<span data-ttu-id="b6c0c-109">Par défaut, les messages de débogage ne s’affichent pas dans la console, mais vous pouvez les afficher à l’aide du paramètre **Debug** ou de la `$DebugPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-109">By default, debug messages are not displayed in the console, but you can display them by using the **Debug** parameter or the `$DebugPreference` variable.</span></span>

## <span data-ttu-id="b6c0c-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b6c0c-110">EXAMPLES</span></span>

### <span data-ttu-id="b6c0c-111">Exemple 1 : comprendre $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="b6c0c-111">Example 1: Understand $DebugPreference</span></span>

<span data-ttu-id="b6c0c-112">Cet exemple écrit un message de débogage.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-112">This example writes a debug message.</span></span>

```powershell
Write-Debug "Cannot open file."
```

<span data-ttu-id="b6c0c-113">La valeur par défaut de `$DebugPreference` est **SilentlyContinue** .</span><span class="sxs-lookup"><span data-stu-id="b6c0c-113">The default value of `$DebugPreference` is **SilentlyContinue** .</span></span> <span data-ttu-id="b6c0c-114">Par conséquent, le message ne s’affiche pas dans la console.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-114">Therefore, the message is not displayed in the console.</span></span>

### <span data-ttu-id="b6c0c-115">Exemple 2 : modifier la valeur de $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="b6c0c-115">Example 2: Change the value of $DebugPreference</span></span>

<span data-ttu-id="b6c0c-116">Cet exemple montre l’effet de la modification de la valeur de la `$DebugPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-116">This example shows the effect of changing the value of the `$DebugPreference` variable.</span></span> <span data-ttu-id="b6c0c-117">Tout d’abord, nous affichons la valeur actuelle de `$DebugPreference` et nous tentons d’écrire un message de débogage.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-117">First, we display the current value of `$DebugPreference` and attempt to write a debug message.</span></span> <span data-ttu-id="b6c0c-118">Ensuite, nous modifions la valeur de `$DebugPreference` pour **Continuer** , ce qui permet d’afficher les messages de débogage.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-118">Then we change the value of `$DebugPreference` to **Continue** , which allows debug messages to be displayed.</span></span>

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

<span data-ttu-id="b6c0c-119">Pour plus d’informations sur `$DebugPreference` , consultez [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span><span class="sxs-lookup"><span data-stu-id="b6c0c-119">For more information about `$DebugPreference`, see [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span></span>

### <span data-ttu-id="b6c0c-120">Exemple 3 : utiliser le paramètre Debug pour remplacer $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="b6c0c-120">Example 3: Use the Debug parameter to override $DebugPreference</span></span>

<span data-ttu-id="b6c0c-121">La `Test-Debug` fonction écrit la valeur de la `$DebugPreference` variable dans l’hôte PowerShell et dans le flux de débogage.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-121">The `Test-Debug` function writes the value of the `$DebugPreference` variable to the PowerShell host and to the Debug stream.</span></span> <span data-ttu-id="b6c0c-122">Dans cet exemple, nous utilisons le paramètre **Debug** pour remplacer la `$DebugPreference` valeur.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-122">In this example, we use the **Debug** parameter to override the `$DebugPreference` value.</span></span>

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

<span data-ttu-id="b6c0c-123">Notez que la valeur de `$DebugPreference` change quand vous utilisez le paramètre **Debug** .</span><span class="sxs-lookup"><span data-stu-id="b6c0c-123">Notice that the value of `$DebugPreference` changes when you use the **Debug** parameter.</span></span> <span data-ttu-id="b6c0c-124">Cette modification affecte uniquement l’étendue de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-124">This change only affects the scope of the function.</span></span> <span data-ttu-id="b6c0c-125">La valeur n’est pas affectée en dehors de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-125">The value is not affected outside the function.</span></span>

<span data-ttu-id="b6c0c-126">Pour plus d’informations sur le paramètre commun de **débogage** , consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b6c0c-126">For more information about the **Debug** common parameter, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b6c0c-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b6c0c-127">PARAMETERS</span></span>

### <span data-ttu-id="b6c0c-128">-Message</span><span class="sxs-lookup"><span data-stu-id="b6c0c-128">-Message</span></span>

<span data-ttu-id="b6c0c-129">Spécifie le message de débogage à envoyer à la console.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-129">Specifies the debug message to send to the console.</span></span>

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

### <span data-ttu-id="b6c0c-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b6c0c-130">CommonParameters</span></span>

<span data-ttu-id="b6c0c-131">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b6c0c-132">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b6c0c-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b6c0c-133">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b6c0c-133">INPUTS</span></span>

### <span data-ttu-id="b6c0c-134">System.String</span><span class="sxs-lookup"><span data-stu-id="b6c0c-134">System.String</span></span>

<span data-ttu-id="b6c0c-135">Vous pouvez diriger une chaîne qui contient un message de débogage vers `Write-Debug` .</span><span class="sxs-lookup"><span data-stu-id="b6c0c-135">You can pipe a string that contains a debug message to `Write-Debug`.</span></span>

## <span data-ttu-id="b6c0c-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b6c0c-136">OUTPUTS</span></span>

### <span data-ttu-id="b6c0c-137">Aucun</span><span class="sxs-lookup"><span data-stu-id="b6c0c-137">None</span></span>

<span data-ttu-id="b6c0c-138">`Write-Debug` écrit uniquement dans le flux de débogage.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-138">`Write-Debug` only writes to the debug stream.</span></span> <span data-ttu-id="b6c0c-139">Il n’écrit pas d’objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="b6c0c-139">It does not write any objects to the pipeline.</span></span>

## <span data-ttu-id="b6c0c-140">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b6c0c-140">NOTES</span></span>

## <span data-ttu-id="b6c0c-141">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b6c0c-141">RELATED LINKS</span></span>

[<span data-ttu-id="b6c0c-142">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="b6c0c-142">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="b6c0c-143">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="b6c0c-143">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="b6c0c-144">Écriture-erreur</span><span class="sxs-lookup"><span data-stu-id="b6c0c-144">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="b6c0c-145">Write-Host</span><span class="sxs-lookup"><span data-stu-id="b6c0c-145">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="b6c0c-146">Write-Output</span><span class="sxs-lookup"><span data-stu-id="b6c0c-146">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="b6c0c-147">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="b6c0c-147">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="b6c0c-148">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="b6c0c-148">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="b6c0c-149">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="b6c0c-149">Write-Warning</span></span>](Write-Warning.md)
