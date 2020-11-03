---
description: Décrit comment modifier des commandes à l’invite de commandes PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_line_editing?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Line_Editing
ms.openlocfilehash: d4b525e4c3f461b799c3bef157e04e0763a0b9c6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207389"
---
# <a name="about-line-editing"></a>À propos de la modification de ligne

## <a name="short-description"></a>Description courte

Décrit comment modifier des commandes à l’invite de commandes PowerShell.

## <a name="long-description"></a>Description longue

La console PowerShell contient des raccourcis clavier utiles pour vous aider à modifier les commandes à l’invite de commandes PowerShell.

### <a name="add-a-line"></a>Ajouter une ligne

Pour ajouter une ligne, appuyez sur <kbd>MAJ</kbd> + <kbd>entrée</kbd>.

Vous pouvez ajouter plusieurs lignes. Chaque ligne supplémentaire commence par `>>` , l’invite de continuation. Appuyez sur <kbd>entrée</kbd> pour exécuter la commande.

### <a name="move-left-and-right"></a>Déplacer vers la gauche et vers la droite

Pour déplacer le curseur d’un caractère vers la gauche, appuyez sur la <kbd>flèche gauche</kbd>.

Pour déplacer le curseur d’un mot vers la gauche, appuyez sur <kbd>CTRL</kbd> + <kbd>gauche</kbd>.

Pour déplacer le curseur d’un caractère vers la droite, appuyez sur la <kbd>flèche droite</kbd>.

Pour déplacer le curseur d’un mot vers la droite, appuyez sur <kbd>CTRL</kbd> + <kbd>droite</kbd>.

### <a name="move-to-a-lines-beginning-or-end"></a>Atteindre le début ou la fin d’une ligne

Pour passer au début d’une ligne, appuyez sur <kbd>origine</kbd>.

Pour passer à la fin d’une ligne, appuyez sur <kbd>fin</kbd>.

Si des lignes ont été ajoutées, appuyez deux fois sur <kbd>orig</kbd> ou sur <kbd>Terminer</kbd> pour vous déplacer au début ou à la fin des lignes.

### <a name="delete-characters"></a>Supprimer les caractères

Pour supprimer le caractère situé derrière la position du curseur, appuyez sur la touche <kbd>retour arrière</kbd>.

Pour supprimer le caractère à la position du curseur, appuyez sur la touche <kbd>Suppr</kbd>.

### <a name="delete-characters-from-a-line"></a>Supprimer des caractères d’une ligne

Pour supprimer tous les caractères à partir de la position du curseur jusqu’à la fin d’une ligne, appuyez sur <kbd>CTRL</kbd> + <kbd>fin</kbd>.

Pour supprimer tous les caractères à partir de la position du curseur jusqu’au début d’une ligne, appuyez sur la <kbd>touche Ctrl</kbd> + <kbd>orig</kbd>.

Si des lignes ont été ajoutées, les caractères sont supprimés de la ligne active et les lignes qui ont été ajoutées.

### <a name="insert-and-overstrike-mode"></a>Mode insertion et Refrappe

Pour passer en mode de remplacement, appuyez sur <kbd>Insérer</kbd>. Pour revenir au mode insertion, appuyez de nouveau sur <kbd>Insérer</kbd> .

### <a name="tab-completion"></a>Saisie semi-automatique via la touche Tab

Pour terminer un nom d’applet de commande, un paramètre ou un chemin d’accès, appuyez sur la touche <kbd>Tab</kbd> . Pour faire défiler une liste de valeurs, appuyez de nouveau sur la touche <kbd>Tab</kbd> .

## <a name="see-also"></a>Voir aussi

[about_Command_Syntax](about_Command_Syntax.md)

[about_Path_Syntax](about_Path_Syntax.md)

[about_PSReadline](../../PSReadline/About/about_PSReadline.md)
