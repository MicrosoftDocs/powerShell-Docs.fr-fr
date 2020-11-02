---
ms.date: 06/12/2017
title: Retirer des packages de la liste
description: PowerShell Gallery ne gère pas la suppression définitive de packages par des utilisateurs. Cela permet à d’autres utilisateurs d’ajouter des dépendances vis-à-vis de vos packages sans avoir à se soucier de risques d’arrêts.
ms.openlocfilehash: 738167011f64b5174df3504c8e1d06146f4c7db5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662429"
---
# <a name="unlisting-packages"></a>Retirer des packages de la liste

**Pourquoi la suppression d’un package de PowerShell Gallery n’est-elle pas proposée en option ?**

PowerShell Gallery ne gère pas la suppression définitive de packages par des utilisateurs. Cela permet à d’autres utilisateurs d’ajouter des dépendances vis-à-vis de vos packages sans avoir à se soucier de risques d’arrêts.
Par exemple, si le module Pester dépend du module Azure et que le module Azure est supprimé de la galerie, les utilisateurs ne peuvent plus utiliser le module Pester.

Au lieu de supprimer un package, vous pouvez ne plus le répertorier.

**À quoi sert le retrait d’un package sur PowerShell Gallery ?**

Lorsqu’un package, comme un module ou un script, est retiré de la liste sur PowerShell Gallery, il est supprimé de l’onglet Packages. Par ailleurs, il n’est plus détectable à l’aide de la barre de recherche. La seule façon de le télécharger consiste à spécifier son nom et sa version exacts. Le retrait d’un package de la liste ne provoque donc pas l’arrêt des modules ou des scripts qui en dépendent.

Pour retirer votre package de la liste, accédez à la page des détails du package, puis sélectionnez « Supprimer le module ». Décochez la case « Répertorié », puis sélectionnez « Enregistrer ».

**Comment supprimer un package ?**

Si vous vous trouvez dans une situation nécessitant la suppression d’un package, contactez les administrateurs PowerShell Gallery. Les scénarios de suppression valides sont les suivants :

- Problèmes de violation des droits d’auteur.
- Contenu potentiellement dangereux.
- Package contenant des données sensibles.

Pour soumettre une demande de suppression de package aux administrateurs PowerShell Gallery, accédez à la page des détails de votre package, puis sélectionnez Contacter le support.
