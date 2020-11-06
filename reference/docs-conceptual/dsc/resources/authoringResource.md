---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,installation
title: Création de ressources DSC Windows PowerShell personnalisées
description: Cet article constitue une présentation du développement de ressources et fournit des liens vers des articles contenant des informations spécifiques et des exemples.
ms.openlocfilehash: ff9a0c8ae10583155217fbeccc62e6e1c94f9a11
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656403"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Création de ressources DSC Windows PowerShell personnalisées

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La configuration de l’état souhaité (DSC) de Windows PowerShell comprend des ressources intégrées que vous pouvez utiliser pour configurer votre environnement. Cet article constitue une présentation du développement de ressources et fournit des liens vers des articles contenant des informations spécifiques et des exemples.

## <a name="dsc-resource-components"></a>Composants de la ressource DSC

Une ressource DSC est un module Windows PowerShell. Le module contient à la fois le schéma (la définition des propriétés configurables) et l’implémentation (le code qui effectue le travail spécifié par une configuration) de la ressource. Un schéma de ressources DSC peut être défini dans un fichier MOF et l’implémentation est effectuée par un module de script. À partir de la version 5 des classes PowerShell, le schéma et l’implémentation peuvent être définis dans une classe. Les articles suivants expliquent plus en détail comment créer des ressources DSC.

- [Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md)
- [Implementing a DSC resource in C#](authoringResourceMofCS.md)
- [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](authoringResourceClass.md)
- [Ressources composites : utilisation d’une configuration DSC comme ressource](authoringResourceComposite.md)
- [Utilisation du Concepteur de ressources](authoringResourceMofDesigner.md)
