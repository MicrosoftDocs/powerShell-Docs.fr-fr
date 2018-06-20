---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell
ms.openlocfilehash: c9069d7c9ce9c614330e36a42233b00363660a4b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187474"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

DSC est une plateforme de gestion dans PowerShell qui vous permet de gérer votre infrastructure informatique et de développement avec la configuration en tant que code.

- Pour une vue d’ensemble des avantages métier de DSC, consultez [Présentation de la configuration de l’état souhaité pour les décideurs](decisionMaker.md).
- Pour une vue d’ensemble des avantages de l’utilisation de DSC en termes d’ingénierie, consultez [Présentation de la configuration de l’état souhaité pour les ingénieurs](DscForEngineers.md).
- Pour commencer à utiliser rapidement DSC, consultez [Démarrage rapide avec DSC](quickStart.md).

## <a name="key-concepts"></a>Concepts clés

DSC est une plateforme déclarative employée pour la configuration, le déploiement et la gestion des systèmes. Elle réunit trois composants principaux :

- Les [configurations](configurations.md) sont des scripts PowerShell déclaratifs qui définissent et configurent des instances de ressources.
    Quand une configuration est exécutée, DSC (et toutes les ressources appelées par cette configuration) « fait simplement en sorte » que le système se trouve dans l’état souhaité défini par la configuration.
    Les configurations DSC sont également idempotent, c’est-à-dire que le Gestionnaire de configuration local (ou « LCM ») s’assure en permanence que les machines restent configurées dans l’état déclaré dans la configuration.
- Les [ressources](resources.md) constituent la base de DSC. Elles contiennent le code qui place et conserve la cible d’une configuration dans l’état spécifié.
    Les ressources sont stockées dans les modules PowerShell et peuvent être créées pour modéliser des éléments généraux, comme un fichier ou un processus Windows, ou des éléments plus spécifiques, tels qu’un serveur IIS ou une machine virtuelle Azure.
- Le [LCM](metaConfig.md) est le moteur utilisé par DSC pour faciliter les interactions entre les ressources et les configurations.
    Le LCM interroge régulièrement le système, via le flux de contrôle implémenté par les ressources, pour s’assurer que le système est dans l’état déclaré dans une configuration.
    Si le système n’est pas dans l’état souhaité, le LCM effectue des appels aux code dans les ressources pour « faire en sorte » qu’il soit conforme à l’état déclaré dans la configuration.

## <a name="see-also"></a>Voir aussi

- [Configurations DSC](configurations.md)
- [Ressources DSC](resources.md)
- [Configuration du Gestionnaire de configuration local](metaConfig.md)