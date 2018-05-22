---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressources DSC
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-resources"></a>Ressources DSC

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC. Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.

Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.  Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.

Les rubriques suivantes décrivent les ressources DSC :

- [Ressources DSC intégrées](builtInResource.md)
- [Créer des ressources DSC personnalisées](authoringResource.md)
- [Ressources DSC intégrées pour Linux](lnxBuiltInResources.md)