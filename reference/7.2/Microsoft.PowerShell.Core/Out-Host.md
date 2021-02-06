---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 4fefb133416b3db6c19c71a916d73fe00f86f3a4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598765"
---
# <span data-ttu-id="923da-102">Out-Host</span><span class="sxs-lookup"><span data-stu-id="923da-102">Out-Host</span></span>

## <span data-ttu-id="923da-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="923da-103">SYNOPSIS</span></span>
<span data-ttu-id="923da-104">Envoie la sortie vers la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="923da-104">Sends output to the command line.</span></span>

## <span data-ttu-id="923da-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="923da-105">SYNTAX</span></span>

### <span data-ttu-id="923da-106">Tous</span><span class="sxs-lookup"><span data-stu-id="923da-106">All</span></span>

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="923da-107">Description</span><span class="sxs-lookup"><span data-stu-id="923da-107">DESCRIPTION</span></span>

<span data-ttu-id="923da-108">L' `Out-Host` applet de commande envoie la sortie à l’hôte PowerShell pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="923da-108">The `Out-Host` cmdlet sends output to the PowerShell host for display.</span></span> <span data-ttu-id="923da-109">L'hôte affiche la sortie sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="923da-109">The host displays the output at the command line.</span></span> <span data-ttu-id="923da-110">Étant donné que `Out-Host` est la valeur par défaut, vous n’êtes pas obligé de la spécifier, sauf si vous souhaitez utiliser ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="923da-110">Because `Out-Host` is the default, you don't have to specify it unless you want to use its parameters.</span></span>

<span data-ttu-id="923da-111">`Out-Host` est ajouté automatiquement à chaque commande exécutée.</span><span class="sxs-lookup"><span data-stu-id="923da-111">`Out-Host` is automatically appended to every command that is executed.</span></span> <span data-ttu-id="923da-112">Elle transmet la sortie du pipeline à l’hôte qui exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="923da-112">It passes the output of the pipeline to the host executing the command.</span></span> <span data-ttu-id="923da-113">`Out-Host` ignore les séquences d’échappement ANSI.</span><span class="sxs-lookup"><span data-stu-id="923da-113">`Out-Host` ignores ANSI escape sequences.</span></span> <span data-ttu-id="923da-114">Les séquences d’échappement sont gérées par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="923da-114">The escape sequences are handled by the host.</span></span> <span data-ttu-id="923da-115">`Out-Host` passe des séquences d’échappement ANSI à l’hôte sans tenter de les interpréter ou de les modifier.</span><span class="sxs-lookup"><span data-stu-id="923da-115">`Out-Host` passes ANSI escape sequences to the host without trying to interpret or change them.</span></span>

## <span data-ttu-id="923da-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="923da-116">EXAMPLES</span></span>

### <span data-ttu-id="923da-117">Exemple 1 : afficher la sortie une page à la fois</span><span class="sxs-lookup"><span data-stu-id="923da-117">Example 1: Display output one page at a time</span></span>

<span data-ttu-id="923da-118">Cet exemple affiche les processus système une page à la fois.</span><span class="sxs-lookup"><span data-stu-id="923da-118">This example displays the system processes one page at a time.</span></span>

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="923da-119">`Get-Process` Obtient le système traite et envoie les objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="923da-119">`Get-Process` gets the system processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="923da-120">`Out-Host` utilise le paramètre de **pagination** pour afficher une page de données à la fois.</span><span class="sxs-lookup"><span data-stu-id="923da-120">`Out-Host` uses the **Paging** parameter to display one page of data at a time.</span></span>

### <span data-ttu-id="923da-121">Exemple 2 : utiliser une variable comme entrée</span><span class="sxs-lookup"><span data-stu-id="923da-121">Example 2: Use a variable as input</span></span>

<span data-ttu-id="923da-122">Cet exemple utilise des objets stockés dans une variable comme entrée pour `Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="923da-122">This example uses objects stored in a variable as the input for `Out-Host`.</span></span>

```powershell
$io = Get-History
Out-Host -InputObject $io
```

<span data-ttu-id="923da-123">`Get-History` Obtient l’historique de la session PowerShell et stocke les objets dans la `$io` variable.</span><span class="sxs-lookup"><span data-stu-id="923da-123">`Get-History` gets the PowerShell session's history, and stores the objects in the `$io` variable.</span></span>
<span data-ttu-id="923da-124">`Out-Host` utilise le paramètre **InputObject** pour spécifier la `$io` variable et afficher l’historique.</span><span class="sxs-lookup"><span data-stu-id="923da-124">`Out-Host` uses the **InputObject** parameter to specify the `$io` variable and displays the history.</span></span>

## <span data-ttu-id="923da-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="923da-125">PARAMETERS</span></span>

### <span data-ttu-id="923da-126">-InputObject</span><span class="sxs-lookup"><span data-stu-id="923da-126">-InputObject</span></span>

<span data-ttu-id="923da-127">Spécifie les objets qui sont écrits dans la console.</span><span class="sxs-lookup"><span data-stu-id="923da-127">Specifies the objects that are written to the console.</span></span> <span data-ttu-id="923da-128">Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.</span><span class="sxs-lookup"><span data-stu-id="923da-128">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="923da-129">-Pagination</span><span class="sxs-lookup"><span data-stu-id="923da-129">-Paging</span></span>

<span data-ttu-id="923da-130">Indique que `Out-Host` affiche une page de sortie à la fois et attend une entrée utilisateur avant l’affichage des pages restantes.</span><span class="sxs-lookup"><span data-stu-id="923da-130">Indicates that `Out-Host` displays one page of output at a time, and waits for user input before the remaining pages are displayed.</span></span> <span data-ttu-id="923da-131">Par défaut, toute la sortie est affichée sur une seule page.</span><span class="sxs-lookup"><span data-stu-id="923da-131">By default, all the output is displayed on a single page.</span></span> <span data-ttu-id="923da-132">La taille de la page est déterminée par les caractéristiques de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="923da-132">The page size is determined by the characteristics of the host.</span></span>

<span data-ttu-id="923da-133">Appuyez sur la barre d' <kbd>espace</kbd> pour afficher la page de sortie suivante ou la touche <kbd>entrée</kbd> pour afficher la ligne de sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="923da-133">Press the <kbd>Space</kbd> bar to display the next page of output or the <kbd>Enter</kbd> key to view the next line of output.</span></span> <span data-ttu-id="923da-134">Appuyez sur <kbd>Q</kbd> pour quitter.</span><span class="sxs-lookup"><span data-stu-id="923da-134">Press <kbd>Q</kbd> to quit.</span></span>

<span data-ttu-id="923da-135">La **pagination** est semblable à la commande **More** .</span><span class="sxs-lookup"><span data-stu-id="923da-135">**Paging** is similar to the **more** command.</span></span>

> [!NOTE]
> <span data-ttu-id="923da-136">Le paramètre de **pagination** n’est pas pris en charge par l’hôte ISE PowerShell.</span><span class="sxs-lookup"><span data-stu-id="923da-136">The **Paging** parameter isn't supported by the PowerShell ISE host.</span></span>

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

### <span data-ttu-id="923da-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="923da-137">CommonParameters</span></span>

<span data-ttu-id="923da-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="923da-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="923da-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="923da-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="923da-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="923da-140">INPUTS</span></span>

### <span data-ttu-id="923da-141">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="923da-141">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="923da-142">Vous pouvez envoyer des objets vers le dessous du pipeline `Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="923da-142">You can send objects down the pipeline to `Out-Host`.</span></span>

## <span data-ttu-id="923da-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="923da-143">OUTPUTS</span></span>

### <span data-ttu-id="923da-144">None</span><span class="sxs-lookup"><span data-stu-id="923da-144">None</span></span>

<span data-ttu-id="923da-145">`Out-Host` ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="923da-145">`Out-Host` doesn't generate any output.</span></span> <span data-ttu-id="923da-146">Elle envoie des objets à l’hôte pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="923da-146">It sends objects to the host for display.</span></span>

## <span data-ttu-id="923da-147">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="923da-147">NOTES</span></span>

<span data-ttu-id="923da-148">Le paramètre de **pagination** n’est pas pris en charge par tous les hôtes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="923da-148">The **Paging** parameter isn't supported by all PowerShell hosts.</span></span> <span data-ttu-id="923da-149">Par exemple, si vous utilisez le paramètre de **pagination** dans PowerShell ISE, l’erreur suivante s’affiche : `out-lineoutput : The method or operation is not implemented.`</span><span class="sxs-lookup"><span data-stu-id="923da-149">For example, if you use the **Paging** parameter in the PowerShell ISE, the following error is displayed: `out-lineoutput : The method or operation is not implemented.`</span></span>

<span data-ttu-id="923da-150">Les applets de commande qui contiennent le verbe **out** , `Out-` , ne mettent pas en forme les objets.</span><span class="sxs-lookup"><span data-stu-id="923da-150">The cmdlets that contain the **Out** verb, `Out-`, don't format objects.</span></span> <span data-ttu-id="923da-151">Ils affichent les objets et les envoient à la destination d’affichage spécifiée.</span><span class="sxs-lookup"><span data-stu-id="923da-151">They render objects and send them to the specified display destination.</span></span> <span data-ttu-id="923da-152">Si vous envoyez un objet non mis en forme à une applet de commande `Out-` , l’applet de commande l’envoie à une applet de commande de mise en forme avant de le restituer.</span><span class="sxs-lookup"><span data-stu-id="923da-152">If you send an unformatted object to an `Out-` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="923da-153">Les `Out-` applets de commande n’ont pas de paramètres pour les noms ou les chemins d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="923da-153">The `Out-` cmdlets don't have parameters for names or file paths.</span></span> <span data-ttu-id="923da-154">Pour envoyer des données à une `Out-` applet de commande, utilisez le pipeline pour envoyer la sortie d’une commande PowerShell à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="923da-154">To send data to an `Out-` cmdlet, use the pipeline to send a PowerShell command's output to the cmdlet.</span></span> <span data-ttu-id="923da-155">Ou vous pouvez stocker des données dans une variable et utiliser le paramètre **InputObject** pour transmettre les données à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="923da-155">Or, you can store data in a variable and use the **InputObject** parameter to pass the data to the cmdlet.</span></span>

<span data-ttu-id="923da-156">`Out-Host` envoie des données, mais ne produit pas d’objet de sortie.</span><span class="sxs-lookup"><span data-stu-id="923da-156">`Out-Host` sends data, but it doesn't produce any output objects.</span></span> <span data-ttu-id="923da-157">Si vous dirigez la sortie de `Out-Host` vers l’applet de commande `Get-Member` , `Get-Member` signale qu’aucun objet n’a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="923da-157">If you pipeline the output of `Out-Host` to the `Get-Member` cmdlet, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="923da-158">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="923da-158">RELATED LINKS</span></span>

[<span data-ttu-id="923da-159">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="923da-159">Clear-Host</span></span>](Clear-Host.md)

[<span data-ttu-id="923da-160">Out-Default</span><span class="sxs-lookup"><span data-stu-id="923da-160">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="923da-161">Out-File</span><span class="sxs-lookup"><span data-stu-id="923da-161">Out-File</span></span>](../Microsoft.PowerShell.Utility/Out-File.md)

[<span data-ttu-id="923da-162">Out-Null</span><span class="sxs-lookup"><span data-stu-id="923da-162">Out-Null</span></span>](Out-Null.md)

[<span data-ttu-id="923da-163">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="923da-163">Out-Printer</span></span>](../Microsoft.PowerShell.Utility/Out-Printer.md)

[<span data-ttu-id="923da-164">Out-String</span><span class="sxs-lookup"><span data-stu-id="923da-164">Out-String</span></span>](../Microsoft.PowerShell.Utility/Out-String.md)

[<span data-ttu-id="923da-165">Write-Host</span><span class="sxs-lookup"><span data-stu-id="923da-165">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)

