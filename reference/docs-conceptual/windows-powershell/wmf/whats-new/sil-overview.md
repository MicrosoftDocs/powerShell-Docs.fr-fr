---
ms.date: 06/12/2017
title: Journalisation de l’inventaire logiciel
description: WMF 5. x ajoute des fonctionnalités de journalisation de l’inventaire logiciel qui vous permettent de collecter des informations sur les logiciels installés dans un emplacement central pour faciliter la gestion et l’audit.
ms.openlocfilehash: 85e261782a3df5fe5561a80529ba699d686a8779
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646614"
---
# <a name="software-inventory-logging-sil"></a>Journalisation de l’inventaire logiciel

> [!IMPORTANT]
> Après avoir installé WMF 5.x sur un serveur Windows Server 2012 R2 sur lequel la Journalisation de l’inventaire logiciel tourne déjà, il est nécessaire d’exécuter une fois la cmdlet Start-SilLogging, car le processus d’installation arrête la fonctionnalité de Journalisation de l’inventaire logiciel de façon non contrôlée.

La journalisation de l’inventaire logiciel aide à réduire les coûts d’exploitation liés à l’obtention d’informations précises concernant les logiciels Microsoft installés localement sur un serveur, mais plus particulièrement sur de nombreux serveurs d’un environnement informatique (en supposant que les logiciels soient installés et en cours d’exécution dans l’environnement informatique). Vous pouvez alors transférer ces données à un serveur d’agrégation et recueillir les données des journaux dans un emplacement centralisé à l’aide d’un processus uniforme et automatique.

Même si vous pouvez aussi journaliser les données d’inventaire logiciel en interrogeant directement chaque ordinateur, la journalisation de l’inventaire logiciel, en utilisant une architecture de transmission (par le biais le réseau) mise en œuvre par chaque serveur, permet de relever les défis liés à la découverte des serveurs, défis typiques de nombreux scénarios de gestion des actifs et d’inventaire logiciel. La journalisation de l’inventaire logiciel utilise le protocole SSL pour sécuriser les données qui sont transférées à un serveur d’agrégation par le biais du protocole HTTPS. Le stockage des données dans un emplacement centralisé facilite l’analyse, la manipulation et le partage des données en cas de besoin.

Aucune de ces données n’est envoyée à Microsoft dans le cadre du fonctionnement de la fonctionnalité. Les fonctions et données de la journalisation de l’inventaire logiciel sont réservées aux administrateurs et au propriétaire titulaire d’une licence du logiciel serveur.

Pour plus d’informations et de documentation sur les cmdlets de Journalisation de l’inventaire logiciel, voir [Gérer la Journalisation de l’inventaire logiciel dans Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
