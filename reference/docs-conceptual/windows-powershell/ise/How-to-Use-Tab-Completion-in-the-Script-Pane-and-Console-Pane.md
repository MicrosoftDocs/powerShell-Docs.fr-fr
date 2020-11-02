---
ms.date: 01/02/2020
title: Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande
description: Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande
ms.openlocfilehash: d59a324ef5ca8eb882814c51bd9b7780b5916e81
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663681"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande

La saisie semi-automatique par le biais de la touche Tab fournit une aide automatique quand vous tapez dans le volet Script ou Commande. Pour tirer parti de cette fonctionnalité, procédez comme suit :

## <a name="to-automatically-complete-a-command-entry"></a>Pour compléter automatiquement une entrée de commande

Dans le volet Commande ou Script, tapez quelques caractères d’une commande, puis appuyez sur <kbd>TAB</kbd> pour sélectionner le texte de saisie semi-automatique souhaité. Si plusieurs éléments commencent par le texte que vous avez tapé initialement, continuez à appuyer sur <kbd>TAB</kbd> jusqu’à ce que l’élément souhaité s’affiche. La saisie semi-automatique via la touche Tab peut vous aider à saisir un nom d’applet de commande, un nom de paramètre, un nom de variable, un nom de propriété d’objet ou un chemin d’accès de fichier.

> [!NOTE]
> Dans le volet Script, appuyer sur <kbd>TAB</kbd> permet de terminer automatiquement une commande uniquement lorsque vous éditez des fichiers `.ps1`, `.psd1` ou `.psm1`. La saisie semi-automatique via la touche Tab fonctionne à tout moment lorsque vous tapez dans le volet Commande.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Pour compléter automatiquement une entrée de paramètre d’applet de commande

Dans le volet Commande ou Script, tapez une cmdlet suivie d’un tiret, puis appuyez sur <kbd>TAB</kbd>.

Par exemple, tapez `Get-Process -` puis appuyez sur <kbd>TAB</kbd> plusieurs fois pour afficher successivement chacun des paramètres de la cmdlet.

## <a name="see-also"></a>Voir aussi

- [Présentation de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Comment créer un onglet PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
