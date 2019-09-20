---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Améliorations de la console dans WMF 5.1
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147629"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="2711e-103">Améliorations de la console dans WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2711e-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="2711e-104">Améliorations de la console PowerShell</span><span class="sxs-lookup"><span data-stu-id="2711e-104">PowerShell console improvements</span></span>

<span data-ttu-id="2711e-105">Les modifications suivantes ont été apportées à powershell.exe dans WMF 5.1 pour améliorer l’expérience de la console :</span><span class="sxs-lookup"><span data-stu-id="2711e-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="2711e-106">Prise en charge de VT100</span><span class="sxs-lookup"><span data-stu-id="2711e-106">VT100 support</span></span>

<span data-ttu-id="2711e-107">Ajout dans Windows 10 de la prise en charge des [séquences d’échappement VT100](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="2711e-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="2711e-108">PowerShell ignore certaines séquences d’échappement de mise en forme VT100 lors du calcul des largeurs de tableaux.</span><span class="sxs-lookup"><span data-stu-id="2711e-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="2711e-109">Ajout dans PowerShell d’une nouvelle API que vous pouvez utiliser dans le code de mise en forme pour déterminer si VT100 est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2711e-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="2711e-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2711e-110">For example:</span></span>

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

<span data-ttu-id="2711e-111">Voici un [exemple](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) complet que vous pouvez utiliser pour mettre en surbrillance des correspondances à partir de `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="2711e-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span> <span data-ttu-id="2711e-112">Enregistrez l’exemple dans un fichier nommé `MatchInfo.format.ps1xml` puis, pour l’utiliser, dans votre profil ou ailleurs, exécutez `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="2711e-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="2711e-113">Notez que les séquences d’échappement VT100 ne sont prises en charge qu’à compter de la Mise à jour anniversaire Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2711e-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update.</span></span>
<span data-ttu-id="2711e-114">Elles ne sont pas prises en charge sur les systèmes antérieurs.</span><span class="sxs-lookup"><span data-stu-id="2711e-114">They are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="2711e-115">Prise en charge du mode vi dans PSReadline</span><span class="sxs-lookup"><span data-stu-id="2711e-115">Vi mode support in PSReadline</span></span>

<span data-ttu-id="2711e-116">Ajout de la prise en charge du mode vi dans [PSReadline](https://github.com/PowerShell/PSReadLine).</span><span class="sxs-lookup"><span data-stu-id="2711e-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="2711e-117">Pour utiliser le mode vi, exécutez `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="2711e-117">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="2711e-118">Stdin redirigé avec entrée interactive</span><span class="sxs-lookup"><span data-stu-id="2711e-118">Redirected stdin with interactive input</span></span>

<span data-ttu-id="2711e-119">Dans les versions antérieures, vous deviez démarrer PowerShell avec `powershell -File -` quand stdin était redirigé et que vous souhaitiez entrer des commandes de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="2711e-119">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="2711e-120">Avec WMF 5.1, cette option difficile à découvrir n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2711e-120">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="2711e-121">Il est possible de lancer PowerShell sans aucune option.</span><span class="sxs-lookup"><span data-stu-id="2711e-121">You can start PowerShell without any options.</span></span>

<span data-ttu-id="2711e-122">Notez que PSReadline ne prend pas en charge le flux STDIN redirigé et que l’expérience de modification de ligne de commande intégrée avec flux STDIN redirigé est très limitée (par exemple, les touches de direction ne fonctionnent pas).</span><span class="sxs-lookup"><span data-stu-id="2711e-122">Note that PSReadline does not support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="2711e-123">Une version ultérieure de PSReadline doit résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="2711e-123">A future release of PSReadline should address this issue.</span></span>