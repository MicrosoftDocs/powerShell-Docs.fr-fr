---
ms.date: 08/03/2020
keywords: powershell,applet de commande
title: 'Annexe 1 : Alias de compatibilité'
description: PowerShell a plusieurs alias qui permettent aux utilisateurs UNIX et cmd.exe d’utiliser des commandes familières.
ms.openlocfilehash: 8cbbd5a358de9018fcb5c840e711cd76f7a9a353
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500740"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="da198-104">Annexe 1 - Alias de compatibilité</span><span class="sxs-lookup"><span data-stu-id="da198-104">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="da198-105">PowerShell a plusieurs alias qui permettent aux utilisateurs **UNIX** et **cmd.exe** d’utiliser des commandes familières.</span><span class="sxs-lookup"><span data-stu-id="da198-105">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="da198-106">Les commandes, ainsi que leurs applets de commande PowerShell et alias PowerShell associés, sont indiqués dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="da198-106">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|            <span data-ttu-id="da198-107">commande cmd.exe</span><span class="sxs-lookup"><span data-stu-id="da198-107">cmd.exe command</span></span>            | <span data-ttu-id="da198-108">Commande UNIX</span><span class="sxs-lookup"><span data-stu-id="da198-108">UNIX command</span></span> | <span data-ttu-id="da198-109">Applet de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="da198-109">PowerShell cmdlet</span></span> | <span data-ttu-id="da198-110">Alias PowerShell</span><span class="sxs-lookup"><span data-stu-id="da198-110">PowerShell alias</span></span> |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| <span data-ttu-id="da198-111">**cd** , **chdir**</span><span class="sxs-lookup"><span data-stu-id="da198-111">**cd** , **chdir**</span></span>                     | <span data-ttu-id="da198-112">**cd**</span><span class="sxs-lookup"><span data-stu-id="da198-112">**cd**</span></span>       | `Set-Location`    | `sl`             |
| <span data-ttu-id="da198-113">**cls**</span><span class="sxs-lookup"><span data-stu-id="da198-113">**cls**</span></span>                               | <span data-ttu-id="da198-114">**clear**</span><span class="sxs-lookup"><span data-stu-id="da198-114">**clear**</span></span>    | `Clear-Host`      | `cls`            |
| <span data-ttu-id="da198-115">**copy**</span><span class="sxs-lookup"><span data-stu-id="da198-115">**copy**</span></span>                              | <span data-ttu-id="da198-116">**cp**</span><span class="sxs-lookup"><span data-stu-id="da198-116">**cp**</span></span>       | `Copy-Item`       | `cpi`            |
| <span data-ttu-id="da198-117">**del** , **erase** , **rd** , **rmdir**</span><span class="sxs-lookup"><span data-stu-id="da198-117">**del** , **erase** , **rd** , **rmdir**</span></span> | <span data-ttu-id="da198-118">**rm**</span><span class="sxs-lookup"><span data-stu-id="da198-118">**rm**</span></span>       | `Remove-Item`     | `ri`             |
| <span data-ttu-id="da198-119">**dir**</span><span class="sxs-lookup"><span data-stu-id="da198-119">**dir**</span></span>                               | <span data-ttu-id="da198-120">**ls**</span><span class="sxs-lookup"><span data-stu-id="da198-120">**ls**</span></span>       | `Get-ChildItem`   | `gci`            |
| <span data-ttu-id="da198-121">**echo**</span><span class="sxs-lookup"><span data-stu-id="da198-121">**echo**</span></span>                              | <span data-ttu-id="da198-122">**echo**</span><span class="sxs-lookup"><span data-stu-id="da198-122">**echo**</span></span>     | `Write-Output`    | `write`          |
| <span data-ttu-id="da198-123">**md**</span><span class="sxs-lookup"><span data-stu-id="da198-123">**md**</span></span>                                | <span data-ttu-id="da198-124">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="da198-124">**mkdir**</span></span>    | `New-Item`        | `ni`             |
| <span data-ttu-id="da198-125">**move**</span><span class="sxs-lookup"><span data-stu-id="da198-125">**move**</span></span>                              | <span data-ttu-id="da198-126">**mv**</span><span class="sxs-lookup"><span data-stu-id="da198-126">**mv**</span></span>       | `Move-Item`       | `mi`             |
| <span data-ttu-id="da198-127">**popd**</span><span class="sxs-lookup"><span data-stu-id="da198-127">**popd**</span></span>                              | <span data-ttu-id="da198-128">**popd**</span><span class="sxs-lookup"><span data-stu-id="da198-128">**popd**</span></span>     | `Pop-Location`    | `popd`           |
| <span data-ttu-id="da198-129">**pushd**</span><span class="sxs-lookup"><span data-stu-id="da198-129">**pushd**</span></span>                             | <span data-ttu-id="da198-130">**pushd**</span><span class="sxs-lookup"><span data-stu-id="da198-130">**pushd**</span></span>    | `Push-Location`   | `pushd`          |
| <span data-ttu-id="da198-131">**ren**</span><span class="sxs-lookup"><span data-stu-id="da198-131">**ren**</span></span>                               | <span data-ttu-id="da198-132">**mv**</span><span class="sxs-lookup"><span data-stu-id="da198-132">**mv**</span></span>       | `Rename-Item`     | `rni`            |
| <span data-ttu-id="da198-133">**type**</span><span class="sxs-lookup"><span data-stu-id="da198-133">**type**</span></span>                              | <span data-ttu-id="da198-134">**cat**</span><span class="sxs-lookup"><span data-stu-id="da198-134">**cat**</span></span>      | `Get-Content`     | `gc`             |

<span data-ttu-id="da198-135">Pour trouver les alias PowerShell, utilisez l’applet de commande [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias).</span><span class="sxs-lookup"><span data-stu-id="da198-135">To find the PowerShell aliases, use the [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet.</span></span> <span data-ttu-id="da198-136">Pour afficher les alias d’une applet de commande, utilisez le paramètre **Definition** et spécifiez le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="da198-136">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="da198-137">Ou, pour trouver le nom d’applet de commande d’un alias, utilisez le paramètre **Name** et spécifiez l’alias.</span><span class="sxs-lookup"><span data-stu-id="da198-137">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
