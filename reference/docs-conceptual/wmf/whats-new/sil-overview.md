---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Journalisation de l’inventaire logiciel
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147779"
---
# <a name="software-inventory-logging-sil"></a>Journalisation de l’inventaire logiciel

> [!IMPORTANT]
> Après avoir installé WMF 5.x sur un serveur Windows Server 2012 R2 sur lequel la Journalisation de l’inventaire logiciel tourne déjà, il est nécessaire d’exécuter une fois la cmdlet Start-SilLogging, car le processus d’installation arrête la fonctionnalité de Journalisation de l’inventaire logiciel de façon non contrôlée.

La journalisation de l’inventaire logiciel aide à réduire les coûts d’exploitation liés à l’obtention d’informations précises concernant les logiciels Microsoft installés localement sur un serveur, mais plus particulièrement sur de nombreux serveurs d’un environnement informatique (en supposant que les logiciels soient installés et en cours d’exécution dans l’environnement informatique). Vous pouvez alors transférer ces données à un serveur d’agrégation et recueillir les données des journaux dans un emplacement centralisé à l’aide d’un processus uniforme et automatique.

Même si vous pouvez aussi journaliser les données d’inventaire logiciel en interrogeant directement chaque ordinateur, la journalisation de l’inventaire logiciel, en utilisant une architecture de transmission (par le biais le réseau) mise en œuvre par chaque serveur, permet de relever les défis liés à la découverte des serveurs, défis typiques de nombreux scénarios de gestion des actifs et d’inventaire logiciel. La journalisation de l’inventaire logiciel utilise le protocole SSL pour sécuriser les données qui sont transférées à un serveur d’agrégation par le biais du protocole HTTPS. Le stockage des données dans un emplacement centralisé facilite l’analyse, la manipulation et le partage des données en cas de besoin.

Aucune de ces données n’est envoyée à Microsoft dans le cadre du fonctionnement de la fonctionnalité. Les fonctions et données de la journalisation de l’inventaire logiciel sont réservées aux administrateurs et au propriétaire titulaire d’une licence du logiciel serveur.

Pour plus d’informations et de documentation sur les cmdlets de Journalisation de l’inventaire logiciel, voir [Gérer la Journalisation de l’inventaire logiciel dans Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
