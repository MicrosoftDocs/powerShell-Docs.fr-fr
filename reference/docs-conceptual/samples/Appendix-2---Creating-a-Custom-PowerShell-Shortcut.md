---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: 'Annexe 2 : création d’un raccourci PowerShell personnalisé'
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057845"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Annexe 2 : création d’un raccourci PowerShell personnalisé

La procédure suivante décrit comment créer un raccourci vers Windows PowerShell offrant plusieurs options pratiques personnalisées.

1. Créez un raccourci qui pointe vers Powershell.exe.

2. Cliquez avec le bouton droit sur le raccourci, puis cliquez sur **Propriétés**.

3. Cliquez sur l’onglet **Options**.

4. Dans la section **Modifier les options**, activez la case à cocher **QuickEdit**.

    Ce paramètre permet de sélectionner du texte dans la fenêtre de console Windows PowerShell en faisant glisser tout en appuyant sur le bouton gauche de la souris, et permet de copier du texte dans le Presse-papiers en appuyant sur Entrée ou en cliquant avec le bouton droit.

5. Dans la section **Modifier les options**, activez la case à cocher **Mode insertion**. Ce paramètre permet de cliquer avec le bouton droit dans la fenêtre de console pour coller automatiquement du texte à partir du Presse-papiers.

6. Dans la section **Historique des commandes**, dans le champ **Taille de la mémoire tampon**, tapez ou sélectionnez un nombre compris entre 1 et 999. Cela a pour effet de définir le nombre de commandes saisies qui sont conservées dans la mémoire tampon de la console.

7. Dans la section **Historique des commandes**, activez la case à cocher **Supprimer les doublons** pour éliminer les commandes répétées de la mémoire tampon de la console.

8. Cliquez sur l’onglet **Disposition**.

9. Dans la section **Mémoire tampon d’écran**, dans le champ **Hauteur**, tapez un nombre compris entre 1 et 9999. La hauteur représente le nombre de lignes de sortie qui sont mises en mémoire tampon. Il s’agit du nombre maximal de lignes conservées pour affichage lorsque vous faites défiler la fenêtre de console. Si ce nombre est inférieur à la hauteur affichée dans la section **Taille de la fenêtre**, la hauteur de la fenêtre est automatiquement réduite la même valeur.

10. Dans la section **Taille de la fenêtre**, tapez un nombre compris entre 1 et 9999 pour la largeur. Ce nombre représente le nombre de caractères qui s’affichent dans la fenêtre de console. La largeur par défaut est 80, et la mise en forme de la sortie de Windows PowerShell est conçue pour cette largeur.

11. Si vous souhaitez placer la console à un endroit particulier sur le Bureau quand elle est ouverte, désactivez la case à cocher **Positionnée par le système** dans la section **Position de la fenêtre**, puis modifiez les valeurs des champs **Gauche** et **Haut** dans la section **Position de la fenêtre**.

12. Cliquez sur **OK**.