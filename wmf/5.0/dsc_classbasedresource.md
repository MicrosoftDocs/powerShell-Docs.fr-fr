---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221848"
---
# <a name="class-based-dsc-resources"></a>Ressources DSC basées sur une classe

## <a name="defining-dsc-resources-with-classes"></a>Définition de ressources DSC avec des classes

Suite à vos commentaires, nous avons simplifié la création et la compréhension des ressources DSC basées sur des classes.
Les principales différences entre une ressource DSC basée sur une classe et un fournisseur de ressources DSC d’applet de commande sont les suivantes :

* Aucun fichier MOF pour le schéma n’est nécessaire.
* Aucun sous-dossier **DSCResource** dans le dossier de module n’est nécessaire.
* Un fichier de module PowerShell peut contenir plusieurs classes de ressources DSC.

Pour plus d’informations, consultez [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).
