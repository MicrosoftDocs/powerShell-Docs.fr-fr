---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Améliorations de la console dans WMF 5.1
ms.openlocfilehash: a8e82e2f973916c2ed5007eba90ee6f2b7a9a769
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085124"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="0c553-103">Améliorations de la console dans WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="0c553-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="0c553-104">Améliorations de la console PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c553-104">PowerShell console improvements</span></span>

<span data-ttu-id="0c553-105">Les modifications suivantes ont été apportées à powershell.exe dans WMF 5.1 pour améliorer l’expérience de la console :</span><span class="sxs-lookup"><span data-stu-id="0c553-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="0c553-106">Prise en charge de VT100</span><span class="sxs-lookup"><span data-stu-id="0c553-106">VT100 support</span></span>

<span data-ttu-id="0c553-107">Ajout dans Windows 10 de la prise en charge des [séquences d’échappement VT100](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="0c553-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="0c553-108">PowerShell ignore certaines séquences d’échappement de mise en forme VT100 lors du calcul des largeurs de tableaux.</span><span class="sxs-lookup"><span data-stu-id="0c553-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="0c553-109">Ajout dans PowerShell d’une nouvelle API que vous pouvez utiliser dans le code de mise en forme pour déterminer si VT100 est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0c553-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="0c553-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0c553-110">For example:</span></span>

```powershell
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```

<span data-ttu-id="0c553-111">Voici un [exemple](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) complet que vous pouvez utiliser pour mettre en surbrillance des correspondances à partir de `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="0c553-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span>
<span data-ttu-id="0c553-112">Enregistrez l’exemple dans un fichier nommé `MatchInfo.format.ps1xml` puis, pour l’utiliser, dans votre profil ou ailleurs, exécutez `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="0c553-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="0c553-113">Notez que les séquences d’échappement VT100 sont prises en charge uniquement à compter de la Mise à jour anniversaire Windows 10. Elles ne sont pas prises en charge sur les systèmes antérieurs.</span><span class="sxs-lookup"><span data-stu-id="0c553-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="0c553-114">Prise en charge du mode vi dans PSReadline</span><span class="sxs-lookup"><span data-stu-id="0c553-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="0c553-115">Ajout de la prise en charge du mode vi dans [PSReadline](https://github.com/lzybkr/PSReadLine).</span><span class="sxs-lookup"><span data-stu-id="0c553-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="0c553-116">Pour utiliser le mode vi, exécutez `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="0c553-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="0c553-117">Stdin redirigé avec entrée interactive</span><span class="sxs-lookup"><span data-stu-id="0c553-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="0c553-118">Dans les versions antérieures, vous deviez démarrer PowerShell avec `powershell -File -` quand stdin était redirigé et que vous souhaitiez entrer des commandes de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="0c553-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="0c553-119">Avec WMF 5.1, cette option difficile à découvrir n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0c553-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="0c553-120">Vous pouvez démarrer PowerShell sans option, par exemple `powershell`.</span><span class="sxs-lookup"><span data-stu-id="0c553-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="0c553-121">Notez que PSReadline ne prend pas en charge stdin redirigé et que l’expérience de modification de ligne de commande intégrée avec stdin redirigé est très limitée (par exemple, les touches de direction ne fonctionnent pas).</span><span class="sxs-lookup"><span data-stu-id="0c553-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="0c553-122">Une version ultérieure de PSReadline doit résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="0c553-122">A future release of PSReadline should address this issue.</span></span>