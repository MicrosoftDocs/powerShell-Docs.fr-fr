---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 7fb4341a84706f7d31d463bb527a1a31f387c2ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599160"
---
# <span data-ttu-id="9410e-102">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="9410e-102">Invoke-History</span></span>

## <span data-ttu-id="9410e-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9410e-103">SYNOPSIS</span></span>
<span data-ttu-id="9410e-104">Exécute des commandes à partir de l'historique de session.</span><span class="sxs-lookup"><span data-stu-id="9410e-104">Runs commands from the session history.</span></span>

## <span data-ttu-id="9410e-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="9410e-105">SYNTAX</span></span>

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9410e-106">Description</span><span class="sxs-lookup"><span data-stu-id="9410e-106">DESCRIPTION</span></span>

<span data-ttu-id="9410e-107">L' `Invoke-History` applet de commande exécute des commandes à partir de l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="9410e-107">The `Invoke-History` cmdlet runs commands from the session history.</span></span> <span data-ttu-id="9410e-108">Vous pouvez passer des objets représentant les commandes de Get-History à `Invoke-History` ou vous pouvez identifier les commandes dans l’historique actuel à l’aide de leur numéro d' **identification** .</span><span class="sxs-lookup"><span data-stu-id="9410e-108">You can pass objects representing the commands from Get-History to `Invoke-History`, or you can identify commands in the current history by using their **Id** number.</span></span> <span data-ttu-id="9410e-109">Pour rechercher le numéro d’identification d’une commande, utilisez l’applet de commande `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="9410e-109">To find the identification number of a command, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="9410e-110">L’historique de session est géré séparément de l’historique géré par le module **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="9410e-110">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="9410e-111">Les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé.</span><span class="sxs-lookup"><span data-stu-id="9410e-111">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="9410e-112">Cette applet de commande fonctionne uniquement avec l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="9410e-112">This cmdlet only works with the session history.</span></span> <span data-ttu-id="9410e-113">Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="9410e-113">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="9410e-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9410e-114">EXAMPLES</span></span>

### <span data-ttu-id="9410e-115">Exemple 1 : exécuter la commande la plus récente dans l’historique</span><span class="sxs-lookup"><span data-stu-id="9410e-115">Example 1: Run the most recent command in the history</span></span>

<span data-ttu-id="9410e-116">Cet exemple exécute la dernière commande, ou la plus récente, dans l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="9410e-116">This example runs the last, or most recent, command in the session history.</span></span> <span data-ttu-id="9410e-117">Vous pouvez abréger cette commande en tant que `r` , l’alias de `Invoke-History` .</span><span class="sxs-lookup"><span data-stu-id="9410e-117">You can abbreviate this command as `r`, the alias for `Invoke-History`.</span></span>

```powershell
Invoke-History
```

### <span data-ttu-id="9410e-118">Exemple 2 : exécuter la commande avec un ID spécifié</span><span class="sxs-lookup"><span data-stu-id="9410e-118">Example 2: Run the command that has a specified ID</span></span>

<span data-ttu-id="9410e-119">Cet exemple exécute la commande dans l’historique de session avec l' **Id** 132.</span><span class="sxs-lookup"><span data-stu-id="9410e-119">This example runs the command in the session history with **Id** 132.</span></span> <span data-ttu-id="9410e-120">Étant donné que le nom du paramètre **ID** est facultatif, vous pouvez abréger cette commande comme suit : `Invoke-History 132` , `ihy 132` ou `r 132` .</span><span class="sxs-lookup"><span data-stu-id="9410e-120">Because the name of the **Id** parameter is optional, you can abbreviate this command as the following: `Invoke-History 132`, `ihy 132`, or `r 132`.</span></span>

```powershell
Invoke-History -Id 132
```

### <span data-ttu-id="9410e-121">Exemple 3 : exécuter la commande la plus récente à l’aide du texte de la commande</span><span class="sxs-lookup"><span data-stu-id="9410e-121">Example 3: Run the most recent command by using the command text</span></span>

<span data-ttu-id="9410e-122">Cet exemple exécute la commande la plus récente `Get-Process` dans l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="9410e-122">This example runs the most recent `Get-Process` command in the session history.</span></span> <span data-ttu-id="9410e-123">Lorsque vous tapez des caractères pour le paramètre **ID** , `Invoke-History` exécute la première commande trouvée qui correspond au modèle, en commençant par les commandes les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="9410e-123">When you type characters for the **Id** parameter, `Invoke-History` runs the first command that it finds that matches the pattern, starting with the most recent commands.</span></span>

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> <span data-ttu-id="9410e-124">Les critères spéciaux ne respectent pas la casse, mais le modèle correspond au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="9410e-124">Pattern matching is case-insensitive, but the pattern matches the beginning of the line.</span></span>

### <span data-ttu-id="9410e-125">Exemple 4 : exécuter une séquence de commandes à partir de l’historique</span><span class="sxs-lookup"><span data-stu-id="9410e-125">Example 4: Run a sequence of commands from the history</span></span>

<span data-ttu-id="9410e-126">Cet exemple exécute les commandes 16 à 24.</span><span class="sxs-lookup"><span data-stu-id="9410e-126">This example runs commands 16 through 24.</span></span> <span data-ttu-id="9410e-127">Étant donné que vous ne pouvez répertorier qu’une seule valeur d' **ID** , la commande utilise l' `ForEach-Object` applet de commande pour exécuter la `Invoke-History` commande une fois pour chaque valeur d' **ID** .</span><span class="sxs-lookup"><span data-stu-id="9410e-127">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command one time for each **Id** value.</span></span>

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### <span data-ttu-id="9410e-128">Exemple 5</span><span class="sxs-lookup"><span data-stu-id="9410e-128">Example 5</span></span>

<span data-ttu-id="9410e-129">Cet exemple exécute les sept commandes dans l’historique qui se terminent par la commande 255 (249 à 255).</span><span class="sxs-lookup"><span data-stu-id="9410e-129">This example runs the seven commands in the history that end with command 255 (249 through 255).</span></span> <span data-ttu-id="9410e-130">Elle utilise l' `Get-History` applet de commande pour récupérer les commandes.</span><span class="sxs-lookup"><span data-stu-id="9410e-130">It uses the `Get-History` cmdlet to retrieve the commands.</span></span> <span data-ttu-id="9410e-131">Étant donné que vous ne pouvez répertorier qu’une seule valeur d' **ID** , la commande utilise l' `ForEach-Object` applet de commande pour exécuter la `Invoke-History` commande une fois pour chaque valeur d' **ID** .</span><span class="sxs-lookup"><span data-stu-id="9410e-131">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command once for each **Id** value.</span></span>

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## <span data-ttu-id="9410e-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9410e-132">PARAMETERS</span></span>

### <span data-ttu-id="9410e-133">-Id</span><span class="sxs-lookup"><span data-stu-id="9410e-133">-Id</span></span>

<span data-ttu-id="9410e-134">Spécifie l' **ID** d’une commande dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="9410e-134">Specifies the **Id** of a command in the history.</span></span> <span data-ttu-id="9410e-135">Vous pouvez taper le numéro d' **identification** de la commande ou les premiers caractères de la commande.</span><span class="sxs-lookup"><span data-stu-id="9410e-135">You can type the **Id** number of the command or the first few characters of the command.</span></span>

<span data-ttu-id="9410e-136">Si vous tapez des caractères, `Invoke-History` correspond d’abord aux commandes les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="9410e-136">If you type characters, `Invoke-History` matches the most recent commands first.</span></span> <span data-ttu-id="9410e-137">Si vous omettez ce paramètre, `Invoke-History` exécute la dernière commande, ou la plus récente.</span><span class="sxs-lookup"><span data-stu-id="9410e-137">If you omit this parameter, `Invoke-History` runs the last, or most recent, command.</span></span> <span data-ttu-id="9410e-138">Pour rechercher le numéro d' **identification** d’une commande, utilisez l’applet de commande `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="9410e-138">To find the **Id** number of a command, use the `Get-History` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9410e-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9410e-139">-Confirm</span></span>

<span data-ttu-id="9410e-140">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9410e-140">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9410e-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9410e-141">-WhatIf</span></span>

<span data-ttu-id="9410e-142">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9410e-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9410e-143">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="9410e-143">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9410e-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9410e-144">CommonParameters</span></span>

<span data-ttu-id="9410e-145">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9410e-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9410e-146">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9410e-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9410e-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9410e-147">INPUTS</span></span>

### <span data-ttu-id="9410e-148">System.String</span><span class="sxs-lookup"><span data-stu-id="9410e-148">System.String</span></span>

<span data-ttu-id="9410e-149">Vous pouvez diriger un **ID** d’historique vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9410e-149">You can pipe a history **Id** to this cmdlet.</span></span>

## <span data-ttu-id="9410e-150">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9410e-150">OUTPUTS</span></span>

### <span data-ttu-id="9410e-151">None</span><span class="sxs-lookup"><span data-stu-id="9410e-151">None</span></span>

<span data-ttu-id="9410e-152">Cette applet de commande ne génère pas de sortie, mais la sortie peut être générée par les commandes qui `Invoke-History` s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="9410e-152">This cmdlet does not generate any output, but output might be generated by the commands that `Invoke-History` runs.</span></span>

## <span data-ttu-id="9410e-153">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9410e-153">NOTES</span></span>

<span data-ttu-id="9410e-154">L'historique de session est une liste des commandes entrées pendant la session.</span><span class="sxs-lookup"><span data-stu-id="9410e-154">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="9410e-155">L'historique de session représente l'ordre d'exécution, l'état et les heures de début et de fin de la commande.</span><span class="sxs-lookup"><span data-stu-id="9410e-155">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="9410e-156">Lorsque vous entrez chaque commande, PowerShell l’ajoute à l’historique afin que vous puissiez la réutiliser.</span><span class="sxs-lookup"><span data-stu-id="9410e-156">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="9410e-157">Pour plus d’informations sur l’historique de session, consultez [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="9410e-157">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="9410e-158">Vous pouvez également faire référence à `Invoke-History` par ses alias intégrés `r` et `ihy` .</span><span class="sxs-lookup"><span data-stu-id="9410e-158">You can also refer to `Invoke-History` by its built-in aliases, `r` and `ihy`.</span></span> <span data-ttu-id="9410e-159">Pour plus d’informations, consultez [about_Aliases](About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="9410e-159">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="9410e-160">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9410e-160">RELATED LINKS</span></span>

[<span data-ttu-id="9410e-161">Add-History</span><span class="sxs-lookup"><span data-stu-id="9410e-161">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="9410e-162">Clear-History</span><span class="sxs-lookup"><span data-stu-id="9410e-162">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="9410e-163">Get-History</span><span class="sxs-lookup"><span data-stu-id="9410e-163">Get-History</span></span>](Get-History.md)

