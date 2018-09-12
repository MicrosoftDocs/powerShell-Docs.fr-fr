---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Présentation de la configuration de l’état souhaité pour les décideurs
ms.openlocfilehash: 7c36aa5fadeab8bcb381f316288d102b5ce402e2
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339835"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Présentation de la configuration de l’état souhaité pour les décideurs

Ce document décrit les avantages de l’utilisation de la configuration de l’état souhaité (DSC) Windows PowerShell en entreprise. Il ne s’agit pas d’un guide technique.

## <a name="what-is-desired-state-configuration"></a>Qu’est-ce que la configuration de l’état souhaité ?

La configuration d’état souhaité PowerShell est une plateforme de gestion de la configuration intégrée à Windows, basée sur des standards ouverts. DSC est suffisamment flexible pour fonctionner de manière fiable et cohérente à chaque étape du cycle de vie de déploiement (développement, test, préproduction, production), ainsi qu’au cours d’une montée en puissance parallèle.

DSC repose sur des [configurations](configurations.md).
Une configuration est un document facile à lire qui décrit un environnement d’ordinateurs (ou « nœuds ») ayant des caractéristiques spécifiques.
Ces caractéristiques peuvent être aussi simples que de vérifier qu’une fonctionnalité spécifique de Windows est activée, et aussi complexes que de déployer SharePoint.

DSC comprend également des fonctions intégrées d’analyse et de création de rapports.
Si un système n’est plus conforme, DSC peut déclencher une alerte et corriger le système.

## <a name="benefits-of-using-desired-state-configuration"></a>Avantages de l’utilisation de la configuration de l’état souhaité

Les configurations sont conçues pour être facilement lues, stockées et mises à jour.
Les configurations déclarent l’état dans lequel doivent être les appareils cibles. Vous n’avez donc pas à écrire d’instructions sur l’état des appareils.
L’apprentissage, l’adoption, l’implémentation et la maintenance par le biais de DSC est une solution beaucoup moins coûteuse.

La création de configurations permet de capturer les étapes d’un déploiement complexe sous la forme d’une « source unique de vérité » à un emplacement unique.
Cela évite ainsi les erreurs lors de déploiements répétés d’un ensemble spécifique d’ordinateurs.
Par conséquent, les déploiements sont plus rapides et plus fiables, ce qui permet de réduire les délais des déploiements complexes.

Les configurations peuvent également être partagées via [PowerShell Gallery](https://powershellgallery.com), ce qui signifie que des scénarios courants et des bonnes pratiques existent peut-être déjà pour le travail que vous devez effectuer.


## <a name="desired-state-configuration-and-devops"></a>Configuration de l’état souhaité et DevOps

DSC a été conçu avec [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx)en tête, une association de personnes, de processus et d’outils qui permet un déploiement et une itération rapides qui ont pour but de fournir une valeur ajoutée aux utilisateurs finaux, internes ou externes.
Le fait de n’utiliser qu’une seule configuration pour définir un environnement signifie que les développeurs peuvent coder leurs spécifications dans une configuration et vérifier cette configuration dans le contrôle de code source. Les équipes responsables des opérations peuvent facilement déployer le code sans avoir à passer par des processus manuels sujets aux erreurs.

Les configurations sont également [basées sur les données](configData.md), ce qui permet aux opérations d’identifier et de changer plus facilement les environnements, sans intervention des développeurs.

## <a name="desired-state-configuration-on--and-off-premises"></a>Configuration d’état souhaité sur site et hors site

DSC peut être utilisé pour gérer des déploiements sur site et hors site.
Pour les solutions sur site, DSC possède un [serveur collecteur](pullServer.md) qui peut être utilisé pour centraliser la gestion des ordinateurs et créer des rapports sur leur état.
Pour les solutions cloud, DSC peut être utilisé partout où Windows est utilisable.
Il existe également des offres Azure spécifiques basées sur la configuration d’état souhaité, telles que [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), qui centralise la création de rapports DSC.

## <a name="dsc-and-compatibility"></a>DSC et compatibilité

Même si DSC a fait son apparition avec Windows Server 2012 R2, il est disponible pour les systèmes d’exploitation de bas niveau via le package WMF (Windows Management Framework).
Pour plus d’informations sur le package WMF, reportez-vous à la [page d’accueil de PowerShell](/powershell/).

DSC peut également servir à gérer Linux. Pour plus d’informations, consultez [Bien démarrer avec DSC pour Linux](lnxGettingStarted.md).
