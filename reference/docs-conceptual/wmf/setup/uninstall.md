---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Désinstaller WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147859"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="9dcbc-103">Instructions de désinstallation</span><span class="sxs-lookup"><span data-stu-id="9dcbc-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="9dcbc-104">Utilisation de l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="9dcbc-104">Using Command Prompt</span></span>

1. <span data-ttu-id="9dcbc-105">Ouvrez une **invite de commandes.**</span><span class="sxs-lookup"><span data-stu-id="9dcbc-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="9dcbc-106">Exécutez le [Lanceur autonome Windows Update](https://support.microsoft.com/en-us/kb/934307) comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="9dcbc-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="9dcbc-107">Sur Windows Server 2012 R2 et Windows 8.1 :</span><span class="sxs-lookup"><span data-stu-id="9dcbc-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="9dcbc-108">Sur Windows Server 2012 :</span><span class="sxs-lookup"><span data-stu-id="9dcbc-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="9dcbc-109">Sur Windows Server 2008 R2 SP1 et Windows 7 SP1 :</span><span class="sxs-lookup"><span data-stu-id="9dcbc-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="9dcbc-110">Utilisation du Panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="9dcbc-110">Using Control Panel</span></span>

1. <span data-ttu-id="9dcbc-111">Ouvrez le **Panneau de configuration.**</span><span class="sxs-lookup"><span data-stu-id="9dcbc-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="9dcbc-112">Ouvrez **Programmes**, puis **Désinstaller un programme.**</span><span class="sxs-lookup"><span data-stu-id="9dcbc-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="9dcbc-113">Cliquez sur **Afficher les mises à jour installées.**</span><span class="sxs-lookup"><span data-stu-id="9dcbc-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="9dcbc-114">Sélectionnez **Windows Management Framework 5.0** dans la liste des mises à jour installées.</span><span class="sxs-lookup"><span data-stu-id="9dcbc-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="9dcbc-115">Cela correspond à *KB3134758*, *KB3134759* ou *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="9dcbc-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="9dcbc-116">Cliquez sur **Désinstaller.**</span><span class="sxs-lookup"><span data-stu-id="9dcbc-116">Click **Uninstall.**</span></span>
