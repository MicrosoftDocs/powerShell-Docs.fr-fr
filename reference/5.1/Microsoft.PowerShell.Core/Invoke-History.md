---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 613b460678186380b518a0bc04abc426c1038a84
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202278"
---
# <span data-ttu-id="82226-103">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="82226-103">Invoke-History</span></span>

## <span data-ttu-id="82226-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="82226-104">SYNOPSIS</span></span>
<span data-ttu-id="82226-105">Exécute des commandes à partir de l'historique de session.</span><span class="sxs-lookup"><span data-stu-id="82226-105">Runs commands from the session history.</span></span>

## <span data-ttu-id="82226-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="82226-106">SYNTAX</span></span>

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="82226-107">Description</span><span class="sxs-lookup"><span data-stu-id="82226-107">DESCRIPTION</span></span>

<span data-ttu-id="82226-108">L' `Invoke-History` applet de commande exécute des commandes à partir de l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="82226-108">The `Invoke-History` cmdlet runs commands from the session history.</span></span> <span data-ttu-id="82226-109">Vous pouvez passer des objets représentant les commandes de Get-History à `Invoke-History` ou vous pouvez identifier les commandes dans l’historique actuel à l’aide de leur numéro d' **identification** .</span><span class="sxs-lookup"><span data-stu-id="82226-109">You can pass objects representing the commands from Get-History to `Invoke-History`, or you can identify commands in the current history by using their **Id** number.</span></span> <span data-ttu-id="82226-110">Pour rechercher le numéro d’identification d’une commande, utilisez l’applet de commande `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="82226-110">To find the identification number of a command, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="82226-111">L’historique de session est géré séparément de l’historique géré par le module **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="82226-111">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="82226-112">Les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé.</span><span class="sxs-lookup"><span data-stu-id="82226-112">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="82226-113">Cette applet de commande fonctionne uniquement avec l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="82226-113">This cmdlet only works with the session history.</span></span> <span data-ttu-id="82226-114">Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="82226-114">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="82226-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="82226-115">EXAMPLES</span></span>

### <span data-ttu-id="82226-116">Exemple 1 : exécuter la commande la plus récente dans l’historique</span><span class="sxs-lookup"><span data-stu-id="82226-116">Example 1: Run the most recent command in the history</span></span>

<span data-ttu-id="82226-117">Cet exemple exécute la dernière commande, ou la plus récente, dans l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="82226-117">This example runs the last, or most recent, command in the session history.</span></span> <span data-ttu-id="82226-118">Vous pouvez abréger cette commande en tant que `r` , l’alias de `Invoke-History` .</span><span class="sxs-lookup"><span data-stu-id="82226-118">You can abbreviate this command as `r`, the alias for `Invoke-History`.</span></span>

```powershell
Invoke-History
```

### <span data-ttu-id="82226-119">Exemple 2 : exécuter la commande avec un ID spécifié</span><span class="sxs-lookup"><span data-stu-id="82226-119">Example 2: Run the command that has a specified ID</span></span>

<span data-ttu-id="82226-120">Cet exemple exécute la commande dans l’historique de session avec l' **Id** 132.</span><span class="sxs-lookup"><span data-stu-id="82226-120">This example runs the command in the session history with **Id** 132.</span></span> <span data-ttu-id="82226-121">Étant donné que le nom du paramètre **ID** est facultatif, vous pouvez abréger cette commande comme suit : `Invoke-History 132` , `ihy 132` ou `r 132` .</span><span class="sxs-lookup"><span data-stu-id="82226-121">Because the name of the **Id** parameter is optional, you can abbreviate this command as the following: `Invoke-History 132`, `ihy 132`, or `r 132`.</span></span>

```powershell
Invoke-History -Id 132
```

### <span data-ttu-id="82226-122">Exemple 3 : exécuter la commande la plus récente à l’aide du texte de la commande</span><span class="sxs-lookup"><span data-stu-id="82226-122">Example 3: Run the most recent command by using the command text</span></span>

<span data-ttu-id="82226-123">Cet exemple exécute la commande la plus récente `Get-Process` dans l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="82226-123">This example runs the most recent `Get-Process` command in the session history.</span></span> <span data-ttu-id="82226-124">Lorsque vous tapez des caractères pour le paramètre **ID** , `Invoke-History` exécute la première commande trouvée qui correspond au modèle, en commençant par les commandes les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="82226-124">When you type characters for the **Id** parameter, `Invoke-History` runs the first command that it finds that matches the pattern, starting with the most recent commands.</span></span>

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> <span data-ttu-id="82226-125">Les critères spéciaux ne respectent pas la casse, mais le modèle correspond au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="82226-125">Pattern matching is case-insensitive, but the pattern matches the beginning of the line.</span></span>

### <span data-ttu-id="82226-126">Exemple 4 : exécuter une séquence de commandes à partir de l’historique</span><span class="sxs-lookup"><span data-stu-id="82226-126">Example 4: Run a sequence of commands from the history</span></span>

<span data-ttu-id="82226-127">Cet exemple exécute les commandes 16 à 24.</span><span class="sxs-lookup"><span data-stu-id="82226-127">This example runs commands 16 through 24.</span></span> <span data-ttu-id="82226-128">Étant donné que vous ne pouvez répertorier qu’une seule valeur d' **ID** , la commande utilise l' `ForEach-Object` applet de commande pour exécuter la `Invoke-History` commande une fois pour chaque valeur d' **ID** .</span><span class="sxs-lookup"><span data-stu-id="82226-128">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command one time for each **Id** value.</span></span>

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### <span data-ttu-id="82226-129">Exemple 5</span><span class="sxs-lookup"><span data-stu-id="82226-129">Example 5</span></span>

<span data-ttu-id="82226-130">Cet exemple exécute les sept commandes dans l’historique qui se terminent par la commande 255 (249 à 255).</span><span class="sxs-lookup"><span data-stu-id="82226-130">This example runs the seven commands in the history that end with command 255 (249 through 255).</span></span> <span data-ttu-id="82226-131">Elle utilise l' `Get-History` applet de commande pour récupérer les commandes.</span><span class="sxs-lookup"><span data-stu-id="82226-131">It uses the `Get-History` cmdlet to retrieve the commands.</span></span> <span data-ttu-id="82226-132">Étant donné que vous ne pouvez répertorier qu’une seule valeur d' **ID** , la commande utilise l' `ForEach-Object` applet de commande pour exécuter la `Invoke-History` commande une fois pour chaque valeur d' **ID** .</span><span class="sxs-lookup"><span data-stu-id="82226-132">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command once for each **Id** value.</span></span>

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## <span data-ttu-id="82226-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="82226-133">PARAMETERS</span></span>

### <span data-ttu-id="82226-134">-Id</span><span class="sxs-lookup"><span data-stu-id="82226-134">-Id</span></span>

<span data-ttu-id="82226-135">Spécifie l' **ID** d’une commande dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="82226-135">Specifies the **Id** of a command in the history.</span></span> <span data-ttu-id="82226-136">Vous pouvez taper le numéro d' **identification** de la commande ou les premiers caractères de la commande.</span><span class="sxs-lookup"><span data-stu-id="82226-136">You can type the **Id** number of the command or the first few characters of the command.</span></span>

<span data-ttu-id="82226-137">Si vous tapez des caractères, `Invoke-History` correspond d’abord aux commandes les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="82226-137">If you type characters, `Invoke-History` matches the most recent commands first.</span></span> <span data-ttu-id="82226-138">Si vous omettez ce paramètre, `Invoke-History` exécute la dernière commande, ou la plus récente.</span><span class="sxs-lookup"><span data-stu-id="82226-138">If you omit this parameter, `Invoke-History` runs the last, or most recent, command.</span></span> <span data-ttu-id="82226-139">Pour rechercher le numéro d' **identification** d’une commande, utilisez l’applet de commande `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="82226-139">To find the **Id** number of a command, use the `Get-History` cmdlet.</span></span>

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

### <span data-ttu-id="82226-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="82226-140">-Confirm</span></span>

<span data-ttu-id="82226-141">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82226-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="82226-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="82226-142">-WhatIf</span></span>

<span data-ttu-id="82226-143">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82226-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="82226-144">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="82226-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="82226-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82226-145">CommonParameters</span></span>

<span data-ttu-id="82226-146">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82226-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82226-147">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="82226-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82226-148">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="82226-148">INPUTS</span></span>

### <span data-ttu-id="82226-149">System.String</span><span class="sxs-lookup"><span data-stu-id="82226-149">System.String</span></span>

<span data-ttu-id="82226-150">Vous pouvez diriger un **ID** d’historique vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="82226-150">You can pipe a history **Id** to this cmdlet.</span></span>

## <span data-ttu-id="82226-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="82226-151">OUTPUTS</span></span>

### <span data-ttu-id="82226-152">Aucun</span><span class="sxs-lookup"><span data-stu-id="82226-152">None</span></span>

<span data-ttu-id="82226-153">Cette applet de commande ne génère pas de sortie, mais la sortie peut être générée par les commandes qui `Invoke-History` s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="82226-153">This cmdlet does not generate any output, but output might be generated by the commands that `Invoke-History` runs.</span></span>

## <span data-ttu-id="82226-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="82226-154">NOTES</span></span>

<span data-ttu-id="82226-155">L'historique de session est une liste des commandes entrées pendant la session.</span><span class="sxs-lookup"><span data-stu-id="82226-155">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="82226-156">L'historique de session représente l'ordre d'exécution, l'état et les heures de début et de fin de la commande.</span><span class="sxs-lookup"><span data-stu-id="82226-156">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="82226-157">Lorsque vous entrez chaque commande, PowerShell l’ajoute à l’historique afin que vous puissiez la réutiliser.</span><span class="sxs-lookup"><span data-stu-id="82226-157">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="82226-158">Pour plus d’informations sur l’historique de session, consultez [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="82226-158">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="82226-159">Vous pouvez également faire référence à `Invoke-History` par ses alias intégrés `r` et `ihy` .</span><span class="sxs-lookup"><span data-stu-id="82226-159">You can also refer to `Invoke-History` by its built-in aliases, `r` and `ihy`.</span></span> <span data-ttu-id="82226-160">Pour plus d’informations, consultez [about_Aliases](About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="82226-160">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="82226-161">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="82226-161">RELATED LINKS</span></span>

[<span data-ttu-id="82226-162">Add-History</span><span class="sxs-lookup"><span data-stu-id="82226-162">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="82226-163">Clear-History</span><span class="sxs-lookup"><span data-stu-id="82226-163">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="82226-164">Get-History</span><span class="sxs-lookup"><span data-stu-id="82226-164">Get-History</span></span>](Get-History.md)
