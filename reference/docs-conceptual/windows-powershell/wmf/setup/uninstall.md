---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Désinstaller WMF 5.0
ms.openlocfilehash: fa76bacb4b62025d0d2350b9a0e072068ca83ab1
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236303"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="2bc9a-103">Instructions de désinstallation</span><span class="sxs-lookup"><span data-stu-id="2bc9a-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="2bc9a-104">Utilisation de l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="2bc9a-104">Using Command Prompt</span></span>

1. <span data-ttu-id="2bc9a-105">Ouvrez une **invite de commandes.**</span><span class="sxs-lookup"><span data-stu-id="2bc9a-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="2bc9a-106">Exécutez le [Lanceur autonome Windows Update](https://support.microsoft.com/kb/934307) comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="2bc9a-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/kb/934307) as shown below:</span></span>

<span data-ttu-id="2bc9a-107">Sur Windows Server 2012 R2 et Windows 8.1 :</span><span class="sxs-lookup"><span data-stu-id="2bc9a-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="2bc9a-108">Sur Windows Server 2012 :</span><span class="sxs-lookup"><span data-stu-id="2bc9a-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="2bc9a-109">Sur Windows Server 2008 R2 SP1 et Windows 7 SP1 :</span><span class="sxs-lookup"><span data-stu-id="2bc9a-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="2bc9a-110">Utilisation du Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="2bc9a-110">Using Control Panel</span></span>

1. <span data-ttu-id="2bc9a-111">Ouvrez le **Panneau de configuration.**</span><span class="sxs-lookup"><span data-stu-id="2bc9a-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="2bc9a-112">Ouvrez **Programmes**, puis **Désinstaller un programme.**</span><span class="sxs-lookup"><span data-stu-id="2bc9a-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="2bc9a-113">Cliquez sur **Afficher les mises à jour installées.**</span><span class="sxs-lookup"><span data-stu-id="2bc9a-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="2bc9a-114">Sélectionnez **Windows Management Framework 5.0** dans la liste des mises à jour installées.</span><span class="sxs-lookup"><span data-stu-id="2bc9a-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="2bc9a-115">Cela correspond à *KB3134758*, *KB3134759* ou *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="2bc9a-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="2bc9a-116">Cliquez sur **Désinstaller.**</span><span class="sxs-lookup"><span data-stu-id="2bc9a-116">Click **Uninstall.**</span></span>
