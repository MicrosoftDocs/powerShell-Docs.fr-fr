---
ms.date: 09/09/2019
keywords: powershell,applet de commande
title: 'Annexe 1 : Alias de compatibilité'
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "70848166"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="a6d9c-103">Annexe 1 - Alias de compatibilité</span><span class="sxs-lookup"><span data-stu-id="a6d9c-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="a6d9c-104">PowerShell a plusieurs alias qui permettent aux utilisateurs **UNIX** et **cmd.exe** d’utiliser des commandes familières.</span><span class="sxs-lookup"><span data-stu-id="a6d9c-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="a6d9c-105">Les commandes, ainsi que leurs applets de commande PowerShell et alias PowerShell associés, sont indiqués dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="a6d9c-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="a6d9c-106">commande cmd.exe</span><span class="sxs-lookup"><span data-stu-id="a6d9c-106">cmd.exe command</span></span>|<span data-ttu-id="a6d9c-107">Commande UNIX</span><span class="sxs-lookup"><span data-stu-id="a6d9c-107">UNIX command</span></span>|<span data-ttu-id="a6d9c-108">Applet de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6d9c-108">PowerShell cmdlet</span></span>|<span data-ttu-id="a6d9c-109">Alias PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6d9c-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="a6d9c-110">**cls**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-110">**cls**</span></span>|<span data-ttu-id="a6d9c-111">**clear**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-111">**clear**</span></span>|<span data-ttu-id="a6d9c-112">`Clear-Host` (fonction)</span><span class="sxs-lookup"><span data-stu-id="a6d9c-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="a6d9c-113">**copy**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-113">**copy**</span></span>|<span data-ttu-id="a6d9c-114">**cp**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="a6d9c-115">**dir**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-115">**dir**</span></span>|<span data-ttu-id="a6d9c-116">**ls**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="a6d9c-117">**type**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-117">**type**</span></span>|<span data-ttu-id="a6d9c-118">**cat**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="a6d9c-119">**move**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-119">**move**</span></span>|<span data-ttu-id="a6d9c-120">**mv**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="a6d9c-121">**md**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-121">**md**</span></span>|<span data-ttu-id="a6d9c-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="a6d9c-123">**pushd**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-123">**pushd**</span></span>|<span data-ttu-id="a6d9c-124">**pushd**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="a6d9c-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-125">**popd**</span></span>|<span data-ttu-id="a6d9c-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="a6d9c-127">**del**, **erase**, **rd**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="a6d9c-128">**rm**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="a6d9c-129">**ren**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-129">**ren**</span></span>|<span data-ttu-id="a6d9c-130">**mv**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="a6d9c-131">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-131">**cd**, **chdir**</span></span>|<span data-ttu-id="a6d9c-132">**cd**</span><span class="sxs-lookup"><span data-stu-id="a6d9c-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="a6d9c-133">Pour trouver les alias PowerShell, utilisez l’applet de commande [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias).</span><span class="sxs-lookup"><span data-stu-id="a6d9c-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="a6d9c-134">Pour afficher les alias d’une applet de commande, utilisez le paramètre **Definition** et spécifiez le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a6d9c-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="a6d9c-135">Ou, pour trouver le nom d’applet de commande d’un alias, utilisez le paramètre **Name** et spécifiez l’alias.</span><span class="sxs-lookup"><span data-stu-id="a6d9c-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
