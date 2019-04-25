---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Retirer des packages de la liste
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084111"
---
# <a name="unlisting-packages"></a>Retirer des packages de la liste

**Pourquoi la suppression d’un package de PowerShell Gallery n’est-elle pas proposée en option ?**

PowerShell Gallery ne gère pas la suppression définitive de packages par des utilisateurs.
Cela permet à d’autres utilisateurs d’ajouter des dépendances vis-à-vis de vos packages sans avoir à se soucier de risques d’arrêts.
Par exemple, si le module Pester dépend du module Azure et que le module Azure est supprimé de la galerie, l’utilisateur ne peut plus utiliser le module Pester.

Toutefois, plutôt que de supprimer un package, vous pouvez le retirer de la liste.

**À quoi sert le retrait d’un package sur PowerShell Gallery ?**

Lorsqu’un package, comme un module ou un script, est retiré de la liste sur PowerShell Gallery, il est supprimé de l’onglet Packages. Par ailleurs, il n’est plus détectable à l’aide de la barre de recherche.
La seule façon de le télécharger consiste à spécifier son nom et sa version exacts.
Le retrait d’un package de la liste ne provoque donc pas l’arrêt des modules ou des scripts qui en dépendent.

Pour retirer votre package de la liste, accédez à la page des détails du package, puis sélectionnez « Supprimer le module ». Décochez la case « Répertorié », puis cliquez sur Enregistrer.

**Comment supprimer un package ?**

Si vous vous trouvez dans une situation nécessitant la suppression d’un package, contactez les administrateurs PowerShell Gallery.
Les scénarios de suppression valides sont les suivants :
- Problèmes de violation des droits d’auteur.
- Contenu potentiellement dangereux.
- Package contenant des données sensibles.

Pour soumettre une demande de suppression de package aux administrateurs PowerShell Gallery, accédez à la page des détails de votre package, puis sélectionnez Contacter le support.
