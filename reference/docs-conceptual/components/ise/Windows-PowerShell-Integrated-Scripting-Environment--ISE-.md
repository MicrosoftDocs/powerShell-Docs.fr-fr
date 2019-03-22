---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Environnement d’écriture de scripts intégré de Windows PowerShell ISE
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 3002c2cb7213b1c2d7201dddf5ff3c0651fad767
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054711"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Environnement d'écriture de scripts intégré de Windows PowerShell

L’environnement d’écriture de scripts intégré de Windows PowerShell (ISE) est l’un des deux ordinateurs hôtes pour le moteur et le langage Windows PowerShell. Il permet d’écrire, d’exécuter et de tester des scripts d’une manière que la console Windows PowerShell ne permet pas. L’environnement ISE ajoute la coloration de la syntaxe, la saisie semi-automatique via la touche Tab, IntelliSense, le débogage visuel et l’aide contextuelle.

L’environnement ISE permet d’exécuter des commandes dans un volet Console, et prend également en charge des volets que vous pouvez utiliser pour afficher simultanément le code source de votre script et d’autres outils pouvant s’intégrer à l’environnement ISE. Vous pouvez même ouvrir plusieurs fenêtres de script en même temps, ce qui est particulièrement utile lorsque vous déboguez un script qui utilise des fonctions définies dans d’autres scripts ou modules.

## <a name="whats-new"></a>Nouveautés

Voici quelques-unes des fonctionnalités qui ont été ajoutées à l’environnement ISE dans les versions les plus récentes de PowerShell.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>Ajouté dans PowerShell 3.0 (Windows Server 2012, Windows 8)

**IntelliSense** complète automatiquement vos commandes en affichant des menus d’applets de commande, de paramètres, de valeurs de paramètres, de fichiers ou de dossiers correspondants à mesure que vous tapez.

Les **extraits de code** sont de courtes sections de code que vous pouvez aisément insérer dans les scripts que vous écrivez. Une collection d’extraits de code utiles est incluse dans la zone et vous pouvez faire davantage à l’aide de l’applet de commande **New-Snippet**.

Vous pouvez créer des **outils complémentaires** qui ajoutent des fonctionnalités à l’environnement ISE en écrivant du code qui interagit avec le [Modèle objet de script Windows PowerShell ISE](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

Ces outils peuvent afficher des contrôles dans un volet à onglets ou fonctionner de manière invisible en arrière-plan. Le composant additionnel **Commands** en est un bon exemple. Il est inclus dans les versions 3.0 et ultérieure qui affichent la liste des commandes disponibles et leur aide.

Le **Gestionnaire de démarrage et enregistrement automatique** enregistre automatiquement vos scripts toutes les deux minutes pour vous éviter de perdre votre travail en cas de panne ou de redémarrage inattendu.

La **liste Utilisé(s) récemment** fait désormais partie du menu Ouvrir le fichier. Elle facilite l’accès aux fichiers que vous utilisez le plus souvent.

**Volet Console fusionné**. Les versions précédentes de l’environnement ISE comportaient des volets Commande et Sortie distincts. Ceux-ci sont désormais regroupés dans un seul volet qui reflète plus fidèlement ce que vous voyez dans la console Windows PowerShell.

**Commutateurs de ligne de commande**. Plusieurs nouveaux commutateurs de ligne de commande vous de mieux contrôler le fonctionnement de l’environnement ISE. -NoProfile démarre l’environnement ISE sans exécuter de script de profilage. -Help ouvre une fenêtre d’aide avec l’environnement ISE. -mta démarre l’environnement ISE en « mode de multithread cloisonné ». Le mode par défaut est monothread.

Les **nouvelles fonctionnalités de l’éditeur** facilitent la création et la lecture de votre code :

- **Coloration de la syntaxe XML**. L’éditeur ISE colore désormais la syntaxe XML de la même façon que la syntaxe du code Windows PowerShell.

- **Correspondance d’accolade**. Windows PowerShell ISE met en surbrillance les accolades correspondantes afin que vous puissiez vous assurer que le nombre d’accolades fermantes est égal au nombre d’accolades ouvrantes. Pour localiser l’accolade fermante correspondant à l’accolade ouvrante sur laquelle le curseur est positionné, utilisez CTRL-\[.

- **Mode Plan**. Vous pouvez réduire ou développer des sections de votre code en cliquant sur les signes plus et moins dans la marge de gauche. Cela facilite la recherche du code souhaité dans un script long.

- **Édition du texte par glisser-déplacer**. Vous pouvez sélectionner un bloc de texte et le faire glisser vers un autre emplacement pour le déplacer. En maintenant la touche Ctrl enfoncée pendant que vous faites glisser le texte sélectionné, vous copiez celui-ci au lieu de le déplacer.

- **Affichage des erreurs d’analyse**. Windows PowerShell examine votre script en cours de frappe. S’il détecte une erreur, il affiche une ligne ondulée rouge sous le code douteux. Lorsque vous pointez sur l’erreur indiquée, une info-bulle affiche le problème détecté.

- **Zoom**. Vous pouvez effectuer un zoom avant sur votre texte pour en faciliter la lecture, ou effectuer un zoom arrière pour afficher une vue plus large à l’aide du curseur figurant dans l’angle inférieur droit de la fenêtre ISE.

- **Copier-coller de texte enrichi**. Lorsque vous copiez à partir de l’environnement ISE vers le Presse-papiers, la police, la taille et les informations de couleur du texte sélectionné sont conservées.

- **Sélection de bloc**. Vous pouvez sélectionner un bloc de texte en maintenant la touche Alt enfoncée pendant que vous sélectionnez le texte dans le volet Script à l’aide de la souris, ou en appuyant sur **Alt+Maj+Flèche**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>Ajouté dans PowerShell 2.0 (Windows Server 2008 R2, Windows 7)

L’environnement ISE a été introduit avec PowerShell v2.0.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Configuration requise pour l’exécution de Windows PowerShell ISE

L’environnement ISE est disponible sur tout ordinateur Windows pouvant exécuter Windows PowerShell v2.0 ou version ultérieure. Chaque version de Windows et de Windows Server inclut une version de Windows PowerShell ISE, mais vous pouvez procéder à une mise à niveau vers la version la plus récente disponible en installant WMF (Windows Management Framework). Pour plus d’informations, consultez la documentation de [WMF](/powershell/wmf).

> [!NOTE]
> Étant donné que Windows PowerShell ISE nécessite une interface graphique utilisateur, vous ne pouvez pas l’exécuter sur l’option d’installation minimale de Windows Server.

## <a name="see-also"></a>Voir aussi

[Objectif du modèle objet de script Windows PowerShell ISE](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)