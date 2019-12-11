---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objectif du modèle objet de script Windows PowerShell ISE
ms.openlocfilehash: e59593ef06911c709e92fa7a1eabd96d2636ca30
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030911"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Objectif du modèle objet de script Windows PowerShell ISE

Les objets sont associés aux forme et fonction de Windows PowerShell Integrated Scripting Environment (ISE). La référence du modèle objet fournit des détails sur les propriétés et méthodes membres exposées par ces objets. Des exemples sont fournis pour montrer comment vous pouvez utiliser des scripts pour accéder directement à ces méthodes et propriétés. Le modèle objet de script facilite l’éventail des tâches suivantes.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Personnalisation de l’apparence de Windows PowerShell ISE

Vous pouvez utiliser le modèle objet pour modifier les options et paramètres de l’application. Vous pouvez, par exemple, les modifier comme suit :

- Vous pouvez modifier la couleur des erreurs, des avertissements, des sorties détaillées et des sorties de débogage.
- Vous pouvez obtenir ou définir les couleurs d’arrière-plan pour les volets Commande, Sortie et Script.
- Vous pouvez définir la couleur de premier plan du volet Sortie.
- Vous pouvez définir le nom et la taille de la police pour Windows PowerShell ISE.
- Vous pouvez configurer des avertissements, notamment les avertissements émis quand un fichier est ouvert dans plusieurs onglets PowerShell ou qu’un script dans le fichier s’exécute avant que celui-ci n’ait été enregistré.
- Vous pouvez basculer entre une vue où le volet Script et le volet Sortie sont côte à côte et une vue où le volet Script est au-dessus du volet Sortie. Vous pouvez ancrer le volet Commande en bas ou en haut du volet Sortie.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Amélioration des fonctionnalités de Windows PowerShell ISE

Vous pouvez utiliser le modèle objet pour améliorer les fonctionnalités de Windows PowerShell ISE. Par exemple, vous pouvez :

- Ajouter et modifier l’instance de Windows PowerShell ISE lui-même. Par exemple, pour modifier les menus, vous pouvez ajouter de nouveaux éléments de menu et mapper les nouveaux éléments de menu à des scripts.
- Créer des scripts qui effectuent certaines des tâches que vous pouvez effectuer à l’aide des commandes de menu et des boutons disponibles dans Windows PowerShell ISE. Par exemple, vous pouvez ajouter, supprimer ou sélectionner un onglet PowerShell.
- Effectuer des tâches réalisables à l’aide des boutons et des commandes de menu. Par exemple, vous pouvez renommer un onglet PowerShell.
- Manipuler des tampons de texte pour les volets Commande, Sortie et Script associés à un fichier. Par exemple, vous pouvez :
  - Obtenir ou définir tout le texte.
  - Obtenir ou définir une sélection de texte.
  - Exécuter un script ou une partie sélectionnée d’un script.
  - Faire défiler l’affichage jusqu’à une ligne spécifique.
  - Insérer du texte à l’emplacement du signe d’insertion.
  - Sélectionner un bloc de texte.
  - Obtenir le numéro de la dernière ligne.
- Effectuer des opérations de fichier. Par exemple, vous pouvez :
  - Ouvrir un fichier, enregistrer un fichier ou enregistrer un fichier sous un nom différent.
  - Déterminer si un fichier a été modifié depuis son dernier enregistrement.
  - Obtenir le nom du fichier.
  - Sélectionner un fichier.

## <a name="automating-tasks"></a>Automatisation des tâches

Vous pouvez utiliser le modèle objet de script pour créer des raccourcis clavier pour les opérations fréquentes.

## <a name="see-also"></a>Voir aussi

- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)
