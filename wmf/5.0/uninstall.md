---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="f1aa8-102">Instructions de désinstallation</span><span class="sxs-lookup"><span data-stu-id="f1aa8-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="f1aa8-103">Utilisation de l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="f1aa8-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="f1aa8-104">Ouvrez une **invite de commandes.**</span><span class="sxs-lookup"><span data-stu-id="f1aa8-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="f1aa8-105">Exécutez le [Lanceur autonome Windows Update](https://support.microsoft.com/en-us/kb/934307) comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="f1aa8-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="f1aa8-106">Sur Windows Server 2012 R2 et Windows 8.1 :</span><span class="sxs-lookup"><span data-stu-id="f1aa8-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="f1aa8-107">Sur Windows Server 2012 :</span><span class="sxs-lookup"><span data-stu-id="f1aa8-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="f1aa8-108">Sur Windows Server 2008 R2 SP1 et Windows 7 SP1 :</span><span class="sxs-lookup"><span data-stu-id="f1aa8-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="f1aa8-109">Utilisation du Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="f1aa8-109">Using Control Panel</span></span>
1.  <span data-ttu-id="f1aa8-110">Ouvrez le **Panneau de configuration.**</span><span class="sxs-lookup"><span data-stu-id="f1aa8-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="f1aa8-111">Ouvrez **Programmes**, puis **Désinstaller un programme.**</span><span class="sxs-lookup"><span data-stu-id="f1aa8-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="f1aa8-112">Cliquez sur **Afficher les mises à jour installées.**</span><span class="sxs-lookup"><span data-stu-id="f1aa8-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="f1aa8-113">Sélectionnez **Windows Management Framework 5.0** dans la liste des mises à jour installées.</span><span class="sxs-lookup"><span data-stu-id="f1aa8-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="f1aa8-114">Cela correspond à *KB3134758*, *KB3134759* ou *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="f1aa8-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="f1aa8-115">Cliquez sur **Désinstaller.**</span><span class="sxs-lookup"><span data-stu-id="f1aa8-115">Click **Uninstall.**</span></span>
