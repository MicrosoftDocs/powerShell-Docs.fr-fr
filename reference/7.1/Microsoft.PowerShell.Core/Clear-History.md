---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: c159262b21e39965f32db4a0fa736aa70de8e916
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202114"
---
# <span data-ttu-id="4dcf7-103">Clear-History</span><span class="sxs-lookup"><span data-stu-id="4dcf7-103">Clear-History</span></span>

## <span data-ttu-id="4dcf7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4dcf7-104">SYNOPSIS</span></span>
<span data-ttu-id="4dcf7-105">Supprime des entrées de l’historique de commande de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-105">Deletes entries from the PowerShell session command history.</span></span>

## <span data-ttu-id="4dcf7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4dcf7-106">SYNTAX</span></span>

### <span data-ttu-id="4dcf7-107">IDParameter (par défaut)</span><span class="sxs-lookup"><span data-stu-id="4dcf7-107">IDParameter (Default)</span></span>

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4dcf7-108">CommandLineParameter</span><span class="sxs-lookup"><span data-stu-id="4dcf7-108">CommandLineParameter</span></span>

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## <span data-ttu-id="4dcf7-109">Description</span><span class="sxs-lookup"><span data-stu-id="4dcf7-109">DESCRIPTION</span></span>

<span data-ttu-id="4dcf7-110">`Clear-History` supprime l’historique de commande d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-110">`Clear-History` deletes the command history from a PowerShell session.</span></span> <span data-ttu-id="4dcf7-111">Chaque session PowerShell a son propre historique de commande.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-111">Each PowerShell session has its own command history.</span></span> <span data-ttu-id="4dcf7-112">Pour afficher l’historique des commandes, utilisez l’applet de commande `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-112">To display the command history, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="4dcf7-113">Par défaut, `Clear-History` supprime l’intégralité de l’historique des commandes d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-113">By default, `Clear-History` deletes the entire command history from a PowerShell session.</span></span> <span data-ttu-id="4dcf7-114">Vous pouvez utiliser des paramètres avec `Clear-History` pour supprimer des commandes sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-114">You can use parameters with `Clear-History` to delete selected commands.</span></span>

<span data-ttu-id="4dcf7-115">`Clear-History` n’efface pas le `PSReadLine` fichier d’historique de commandes.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-115">`Clear-History` does not clear the `PSReadLine` command history file.</span></span> <span data-ttu-id="4dcf7-116">Le `PSReadLine` module stocke un fichier d’historique qui contient chaque commande PowerShell de chaque session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-116">The `PSReadLine` module stores a history file that contains every PowerShell command from every PowerShell session.</span></span> <span data-ttu-id="4dcf7-117">À partir d’une invite PowerShell, utilisez les flèches vers le haut et vers le bas de votre clavier pour faire défiler l’historique des commandes.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-117">From a PowerShell prompt, use the up and down arrows on your keyboard to scroll through the command history.</span></span> <span data-ttu-id="4dcf7-118">Pour afficher la `PSReadLine` configuration de l’historique des commandes, utilisez `Get-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-118">To display the `PSReadLine` configuration for command history, use `Get-PSReadLineOption`.</span></span>
<span data-ttu-id="4dcf7-119">`PSReadLine` fourni avec PowerShell 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-119">`PSReadLine` shipped with PowerShell 5.0 and above.</span></span> <span data-ttu-id="4dcf7-120">Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="4dcf7-120">For more information, see [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="4dcf7-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4dcf7-121">EXAMPLES</span></span>

### <span data-ttu-id="4dcf7-122">Exemple 1 : supprimer l’historique de commande d’une session PowerShell</span><span class="sxs-lookup"><span data-stu-id="4dcf7-122">Example 1: Delete the command history from a PowerShell session</span></span>

<span data-ttu-id="4dcf7-123">Cette commande supprime toutes les commandes de l’historique d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-123">This command deletes all of the commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

<span data-ttu-id="4dcf7-124">L' `Get-History` applet de commande affiche l’historique de la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-124">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="4dcf7-125">`Clear-History` supprime l’intégralité de l’historique de la commande.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-125">`Clear-History` deletes the entire command history.</span></span> <span data-ttu-id="4dcf7-126">`Get-History` affiche l’historique de commande mis à jour et confirme que l’historique précédent a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-126">`Get-History` displays the updated command history and confirms the prior history was deleted.</span></span>

### <span data-ttu-id="4dcf7-127">Exemple 2 : supprimer les commandes les plus récentes</span><span class="sxs-lookup"><span data-stu-id="4dcf7-127">Example 2: Delete the newest commands</span></span>

<span data-ttu-id="4dcf7-128">Cette commande utilise les paramètres **Count** et latentes les plus **récents** pour supprimer les commandes les plus récentes de l’historique d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-128">This command uses the **Count** and **Newest** parameters to delete the newest commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

<span data-ttu-id="4dcf7-129">L' `Get-History` applet de commande affiche l’historique de la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-129">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="4dcf7-130">`Clear-History` est utilisé pour supprimer l’historique de la commande.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-130">`Clear-History` is used to delete the command history.</span></span> <span data-ttu-id="4dcf7-131">Le paramètre **Count** indique le nombre de commandes à supprimer, y compris l' **ID** spécifié. Le paramètre le plus **récent** spécifie que les commandes les plus récentes sont effacées de l’historique.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-131">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id** . The **Newest** parameter specifies that the newest commands are cleared from the history.</span></span> <span data-ttu-id="4dcf7-132">`Get-History`affiche l’historique de commande mis à jour et confirme que les cinq commandes les plus récentes ont été supprimées, **ID 6**  -  **ID 10** .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-132">`Get-History` displays the updated command history and confirms that the five newest commands were deleted, **Id 6** - **Id 10** .</span></span>

### <span data-ttu-id="4dcf7-133">Exemple 3 : supprimer des commandes qui correspondent à des critères spécifiques</span><span class="sxs-lookup"><span data-stu-id="4dcf7-133">Example 3: Delete commands that match specific criteria</span></span>

<span data-ttu-id="4dcf7-134">Cette commande supprime les commandes qui correspondent à des critères spécifiques définis par le paramètre **CommandLine** .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-134">This command deletes commands that match specific criteria defined by the **CommandLine** parameter.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

<span data-ttu-id="4dcf7-135">L' `Get-History` applet de commande affiche l’historique de la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-135">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="4dcf7-136">`Clear-History` supprime l’historique de la commande.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-136">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="4dcf7-137">Le paramètre **CommandLine** spécifie les commandes qui contiennent de **l’aide** ou terminent la **syntaxe** .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-137">The **CommandLine** parameter specifies commands that contain **Help** or end with **Syntax** .</span></span> <span data-ttu-id="4dcf7-138">`Get-History` affiche l’historique de commande mis à jour et confirme que les commandes **ID 3** , **ID 5** , **ID 6** et **ID 7** ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-138">`Get-History` displays the updated command history and confirms that commands **Id 3** , **Id 5** , **Id 6** , and **Id 7** were deleted.</span></span>

### <span data-ttu-id="4dcf7-139">Exemple 4 : supprimer des commandes par numéro d’identification</span><span class="sxs-lookup"><span data-stu-id="4dcf7-139">Example 4: Delete commands by Id number</span></span>

<span data-ttu-id="4dcf7-140">Cette commande supprime les éléments d’historique spécifiques à l’aide de l' **ID** . Pour supprimer plusieurs commandes, soumettez une liste de numéros d' **ID** séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-140">This command deletes specific history items using the **Id** . To delete multiple commands, submit a comma-separated list of **Id** numbers.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

<span data-ttu-id="4dcf7-141">L' `Get-History` applet de commande affiche l’historique de la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-141">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="4dcf7-142">`Clear-History` supprime l’historique de la commande.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-142">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="4dcf7-143">Le paramètre **ID** spécifie les commandes à supprimer.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-143">The **Id** parameter specifies which commands to delete.</span></span> <span data-ttu-id="4dcf7-144">`Get-History` affiche l’historique de commande mis à jour et confirme que l' **ID 3** et l' **ID 5** ont été supprimés.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-144">`Get-History` displays the updated command history and confirms that **Id 3** and **Id 5** were deleted.</span></span>

### <span data-ttu-id="4dcf7-145">Exemple 5 : supprimer les commandes par numéro et nombre d’ID</span><span class="sxs-lookup"><span data-stu-id="4dcf7-145">Example 5: Delete commands by Id number and count</span></span>

<span data-ttu-id="4dcf7-146">Cette commande utilise les paramètres **ID** et **Count** pour supprimer l’historique des commandes.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-146">This command uses the **Id** and **Count** parameters to delete command history.</span></span> <span data-ttu-id="4dcf7-147">Les commandes sont supprimées de l' **ID** spécifié dans l’ordre inverse, du plus récent au plus ancien.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-147">Commands are deleted from the specified **Id** in reverse order, newest to oldest.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

<span data-ttu-id="4dcf7-148">L' `Get-History` applet de commande affiche l’historique de la session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-148">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="4dcf7-149">`Clear-History` supprime l’historique de la commande.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-149">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="4dcf7-150">Le paramètre **ID** spécifie de commencer par l' **ID 7** .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-150">The **Id** parameter specifies to begin with **Id 7** .</span></span> <span data-ttu-id="4dcf7-151">Le paramètre **Count** spécifie de supprimer cinq commandes, y compris l' **ID** spécifié. `Get-History`affiche l’historique de commande mis à jour et confirme que cinq commandes ont été supprimées, **ID 3**  -  **ID 7** .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-151">The **Count** parameter specifies to delete five commands, inclusive of the specified **Id** . `Get-History` displays the updated command history and confirms that five commands were deleted, **Id 3** - **Id 7** .</span></span>

## <span data-ttu-id="4dcf7-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4dcf7-152">PARAMETERS</span></span>

### <span data-ttu-id="4dcf7-153">-CommandLine</span><span class="sxs-lookup"><span data-stu-id="4dcf7-153">-CommandLine</span></span>

<span data-ttu-id="4dcf7-154">Supprime l’historique de commande d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-154">Deletes command history from a PowerShell session.</span></span> <span data-ttu-id="4dcf7-155">La chaîne doit être une correspondance exacte ou utiliser des caractères génériques pour faire correspondre les commandes dans l’historique de session PowerShell affiché par `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-155">The string must be an exact match or use wildcards to match commands in the PowerShell session history displayed by `Get-History`.</span></span> <span data-ttu-id="4dcf7-156">Si vous entrez plusieurs chaînes, supprime les `Clear-History` commandes qui correspondent à l’une des chaînes.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-156">If you enter more than one string, `Clear-History` deletes commands that match any of the strings.</span></span> <span data-ttu-id="4dcf7-157">Le paramètre **CommandLine** peut être utilisé avec **Count** .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-157">The **CommandLine** parameter can be used with **Count** .</span></span>

<span data-ttu-id="4dcf7-158">Pour les chaînes avec un espace, utilisez des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-158">For strings with a space, use single quotations.</span></span> <span data-ttu-id="4dcf7-159">Pour plus d’informations, consultez [about_Quoting_Rules](About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="4dcf7-159">For more information, see [about_Quoting_Rules](About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4dcf7-160">-Nombre</span><span class="sxs-lookup"><span data-stu-id="4dcf7-160">-Count</span></span>

<span data-ttu-id="4dcf7-161">Spécifie le nombre d’entrées d’historique que `Clear-History` supprime.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-161">Specifies the number of history entries that `Clear-History` deletes.</span></span> <span data-ttu-id="4dcf7-162">Les commandes sont supprimées dans l’ordre, en commençant par l’entrée la plus ancienne dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-162">Commands are deleted in order, beginning with the oldest entry in the history.</span></span>

<span data-ttu-id="4dcf7-163">Les paramètres **Count** et **ID** peuvent être utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-163">The **Count** and **Id** parameters can be used together.</span></span> <span data-ttu-id="4dcf7-164">Le paramètre **Count** indique le nombre de commandes à supprimer, y compris l' **ID** spécifié. À partir de l' **ID** spécifié, les commandes sont supprimées dans l’ordre séquentiel inverse.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-164">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id** . Beginning at the specified **Id** , commands are deleted in reverse sequential order.</span></span> <span data-ttu-id="4dcf7-165">Par exemple, si l' **ID** est 30 et que le **nombre** est 10, `Clear-History` supprime les éléments 21 à 30.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-165">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 21 through 30.</span></span>

<span data-ttu-id="4dcf7-166">Les paramètres **Count** et **CommandLine** peuvent être utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-166">The **Count** and **CommandLine** parameters can be used together.</span></span> <span data-ttu-id="4dcf7-167">**Nombre** spécifie le nombre de commandes à supprimer qui correspondent à la valeur du paramètre de **ligne** de commande.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-167">**Count** specifies the number of commands to delete that match **CommandLine** parameter value.</span></span> <span data-ttu-id="4dcf7-168">Les commandes sont supprimées dans un ordre séquentiel.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-168">The commands are deleted in sequential order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4dcf7-169">-Id</span><span class="sxs-lookup"><span data-stu-id="4dcf7-169">-Id</span></span>

<span data-ttu-id="4dcf7-170">Spécifie l' **ID** d’historique de commande que `Clear-History` supprime.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-170">Specifies the command history **Id** that `Clear-History` deletes.</span></span> <span data-ttu-id="4dcf7-171">Pour afficher les numéros d' **identification** , utilisez l’applet de commande `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-171">To display **Id** numbers, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="4dcf7-172">Les numéros d' **identification** sont séquentiels et les commandes conservent leur numéro d' **identification** tout au long d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-172">The **Id** numbers are sequential and commands keep their **Id** number throughout a PowerShell session.</span></span> <span data-ttu-id="4dcf7-173">Le paramètre **ID** peut être utilisé avec **Count** et le plus **récent** .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-173">The **Id** parameter can be used with **Count** and **Newest** .</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4dcf7-174">-Plus récent</span><span class="sxs-lookup"><span data-stu-id="4dcf7-174">-Newest</span></span>

<span data-ttu-id="4dcf7-175">Lorsque le paramètre le plus **récent** est utilisé, `Clear-History` supprime les entrées les plus récentes de l’historique.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-175">When the **Newest** parameter is used, `Clear-History` deletes the newest entries in the history.</span></span> <span data-ttu-id="4dcf7-176">Par défaut, `Clear-History` supprime les entrées les plus anciennes dans l’historique.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-176">By default, `Clear-History` deletes the oldest entries in the history.</span></span>

<span data-ttu-id="4dcf7-177">Le paramètre le plus **récent** peut être utilisé avec l' **ID** et le **nombre** .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-177">The **Newest** parameter can be used with **Id** and **Count** .</span></span> <span data-ttu-id="4dcf7-178">Le paramètre **Count** indique le nombre de commandes à supprimer, y compris l' **ID** spécifié. À partir de l' **ID** spécifié, les commandes sont supprimées dans l’ordre séquentiel.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-178">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id** . Beginning at the specified **Id** , commands are deleted in sequential order.</span></span> <span data-ttu-id="4dcf7-179">Par exemple, si l' **ID** est 30 et que le **nombre** est 10, `Clear-History` supprime les éléments de 30 à 39.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-179">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 30 through 39.</span></span>

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

### <span data-ttu-id="4dcf7-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4dcf7-180">-Confirm</span></span>

<span data-ttu-id="4dcf7-181">Vous invite à confirmer l’exécution de l' `Clear-History` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-181">Prompts you for confirmation before running the `Clear-History` cmdlet.</span></span>

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

### <span data-ttu-id="4dcf7-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4dcf7-182">-WhatIf</span></span>

<span data-ttu-id="4dcf7-183">Montre ce qui se passe si l’applet de commande `Clear-History` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-183">Shows what would happen if the `Clear-History` cmdlet runs.</span></span> <span data-ttu-id="4dcf7-184">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4dcf7-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4dcf7-185">CommonParameters</span></span>

<span data-ttu-id="4dcf7-186">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4dcf7-187">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="4dcf7-187">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4dcf7-188">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4dcf7-188">INPUTS</span></span>

### <span data-ttu-id="4dcf7-189">Aucun</span><span class="sxs-lookup"><span data-stu-id="4dcf7-189">None</span></span>

<span data-ttu-id="4dcf7-190">Vous ne pouvez pas diriger d’objets vers `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-190">You cannot pipe objects to `Clear-History`.</span></span>

## <span data-ttu-id="4dcf7-191">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4dcf7-191">OUTPUTS</span></span>

### <span data-ttu-id="4dcf7-192">Aucun</span><span class="sxs-lookup"><span data-stu-id="4dcf7-192">None</span></span>

<span data-ttu-id="4dcf7-193">`Clear-History` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-193">`Clear-History` does not generate any output.</span></span>

## <span data-ttu-id="4dcf7-194">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4dcf7-194">NOTES</span></span>

<span data-ttu-id="4dcf7-195">L’historique de session PowerShell est une liste des commandes entrées au cours d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-195">The PowerShell session history is a list of the commands entered during a PowerShell session.</span></span> <span data-ttu-id="4dcf7-196">Vous pouvez afficher l'historique, ajouter et supprimer des commandes, et exécuter des commandes à partir de l'historique.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-196">You can view the history, add and delete commands, and run commands from the history.</span></span> <span data-ttu-id="4dcf7-197">Pour plus d’informations, consultez [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="4dcf7-197">For more information, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="4dcf7-198">L’historique de session est géré séparément de l’historique géré par le module **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="4dcf7-198">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="4dcf7-199">Les deux historiques sont disponibles dans les sessions où **PSReadLine** est chargé.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-199">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="4dcf7-200">Cette applet de commande fonctionne uniquement avec l’historique de session.</span><span class="sxs-lookup"><span data-stu-id="4dcf7-200">This cmdlet only works with the session history.</span></span> <span data-ttu-id="4dcf7-201">Pour plus d’informations, consultez [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="4dcf7-201">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="4dcf7-202">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4dcf7-202">RELATED LINKS</span></span>

[<span data-ttu-id="4dcf7-203">about_History</span><span class="sxs-lookup"><span data-stu-id="4dcf7-203">about_History</span></span>](About/about_History.md)

[<span data-ttu-id="4dcf7-204">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="4dcf7-204">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="4dcf7-205">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="4dcf7-205">about_Quoting_Rules</span></span>](About/about_Quoting_Rules.md)

[<span data-ttu-id="4dcf7-206">Add-History</span><span class="sxs-lookup"><span data-stu-id="4dcf7-206">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="4dcf7-207">Get-History</span><span class="sxs-lookup"><span data-stu-id="4dcf7-207">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="4dcf7-208">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="4dcf7-208">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="4dcf7-209">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="4dcf7-209">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="4dcf7-210">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="4dcf7-210">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)

