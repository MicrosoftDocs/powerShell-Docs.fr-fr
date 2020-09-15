---
ms.date: 08/03/2020
keywords: powershell,applet de commande
title: 'Annexe 1 : Alias de compatibilité'
ms.openlocfilehash: e5bd170fea6b6109d2ef4fd58863d6cc8a0e3ae1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758497"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="74fb2-103">Annexe 1 - Alias de compatibilité</span><span class="sxs-lookup"><span data-stu-id="74fb2-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="74fb2-104">PowerShell a plusieurs alias qui permettent aux utilisateurs **UNIX** et **cmd.exe** d’utiliser des commandes familières.</span><span class="sxs-lookup"><span data-stu-id="74fb2-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="74fb2-105">Les commandes, ainsi que leurs applets de commande PowerShell et alias PowerShell associés, sont indiqués dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="74fb2-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|            <span data-ttu-id="74fb2-106">commande cmd.exe</span><span class="sxs-lookup"><span data-stu-id="74fb2-106">cmd.exe command</span></span>            | <span data-ttu-id="74fb2-107">Commande UNIX</span><span class="sxs-lookup"><span data-stu-id="74fb2-107">UNIX command</span></span> | <span data-ttu-id="74fb2-108">Applet de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="74fb2-108">PowerShell cmdlet</span></span> | <span data-ttu-id="74fb2-109">Alias PowerShell</span><span class="sxs-lookup"><span data-stu-id="74fb2-109">PowerShell alias</span></span> |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| <span data-ttu-id="74fb2-110">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="74fb2-110">**cd**, **chdir**</span></span>                     | <span data-ttu-id="74fb2-111">**cd**</span><span class="sxs-lookup"><span data-stu-id="74fb2-111">**cd**</span></span>       | `Set-Location`    | `sl`             |
| <span data-ttu-id="74fb2-112">**cls**</span><span class="sxs-lookup"><span data-stu-id="74fb2-112">**cls**</span></span>                               | <span data-ttu-id="74fb2-113">**clear**</span><span class="sxs-lookup"><span data-stu-id="74fb2-113">**clear**</span></span>    | `Clear-Host`      | `cls`            |
| <span data-ttu-id="74fb2-114">**copy**</span><span class="sxs-lookup"><span data-stu-id="74fb2-114">**copy**</span></span>                              | <span data-ttu-id="74fb2-115">**cp**</span><span class="sxs-lookup"><span data-stu-id="74fb2-115">**cp**</span></span>       | `Copy-Item`       | `cpi`            |
| <span data-ttu-id="74fb2-116">**del**, **erase**, **rd**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="74fb2-116">**del**, **erase**, **rd**, **rmdir**</span></span> | <span data-ttu-id="74fb2-117">**rm**</span><span class="sxs-lookup"><span data-stu-id="74fb2-117">**rm**</span></span>       | `Remove-Item`     | `ri`             |
| <span data-ttu-id="74fb2-118">**dir**</span><span class="sxs-lookup"><span data-stu-id="74fb2-118">**dir**</span></span>                               | <span data-ttu-id="74fb2-119">**ls**</span><span class="sxs-lookup"><span data-stu-id="74fb2-119">**ls**</span></span>       | `Get-ChildItem`   | `gci`            |
| <span data-ttu-id="74fb2-120">**echo**</span><span class="sxs-lookup"><span data-stu-id="74fb2-120">**echo**</span></span>                              | <span data-ttu-id="74fb2-121">**echo**</span><span class="sxs-lookup"><span data-stu-id="74fb2-121">**echo**</span></span>     | `Write-Output`    | `write`          |
| <span data-ttu-id="74fb2-122">**md**</span><span class="sxs-lookup"><span data-stu-id="74fb2-122">**md**</span></span>                                | <span data-ttu-id="74fb2-123">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="74fb2-123">**mkdir**</span></span>    | `New-Item`        | `ni`             |
| <span data-ttu-id="74fb2-124">**move**</span><span class="sxs-lookup"><span data-stu-id="74fb2-124">**move**</span></span>                              | <span data-ttu-id="74fb2-125">**mv**</span><span class="sxs-lookup"><span data-stu-id="74fb2-125">**mv**</span></span>       | `Move-Item`       | `mi`             |
| <span data-ttu-id="74fb2-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="74fb2-126">**popd**</span></span>                              | <span data-ttu-id="74fb2-127">**popd**</span><span class="sxs-lookup"><span data-stu-id="74fb2-127">**popd**</span></span>     | `Pop-Location`    | `popd`           |
| <span data-ttu-id="74fb2-128">**pushd**</span><span class="sxs-lookup"><span data-stu-id="74fb2-128">**pushd**</span></span>                             | <span data-ttu-id="74fb2-129">**pushd**</span><span class="sxs-lookup"><span data-stu-id="74fb2-129">**pushd**</span></span>    | `Push-Location`   | `pushd`          |
| <span data-ttu-id="74fb2-130">**ren**</span><span class="sxs-lookup"><span data-stu-id="74fb2-130">**ren**</span></span>                               | <span data-ttu-id="74fb2-131">**mv**</span><span class="sxs-lookup"><span data-stu-id="74fb2-131">**mv**</span></span>       | `Rename-Item`     | `rni`            |
| <span data-ttu-id="74fb2-132">**type**</span><span class="sxs-lookup"><span data-stu-id="74fb2-132">**type**</span></span>                              | <span data-ttu-id="74fb2-133">**cat**</span><span class="sxs-lookup"><span data-stu-id="74fb2-133">**cat**</span></span>      | `Get-Content`     | `gc`             |

<span data-ttu-id="74fb2-134">Pour trouver les alias PowerShell, utilisez l’applet de commande [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias).</span><span class="sxs-lookup"><span data-stu-id="74fb2-134">To find the PowerShell aliases, use the [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet.</span></span> <span data-ttu-id="74fb2-135">Pour afficher les alias d’une applet de commande, utilisez le paramètre **Definition** et spécifiez le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="74fb2-135">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="74fb2-136">Ou, pour trouver le nom d’applet de commande d’un alias, utilisez le paramètre **Name** et spécifiez l’alias.</span><span class="sxs-lookup"><span data-stu-id="74fb2-136">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
