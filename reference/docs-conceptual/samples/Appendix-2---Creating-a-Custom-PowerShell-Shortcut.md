---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: 'Annexe 2 : création d’un raccourci PowerShell personnalisé'
description: La procédure suivante décrit comment créer un raccourci vers Windows PowerShell offrant plusieurs options pratiques personnalisées.
ms.openlocfilehash: abdab517dec1357050bf431b6f2e35311ad49976
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500723"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Annexe 2 : création d’un raccourci PowerShell personnalisé

La procédure suivante décrit comment créer un raccourci vers Windows PowerShell offrant plusieurs options pratiques personnalisées.

1. Créez un raccourci qui pointe vers Powershell.exe.

1. Cliquez avec le bouton droit sur le raccourci, puis cliquez sur **Propriétés** .

1. Cliquez sur l’onglet **Options** .

1. Dans la section **Modifier les options** , activez la case à cocher **QuickEdit** .

    Ce paramètre permet de sélectionner du texte dans la fenêtre de console Windows PowerShell en appuyant sur le bouton gauche de la souris tout en la faisant glisser, et permet de copier du texte dans le Presse-papiers en appuyant sur Entrée ou en cliquant avec le bouton droit.

1. Dans la section **Modifier les options** , activez la case à cocher **Mode insertion** . Ce paramètre permet de cliquer avec le bouton droit dans la fenêtre de console pour coller automatiquement du texte à partir du Presse-papiers.

1. Dans la section **Historique des commandes** , dans le champ **Taille de la mémoire tampon** , tapez ou sélectionnez un nombre compris entre 1 et 999. Cela a pour effet de définir le nombre de commandes saisies qui sont conservées dans la mémoire tampon de la console.

1. Dans la section **Historique des commandes** , activez la case à cocher **Supprimer les doublons** pour éliminer les commandes répétées de la mémoire tampon de la console.

1. Cliquez sur l’onglet **Disposition** .

1. Dans la section **Mémoire tampon d’écran** , dans le champ **Hauteur** , tapez un nombre compris entre 1 et 9999. La hauteur représente le nombre de lignes de sortie qui sont mises en mémoire tampon. Il s’agit du nombre maximal de lignes conservées pour affichage lorsque vous faites défiler la fenêtre de console. Si ce nombre est inférieur à la hauteur affichée dans la section **Taille de la fenêtre** , la hauteur de la fenêtre est automatiquement réduite la même valeur.

1. Dans la section **Taille de la fenêtre** , tapez un nombre compris entre 1 et 9999 pour la largeur. Ce nombre représente le nombre de caractères qui s’affichent dans la fenêtre de console. La largeur par défaut est 80, et la mise en forme de la sortie de Windows PowerShell est conçue pour cette largeur.

1. Si vous souhaitez placer la console à un endroit particulier sur le Bureau quand elle est ouverte, décochez la case **Positionnée par le système** dans la section **Position de la fenêtre** , puis modifiez les valeurs des champs **Gauche** et **Haut** dans la section **Position de la fenêtre** .

1. Cliquez sur **OK** .
