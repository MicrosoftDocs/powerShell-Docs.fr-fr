---
ms.date: 01/02/2020
keywords: powershell,applet de commande
title: Comment utiliser le volet Console dans Windows PowerShell ISE
ms.openlocfilehash: f0ef07e410ed494f5732eab360c4e050c9c09a7f
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736145"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Comment utiliser le volet Console dans Windows PowerShell ISE

Le volet Console de l’environnement d’écriture de scripts intégré de Windows PowerShell fonctionne exactement comme la fenêtre de console Windows PowerShell ISE autonome.

Pour exécuter une commande dans le volet Console, tapez la commande, puis appuyez sur <kbd>ENTRÉE</kbd>. Pour entrer plusieurs commandes à exécuter de façon séquentielle, tapez <kbd>MAJ</kbd>+<kbd>ENTRÉE</kbd> entre les commandes. Pour obtenir de l’aide sur la saisie des commandes, voir [Comment utiliser la saisie semi-automatique via la touche Tab dans le volet Script et le volet Console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).

Pour arrêter une commande, dans la barre d’outils, cliquez sur **Arrêter l’opération** ou appuyez sur <kbd>CTRL</kbd>+<kbd>ARRÊTER</kbd>. Vous pouvez également appuyer sur <kbd>CTRL</kbd>+<kbd>C</kbd> pour arrêter une commande si le contexte est sans ambiguïté. Par exemple, si du texte a été sélectionné dans le volet actif, <kbd>CTRL</kbd>+<kbd>C</kbd> mappe à l’opération de copie.

Depuis Windows PowerShell v3, le volet Sortie est combiné avec le volet Console. Cela présente l’avantage que le comportement est identique à celui de la console Windows PowerShell autonome, et élimine les différences de procédures en vigueur quand les volets étaient distincts. Vous pouvez :

- sélectionner et copier du texte du volet Console dans le Presse-papiers pour le coller dans toute autre fenêtre. Pour sélectionner du texte, cliquez et maintenez enfoncé le bouton de la souris dans le volet Sortie tout en faisant glisser le curseur sur le texte à capturer. Vous pouvez également utiliser les touches de direction tout en maintenant la touche <kbd>Maj</kbd> enfoncée pour sélectionner le texte. Appuyez sur <kbd>CTRL</kbd>+<kbd>C</kbd> ou cliquez sur l’icône **Copie** dans la barre d’outils.

- Collez le texte sélectionné à l’emplacement du curseur. Cliquez sur l’icône **Coller** dans la barre d’outils.

- Effacer tout le texte dans le volet Console. Pour effacer le volet Console, vous pouvez cliquer sur l’icône **Effacer le volet Console** dans la barre d’outils ou exécuter la commande `Clear-Host` ou son alias, `cls`.

## <a name="see-also"></a>Voir aussi

- [Présentation de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
