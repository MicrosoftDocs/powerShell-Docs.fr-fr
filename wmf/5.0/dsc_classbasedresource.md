---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058112"
---
# <a name="class-based-dsc-resources"></a>Ressources DSC basées sur une classe

## <a name="defining-dsc-resources-with-classes"></a>Définition de ressources DSC avec des classes

Suite à vos commentaires, nous avons simplifié la création et la compréhension des ressources DSC basées sur des classes.
Les principales différences entre une ressource DSC basée sur une classe et un fournisseur de ressources DSC d’applet de commande sont les suivantes :

* Aucun fichier MOF pour le schéma n’est nécessaire.
* Aucun sous-dossier **DSCResource** dans le dossier de module n’est nécessaire.
* Un fichier de module PowerShell peut contenir plusieurs classes de ressources DSC.

Pour plus d’informations, consultez [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).
