---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: ba8d0af7e7fc0f1df9f65116be899097b0a97a3c
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Comment utiliser la saisie semi-automatique via la touche Tab dans les volets Script et Commande
La saisie semi-automatique par le biais de la touche Tab fournit une aide automatique quand vous tapez dans le volet Script ou Commande. Pour tirer parti de cette fonctionnalité, procédez comme suit :

## <a name="to-automatically-complete-a-command-entry"></a>Pour compléter automatiquement une entrée de commande
Dans le volet Commande ou Script, tapez quelques caractères d’une commande, puis appuyez sur la touche TAB pour sélectionner le texte de saisie semi-automatique souhaité. Si plusieurs éléments commencent par le texte que vous avez tapé initialement, continuez à appuyer sur la touche Tab jusqu’à ce que l’élément souhaité s’affiche. La saisie semi-automatique via la touche Tab peut vous aider à saisir un nom d’applet de commande, un nom de paramètre, un nom de variable, un nom de propriété d’objet ou un chemin d’accès de fichier.

> [!NOTE]
> Dans le volet Script, l’appui sur la touche TAB complète automatiquement une commande uniquement lorsque vous éditez des fichiers .psm1, .psd1 ou .ps1. La saisie semi-automatique via la touche Tab fonctionne à tout moment lorsque vous tapez dans le volet Commande.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Pour compléter automatiquement une entrée de paramètre d’applet de commande
Dans le volet Commande ou Script, tapez une applet de commande suivie d’un tiret (ou trait-d’union), puis appuyez sur la touche TAB.

Par exemple, tapez `Get-Process -` puis appuyez sur la touche TAB plusieurs fois pour afficher successivement chacun des paramètres de l’applet de commande.

## <a name="see-also"></a>Voir aussi
- [Utilisation de Windows PowerShell ISE](using-the-windows-powershell-ise.md)
- [Comment créer un onglet PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

