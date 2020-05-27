---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Configuration d’un client collecteur DSC
ms.openlocfilehash: 7c68f4c59170c672e7573de7e7e595a60a81c966
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561101"
---
# <a name="setting-up-a-dsc-pull-client"></a>Configuration d’un client collecteur DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités. Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).

Chaque nœud cible doit recevoir l’instruction d’utiliser le mode par extraction ainsi que l’URL ou l’emplacement du fichier où contacter le serveur collecteur pour obtenir des configurations et des ressources, et où envoyer les données du rapport.

Les rubriques suivantes expliquent comment configurer les clients collecteurs :

* [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md)
* [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md)

> [!NOTE]
> Ces rubriques s’appliquent à PowerShell 5.0. Pour configurer un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md).
