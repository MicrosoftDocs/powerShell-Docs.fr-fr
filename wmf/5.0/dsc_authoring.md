---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: ec4ae8e4b2ef0ec226cb75607f7aaf34b48f6b76
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085641"
---
# <a name="authoring-improvements-using-powershell-ise"></a>Améliorations liées à la création à l’aide de PowerShell ISE

Créer des configurations DSC dans Windows PowerShell ISE est beaucoup plus facile grâce aux améliorations suivantes :

- Énumération de toutes les ressources DSC dans un bloc **configuration** ou **node** en entrant **Ctrl+Espace** sur une ligne vide dans le bloc.
- Saisie semi-automatique sur les propriétés de ressources de type **énumération**.
- Saisie semi-automatique sur la propriété **DependsOn** des ressources DSC, basée sur d’autres instances de ressources dans la configuration.
- Meilleure saisie semi-automatique via la touche Tab pour les valeurs de propriétés de ressources.

**Remarque :** vous devez avoir une chaîne vide comme valeur des propriétés de ressources pour pouvoir lister les options avec Ctrl+Espace. Une pression sur la touche **Tab** permet de parcourir les options.
