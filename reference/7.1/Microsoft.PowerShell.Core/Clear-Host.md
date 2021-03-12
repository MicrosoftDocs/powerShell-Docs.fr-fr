---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: 7f1481c34c22d3fdface82828b6c3afbbbd6fce0
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193884"
---
# <span data-ttu-id="4e233-103">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="4e233-103">Clear-Host</span></span>

## <span data-ttu-id="4e233-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4e233-104">SYNOPSIS</span></span>

<span data-ttu-id="4e233-105">Efface l'affichage dans le programme hôte.</span><span class="sxs-lookup"><span data-stu-id="4e233-105">Clears the display in the host program.</span></span>

## <span data-ttu-id="4e233-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e233-106">SYNTAX</span></span>

```
Clear-Host [<CommonParameters>]
```

## <span data-ttu-id="4e233-107">Description</span><span class="sxs-lookup"><span data-stu-id="4e233-107">DESCRIPTION</span></span>

<span data-ttu-id="4e233-108">La `Clear-Host` fonction supprime tout le texte de l’affichage actuel, y compris les commandes et la sortie qui ont pu être accumulées.</span><span class="sxs-lookup"><span data-stu-id="4e233-108">The `Clear-Host` function removes all text from the current display, including commands and output that might have accumulated.</span></span> <span data-ttu-id="4e233-109">Une fois la fonction terminée, l'invite de commandes apparaît.</span><span class="sxs-lookup"><span data-stu-id="4e233-109">When complete, it displays the command prompt.</span></span> <span data-ttu-id="4e233-110">Vous pouvez utiliser le nom de la fonction ou son alias, `cls` .</span><span class="sxs-lookup"><span data-stu-id="4e233-110">You can use the function name or its alias, `cls`.</span></span>

<span data-ttu-id="4e233-111">`Clear-Host` affecte uniquement l’affichage actuel.</span><span class="sxs-lookup"><span data-stu-id="4e233-111">`Clear-Host` affects only the current display.</span></span> <span data-ttu-id="4e233-112">Elle ne supprime ni les résultats enregistrés ni les éléments de la session.</span><span class="sxs-lookup"><span data-stu-id="4e233-112">It does not delete saved results or remove any items from the session.</span></span> <span data-ttu-id="4e233-113">Les éléments spécifiques à la session, comme les variables et les fonctions, ne sont pas affectés par cette fonction.</span><span class="sxs-lookup"><span data-stu-id="4e233-113">Session-specific items, such as variables and functions, are not affected by this function.</span></span>

<span data-ttu-id="4e233-114">Étant donné que le comportement de la `Clear-Host` fonction est déterminé par le programme hôte, `Clear-Host` peut fonctionner différemment dans différents programmes hôtes.</span><span class="sxs-lookup"><span data-stu-id="4e233-114">Because the behavior of the `Clear-Host` function is determined by the host program, `Clear-Host` might work differently in different host programs.</span></span>

## <span data-ttu-id="4e233-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4e233-115">EXAMPLES</span></span>

### <span data-ttu-id="4e233-116">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="4e233-116">Example 1</span></span>

```
# Before

PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    843      33    14428      22556    99    17.41   1688 CcmExec
     44       6     2196       4964    52     0.23    692 conhost
    646      12     2332       4896    49     1.12    388 csrss
    189      11     2860       7084   114     0.66   2896 csrss
     78      11     1876       4008    42     0.22   4000 csrss
     76       7     1848       5064    54     0.08   1028 dwm
    610      41    23952      44048   208     4.40   2080 explorer
      0       0        0         24     0               0 Idle
    182      32     7692      15980    91     0.23   3056 LogonUI
    186      25     7832      16068    91     0.27   3996 LogonUI
   1272      32    11512      20432    58    25.07    548 lsass
    267      10     3536       6736    34     0.80    556 lsm
    137      17     3520       7472    61     0.05   1220 msdtc
    447      31    70316      84476   201 1,429.67    836 MsMpEng
    265      18     7136      15628   134     2.20   3544 msseces
    248      16     6476       4076    76     0.22   1592 NisSrv
    368      25    61312      65508   614     1.78    848 powershell
    101       8     2304       6624    70     0.64   3648 rdpclip
    258      15     6804      12156    50     2.65    536 services
...

PS C:\> cls
#After

PS C:>
```

<span data-ttu-id="4e233-117">Cette commande utilise l' `cls` alias de `Clear-Host` pour effacer l’affichage actuel.</span><span class="sxs-lookup"><span data-stu-id="4e233-117">This command uses the `cls` alias of `Clear-Host` to clear the current display.</span></span>

## <span data-ttu-id="4e233-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e233-118">PARAMETERS</span></span>

### <span data-ttu-id="4e233-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e233-119">CommonParameters</span></span>
<span data-ttu-id="4e233-120">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e233-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e233-121">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4e233-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e233-122">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4e233-122">INPUTS</span></span>

### <span data-ttu-id="4e233-123">Aucun</span><span class="sxs-lookup"><span data-stu-id="4e233-123">None</span></span>

<span data-ttu-id="4e233-124">Vous ne pouvez pas diriger d’entrée vers `Clear-Host` .</span><span class="sxs-lookup"><span data-stu-id="4e233-124">You cannot pipe input to `Clear-Host`.</span></span>

## <span data-ttu-id="4e233-125">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4e233-125">OUTPUTS</span></span>

### <span data-ttu-id="4e233-126">Aucun</span><span class="sxs-lookup"><span data-stu-id="4e233-126">None</span></span>

<span data-ttu-id="4e233-127">`Clear-Host` ne génère pas de sortie</span><span class="sxs-lookup"><span data-stu-id="4e233-127">`Clear-Host` does not generate any output</span></span>

## <span data-ttu-id="4e233-128">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4e233-128">NOTES</span></span>

<span data-ttu-id="4e233-129">`Clear-Host` est une fonction simple, et non une fonction avancée.</span><span class="sxs-lookup"><span data-stu-id="4e233-129">`Clear-Host` is a simple function, not an advanced function.</span></span> <span data-ttu-id="4e233-130">Par conséquent, vous ne pouvez pas utiliser de paramètres communs, tels que **Debug**, dans une `Clear-Host` commande.</span><span class="sxs-lookup"><span data-stu-id="4e233-130">As such, you cannot use common parameters, such as **Debug**, in a `Clear-Host` command.</span></span>

## <span data-ttu-id="4e233-131">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4e233-131">RELATED LINKS</span></span>

[<span data-ttu-id="4e233-132">Get-Host</span><span class="sxs-lookup"><span data-stu-id="4e233-132">Get-Host</span></span>](../Microsoft.PowerShell.Utility/Get-Host.md)

[<span data-ttu-id="4e233-133">Out-Host</span><span class="sxs-lookup"><span data-stu-id="4e233-133">Out-Host</span></span>](Out-Host.md)

[<span data-ttu-id="4e233-134">Read-Host</span><span class="sxs-lookup"><span data-stu-id="4e233-134">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)

[<span data-ttu-id="4e233-135">Write-Host</span><span class="sxs-lookup"><span data-stu-id="4e233-135">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)

