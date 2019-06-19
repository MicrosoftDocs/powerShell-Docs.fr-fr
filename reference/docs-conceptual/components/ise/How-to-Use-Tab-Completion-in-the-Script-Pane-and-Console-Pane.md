---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande
ms.openlocfilehash: 9fcb85668673adb1de596660d37e56f6607a4064
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030998"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="af068-103">Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande</span><span class="sxs-lookup"><span data-stu-id="af068-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="af068-104">La saisie semi-automatique par le biais de la touche Tab fournit une aide automatique quand vous tapez dans le volet Script ou Commande.</span><span class="sxs-lookup"><span data-stu-id="af068-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="af068-105">Pour tirer parti de cette fonctionnalité, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="af068-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="af068-106">Pour compléter automatiquement une entrée de commande</span><span class="sxs-lookup"><span data-stu-id="af068-106">To automatically complete a command entry</span></span>

<span data-ttu-id="af068-107">Dans le volet Commande ou Script, tapez quelques caractères d’une commande, puis appuyez sur la touche TAB pour sélectionner le texte de saisie semi-automatique souhaité.</span><span class="sxs-lookup"><span data-stu-id="af068-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="af068-108">Si plusieurs éléments commencent par le texte que vous avez tapé initialement, continuez à appuyer sur la touche Tab jusqu’à ce que l’élément souhaité s’affiche.</span><span class="sxs-lookup"><span data-stu-id="af068-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="af068-109">La saisie semi-automatique via la touche Tab peut vous aider à saisir un nom d’applet de commande, un nom de paramètre, un nom de variable, un nom de propriété d’objet ou un chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="af068-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="af068-110">Dans le volet Script, l’appui sur la touche TAB complète automatiquement une commande uniquement lorsque vous éditez des fichiers .psm1, .psd1 ou .ps1.</span><span class="sxs-lookup"><span data-stu-id="af068-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="af068-111">La saisie semi-automatique via la touche Tab fonctionne à tout moment lorsque vous tapez dans le volet Commande.</span><span class="sxs-lookup"><span data-stu-id="af068-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="af068-112">Pour compléter automatiquement une entrée de paramètre d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="af068-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="af068-113">Dans le volet Commande ou Script, tapez une applet de commande suivie d’un tiret, puis appuyez sur la touche de tabulation.</span><span class="sxs-lookup"><span data-stu-id="af068-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press TAB.</span></span>

<span data-ttu-id="af068-114">Par exemple, tapez `Get-Process -` puis appuyez sur la touche TAB plusieurs fois pour afficher successivement chacun des paramètres de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="af068-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="af068-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af068-115">See Also</span></span>

- [<span data-ttu-id="af068-116">Présentation de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="af068-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="af068-117">Comment créer un onglet PowerShell</span><span class="sxs-lookup"><span data-stu-id="af068-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
