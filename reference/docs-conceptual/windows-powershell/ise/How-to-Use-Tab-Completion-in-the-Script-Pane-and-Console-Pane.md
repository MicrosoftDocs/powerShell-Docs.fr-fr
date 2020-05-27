---
ms.date: 01/02/2020
keywords: powershell,applet de commande
title: Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande
ms.openlocfilehash: 07cf9ff75db8d33ed018542153bfcd7503035e40
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808825"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="91258-103">Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande</span><span class="sxs-lookup"><span data-stu-id="91258-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="91258-104">La saisie semi-automatique par le biais de la touche Tab fournit une aide automatique quand vous tapez dans le volet Script ou Commande.</span><span class="sxs-lookup"><span data-stu-id="91258-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="91258-105">Pour tirer parti de cette fonctionnalité, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="91258-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="91258-106">Pour compléter automatiquement une entrée de commande</span><span class="sxs-lookup"><span data-stu-id="91258-106">To automatically complete a command entry</span></span>

<span data-ttu-id="91258-107">Dans le volet Commande ou Script, tapez quelques caractères d’une commande, puis appuyez sur <kbd>TAB</kbd> pour sélectionner le texte de saisie semi-automatique souhaité.</span><span class="sxs-lookup"><span data-stu-id="91258-107">In the Command Pane or Script Pane, type a few characters of a command and then press <kbd>TAB</kbd> to select the desired completion text.</span></span> <span data-ttu-id="91258-108">Si plusieurs éléments commencent par le texte que vous avez tapé initialement, continuez à appuyer sur <kbd>TAB</kbd> jusqu’à ce que l’élément souhaité s’affiche.</span><span class="sxs-lookup"><span data-stu-id="91258-108">If multiple items begin with the text that you initially typed, then continue pressing <kbd>TAB</kbd> until the item you want appears.</span></span> <span data-ttu-id="91258-109">La saisie semi-automatique via la touche Tab peut vous aider à saisir un nom d’applet de commande, un nom de paramètre, un nom de variable, un nom de propriété d’objet ou un chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="91258-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="91258-110">Dans le volet Script, appuyer sur <kbd>TAB</kbd> permet de terminer automatiquement une commande uniquement lorsque vous éditez des fichiers `.ps1`, `.psd1` ou `.psm1`.</span><span class="sxs-lookup"><span data-stu-id="91258-110">In the Script Pane, pressing <kbd>TAB</kbd> will automatically complete a command only when you are editing `.ps1`, `.psd1`, or `.psm1` files.</span></span> <span data-ttu-id="91258-111">La saisie semi-automatique via la touche Tab fonctionne à tout moment lorsque vous tapez dans le volet Commande.</span><span class="sxs-lookup"><span data-stu-id="91258-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="91258-112">Pour compléter automatiquement une entrée de paramètre d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="91258-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="91258-113">Dans le volet Commande ou Script, tapez une cmdlet suivie d’un tiret, puis appuyez sur <kbd>TAB</kbd>.</span><span class="sxs-lookup"><span data-stu-id="91258-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press <kbd>TAB</kbd>.</span></span>

<span data-ttu-id="91258-114">Par exemple, tapez `Get-Process -` puis appuyez sur <kbd>TAB</kbd> plusieurs fois pour afficher successivement chacun des paramètres de la cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91258-114">For example, type `Get-Process -` and then press <kbd>TAB</kbd> multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="91258-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91258-115">See Also</span></span>

- [<span data-ttu-id="91258-116">Présentation de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="91258-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="91258-117">Comment créer un onglet PowerShell</span><span class="sxs-lookup"><span data-stu-id="91258-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
