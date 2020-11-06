---
ms.date: 06/12/2017
title: Désinstaller WMF 5.0
description: Cet article explique comment désinstaller WMF des versions antérieures de Windows.
ms.openlocfilehash: d8078ea918db2c1cf9a7ddd6ea8d1413b593c0ff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660811"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="100b8-103">Instructions de désinstallation</span><span class="sxs-lookup"><span data-stu-id="100b8-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="100b8-104">Utilisation de l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="100b8-104">Using Command Prompt</span></span>

1. <span data-ttu-id="100b8-105">Ouvrez une **invite de commandes.**</span><span class="sxs-lookup"><span data-stu-id="100b8-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="100b8-106">Exécutez le [Lanceur autonome Windows Update](https://support.microsoft.com/kb/934307) comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="100b8-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/kb/934307) as shown below:</span></span>

<span data-ttu-id="100b8-107">Sur Windows Server 2012 R2 et Windows 8.1 :</span><span class="sxs-lookup"><span data-stu-id="100b8-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="100b8-108">Sur Windows Server 2012 :</span><span class="sxs-lookup"><span data-stu-id="100b8-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="100b8-109">Sur Windows Server 2008 R2 SP1 et Windows 7 SP1 :</span><span class="sxs-lookup"><span data-stu-id="100b8-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="100b8-110">Utilisation du Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="100b8-110">Using Control Panel</span></span>

1. <span data-ttu-id="100b8-111">Ouvrez le **Panneau de configuration.**</span><span class="sxs-lookup"><span data-stu-id="100b8-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="100b8-112">Ouvrez **Programmes** , puis **Désinstaller un programme.**</span><span class="sxs-lookup"><span data-stu-id="100b8-112">Open **Programs** , then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="100b8-113">Cliquez sur **Afficher les mises à jour installées.**</span><span class="sxs-lookup"><span data-stu-id="100b8-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="100b8-114">Sélectionnez **Windows Management Framework 5.0** dans la liste des mises à jour installées.</span><span class="sxs-lookup"><span data-stu-id="100b8-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="100b8-115">Cela correspond à *KB3134758* , *KB3134759* ou *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="100b8-115">This corresponds to *KB3134758* , *KB3134759* , or *KB3134760*.</span></span> <span data-ttu-id="100b8-116">Cliquez sur **Désinstaller.**</span><span class="sxs-lookup"><span data-stu-id="100b8-116">Click **Uninstall.**</span></span>
