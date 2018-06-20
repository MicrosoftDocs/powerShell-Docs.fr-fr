---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 1595a3e817fd711c35128f06927fd57df7a63fb8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218244"
---
# <a name="authoring-improvements-using-powershell-ise"></a>Améliorations liées à la création à l’aide de PowerShell ISE

Créer des configurations DSC dans Windows PowerShell ISE est beaucoup plus facile grâce aux améliorations suivantes :

- Énumération de toutes les ressources DSC dans un bloc **configuration** ou **node** en entrant **Ctrl+Espace** sur une ligne vide dans le bloc.
- Saisie semi-automatique sur les propriétés de ressources de type **énumération**.
- Saisie semi-automatique sur la propriété **DependsOn** des ressources DSC, basée sur d’autres instances de ressources dans la configuration.
- Meilleure saisie semi-automatique via la touche Tab pour les valeurs de propriétés de ressources.

**Remarque :** Vous devez avoir une chaîne vide pour les valeurs de propriétés de ressources pour pouvoir utiliser Ctrl+Espace pour répertorier les options. Une pression sur la touche **Tab** permet de parcourir les options.
