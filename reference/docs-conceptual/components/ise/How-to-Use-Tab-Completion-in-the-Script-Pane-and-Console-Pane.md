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
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande

La saisie semi-automatique par le biais de la touche Tab fournit une aide automatique quand vous tapez dans le volet Script ou Commande. Pour tirer parti de cette fonctionnalité, procédez comme suit :

## <a name="to-automatically-complete-a-command-entry"></a>Pour compléter automatiquement une entrée de commande

Dans le volet Commande ou Script, tapez quelques caractères d’une commande, puis appuyez sur la touche TAB pour sélectionner le texte de saisie semi-automatique souhaité. Si plusieurs éléments commencent par le texte que vous avez tapé initialement, continuez à appuyer sur la touche Tab jusqu’à ce que l’élément souhaité s’affiche. La saisie semi-automatique via la touche Tab peut vous aider à saisir un nom d’applet de commande, un nom de paramètre, un nom de variable, un nom de propriété d’objet ou un chemin d’accès de fichier.

> [!NOTE]
> Dans le volet Script, l’appui sur la touche TAB complète automatiquement une commande uniquement lorsque vous éditez des fichiers .psm1, .psd1 ou .ps1. La saisie semi-automatique via la touche Tab fonctionne à tout moment lorsque vous tapez dans le volet Commande.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Pour compléter automatiquement une entrée de paramètre d’applet de commande

Dans le volet Commande ou Script, tapez une applet de commande suivie d’un tiret, puis appuyez sur la touche de tabulation.

Par exemple, tapez `Get-Process -` puis appuyez sur la touche TAB plusieurs fois pour afficher successivement chacun des paramètres de l’applet de commande.

## <a name="see-also"></a>Voir aussi

- [Présentation de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Comment créer un onglet PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
