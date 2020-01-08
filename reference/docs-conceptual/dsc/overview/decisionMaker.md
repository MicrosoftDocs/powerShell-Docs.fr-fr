---
ms.date: 10/11/2019
keywords: dsc,powershell,configuration,installation
title: Présentation de la configuration de l’état souhaité pour les décideurs
ms.openlocfilehash: b6d483d105c2d3b9be7215be36397d452338c7f1
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737251"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Présentation de la configuration de l’état souhaité pour les décideurs

Ce document décrit les avantages de l’utilisation de la configuration de l’état souhaité (DSC) PowerShell en entreprise : il ne s’agit pas d’un guide technique.

## <a name="what-is-dsc"></a>Qu’est-ce que la configuration de l’état souhaité (DSC) ?

PowerShell DSC est une plateforme de gestion de la configuration intégrée à Windows, basée sur des standards ouverts. DSC est suffisamment flexible pour fonctionner de manière fiable et cohérente à chaque étape du cycle de vie de déploiement (développement, test, préproduction, production), ainsi qu’au cours d’une montée en puissance parallèle.

DSC repose sur des [configurations](../configurations/configurations.md). Une configuration est un script PowerShell qui décrit un environnement d’ordinateurs, ou nœuds, ayant des caractéristiques spécifiques. Ces caractéristiques peuvent être aussi simples que de vérifier qu’une fonctionnalité spécifique de Windows est activée, et aussi complexes que de déployer SharePoint.

DSC comprend des fonctions intégrées d’analyse et de création de rapports. Si un système n’est plus conforme, DSC peut déclencher une alerte et corriger le système.

## <a name="benefits-of-using-dsc"></a>Avantages de l'utilisation de DSC

La conception de la configuration simplifie la lecture, le stockage et la mise à jour. Les configurations déclarent l’état des appareils cibles au lieu d’écrire des instructions sur la façon de placer les appareils dans cet état. Ces facteurs réduisent les coûts liés à l’apprentissage, l’adoption, l’implémentation et la maintenance par le biais de DSC.

La création de configurations permet de capturer les étapes d’un déploiement complexe sous la forme d’une **source unique de vérité** à un emplacement unique. Les configurations évitent ainsi les erreurs lors de déploiements répétés d’un ensemble spécifique d’ordinateurs. Et les déploiements sont plus rapides et plus fiables, ce qui permet de réduire les délais des déploiements complexes.

Les configurations peuvent être partagées via [PowerShell Gallery](https://powershellgallery.com). Des scénarios courants et de meilleures pratiques sont peut-être déjà disponibles pour le travail que vous devez effectuer.

## <a name="dsc-and-devops"></a>DSC et DevOps

DSC a été conçu autour de [DevOps](/archive/blogs/ashleymcglone/devops-for-n00bs-ie-windows-people-like-me). Il s’agit d’une association de personnes, de processus et d’outils qui permet un déploiement et une itération rapides centrés sur l’offre de valeur aux utilisateurs finaux, internes ou externes. Le fait de n’utiliser qu’une seule configuration pour définir un environnement signifie que les développeurs peuvent coder leurs spécifications dans une configuration et vérifier cette configuration dans le contrôle de code source. Les équipes responsables des opérations peuvent ainsi facilement déployer le code sans avoir à passer par des processus manuels sujets aux erreurs.

Les configurations sont [basées sur les données](../configurations/configData.md). Les données définies permettent aux opérations d’identifier et de changer plus facilement les environnements, sans intervention des développeurs.

## <a name="dsc-on-premises-and-off-premises"></a>DSC sur site et hors site

DSC permet de gérer des déploiements sur site et hors site. Pour les solutions sur site, DSC possède un [serveur collecteur](../pull-server/pullServer.md) utilisé pour centraliser la gestion des ordinateurs et créer des rapports sur leur état. Pour les solutions de cloud hors site, DSC peut être utilisé partout où Windows est disponible.
Il existe des offres Azure spécifiques basées sur DSC, notamment [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), qui centralise la création de rapports DSC.

## <a name="dsc-and-compatibility"></a>DSC et compatibilité

DSC a fait son apparition avec Windows Server 2012 R2, il est disponible pour les systèmes d’exploitation de bas niveau via le WMF (Windows Management Framework). Pour plus d'informations sur WMF, voir [Windows Management Framework](/powershell/scripting/wmf/overview).

DSC peut servir à gérer Linux. Pour plus d’informations, consultez [Bien démarrer avec DSC pour Linux](../getting-started/lnxGettingStarted.md).
