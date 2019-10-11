---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Création de ressources DSC Windows PowerShell personnalisées
ms.openlocfilehash: f0f35e8d0083d302f142f2215c9f28fee411eb07
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952846"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Création de ressources DSC Windows PowerShell personnalisées

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La configuration de l’état souhaité (DSC) de Windows PowerShell comprend des ressources intégrées que vous pouvez utiliser pour configurer votre environnement. Cette rubrique constitue une présentation du développement de ressources et fournit des liens vers des rubriques contenant des informations spécifiques et des exemples.

## <a name="dsc-resource-components"></a>Composants de la ressource DSC

Une ressource DSC est un module Windows PowerShell. Le module contient à la fois le schéma (la définition des propriétés configurables) et l’implémentation (le code qui effectue le travail spécifié par une configuration) de la ressource. Un schéma de ressources DSC peut être défini dans un fichier MOF et l’implémentation est effectuée par un module de script. À partir de la version 5 des classes PowerShell, le schéma et l’implémentation peuvent être définis dans une classe. Les rubriques suivantes expliquent plus en détail comment créer des ressources DSC.

* [Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md)
* [Implementing a DSC resource in C#](authoringResourceMofCS.md)
* [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](authoringResourceClass.md)
* [Ressources composites : Utiliser une configuration DSC comme ressource](authoringResourceComposite.md)
* [Utilisation du Concepteur de ressources](authoringResourceMofDesigner.md)
