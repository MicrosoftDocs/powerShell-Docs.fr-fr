---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057512"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="c5d17-102">Instructions de désinstallation</span><span class="sxs-lookup"><span data-stu-id="c5d17-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="c5d17-103">Utilisation de l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="c5d17-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="c5d17-104">Ouvrez une **invite de commandes.**</span><span class="sxs-lookup"><span data-stu-id="c5d17-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="c5d17-105">Exécutez le [Lanceur autonome Windows Update](https://support.microsoft.com/en-us/kb/934307) comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="c5d17-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="c5d17-106">Sur Windows Server 2012 R2 et Windows 8.1 :</span><span class="sxs-lookup"><span data-stu-id="c5d17-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="c5d17-107">Sur Windows Server 2012 :</span><span class="sxs-lookup"><span data-stu-id="c5d17-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="c5d17-108">Sur Windows Server 2008 R2 SP1 et Windows 7 SP1 :</span><span class="sxs-lookup"><span data-stu-id="c5d17-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="c5d17-109">Utilisation du Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="c5d17-109">Using Control Panel</span></span>
1.  <span data-ttu-id="c5d17-110">Ouvrez le **Panneau de configuration.**</span><span class="sxs-lookup"><span data-stu-id="c5d17-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="c5d17-111">Ouvrez **Programmes**, puis **Désinstaller un programme.**</span><span class="sxs-lookup"><span data-stu-id="c5d17-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="c5d17-112">Cliquez sur **Afficher les mises à jour installées.**</span><span class="sxs-lookup"><span data-stu-id="c5d17-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="c5d17-113">Sélectionnez **Windows Management Framework 5.0** dans la liste des mises à jour installées.</span><span class="sxs-lookup"><span data-stu-id="c5d17-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="c5d17-114">Cela correspond à *KB3134758*, *KB3134759* ou *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="c5d17-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="c5d17-115">Cliquez sur **Désinstaller.**</span><span class="sxs-lookup"><span data-stu-id="c5d17-115">Click **Uninstall.**</span></span>
