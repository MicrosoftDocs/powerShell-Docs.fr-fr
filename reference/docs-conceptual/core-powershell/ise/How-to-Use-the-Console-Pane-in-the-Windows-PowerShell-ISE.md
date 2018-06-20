---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Comment utiliser le volet Console dans Windows PowerShell ISE
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 5bbbdd3b1f0324ff1a4f2298459f58640c4dc9a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950785"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Comment utiliser le volet Console dans Windows PowerShell ISE

Le volet Console de l’environnement d’écriture de scripts intégré de Windows PowerShell fonctionne exactement comme la fenêtre de console Windows PowerShell ISE autonome.

Pour exécuter une commande dans le volet Console, tapez la commande, puis appuyez sur Entrée. Pour entrer plusieurs commandes à exécuter de façon séquentielle, tapez Maj+Entrée entre les commandes. Pour obtenir de l’aide sur la saisie des commandes, voir [Comment utiliser la saisie semi-automatique via la touche Tab dans le volet Script et le volet Console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).

Pour arrêter une commande, dans la barre d’outils, cliquez sur **Arrêter l’opération**, ou appuyez sur Ctrl+Pause. Vous pouvez également appuyer sur Ctrl+C pour arrêter une commande si le contexte est sans ambiguïté. Par exemple, si du texte a été sélectionné dans le volet actif, la combinaison de touches Ctrl+C correspond à l’opération de copie.

Depuis Windows PowerShell v3, le volet Sortie est combiné avec le volet Console. Cela présente l’avantage que le comportement est identique à celui de la console Windows PowerShell autonome, et élimine les différences de procédures en vigueur quand les volets étaient distincts. Vous pouvez :

- sélectionner et copier du texte du volet Console dans le Presse-papiers pour le coller dans toute autre fenêtre. Pour sélectionner du texte, cliquez et maintenez enfoncé le bouton de la souris dans le volet Sortie tout en faisant glisser le curseur sur le texte à capturer. Vous pouvez également utiliser les touches de direction tout en maintenant la touche **Maj** enfoncée pour sélectionner le texte. Appuyez sur Ctrl+C ou cliquez sur l’icône **Copie** dans la barre d’outils.

- Collez le texte sélectionné à l’emplacement du curseur. Cliquez sur l’icône **Coller** dans la barre d’outils.

- Effacer tout le texte dans le volet Console. Pour effacer le volet Console, vous pouvez cliquer sur l’icône **Effacer le volet Console** dans la barre d’outils, ou exécutez la commande **Clear-Host** ou son alias, **cls**.

## <a name="see-also"></a>Voir aussi

- [Présentation de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)