---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 4a2dfd651f1c74e7441e5f5e357c1c26453adc07
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="software-inventory-logging-sil"></a>Journalisation de l’inventaire logiciel

**IMPORTANT : ** *Lors de l’installation de WMF 5.0 sur un serveur Windows Server 2012 R2 exécutant déjà la journalisation de l’inventaire logiciel, vous devez exécuter l’applet de commande Start-SilLogging une seule fois après l’installation de WMF, car le processus d’installation arrête la fonctionnalité de journalisation de l’inventaire logiciel de façon non contrôlée.*

La journalisation de l’inventaire logiciel aide à réduire les coûts d’exploitation liés à l’obtention d’informations précises concernant les logiciels Microsoft installés localement sur un serveur, mais plus particulièrement sur de nombreux serveurs d’un environnement informatique (en supposant que les logiciels soient installés et en cours d’exécution dans l’environnement informatique). Vous pouvez alors transférer ces données à un serveur d’agrégation et recueillir les données des journaux dans un emplacement centralisé à l’aide d’un processus uniforme et automatique.

Même si vous pouvez aussi journaliser les données d’inventaire logiciel en interrogeant directement chaque ordinateur, la journalisation de l’inventaire logiciel, en utilisant une architecture de transmission (par le biais le réseau) mise en œuvre par chaque serveur, permet de relever les défis liés à la découverte des serveurs, défis typiques de nombreux scénarios de gestion des actifs et d’inventaire logiciel. La journalisation de l’inventaire logiciel utilise le protocole SSL pour sécuriser les données qui sont transférées à un serveur d’agrégation par le biais du protocole HTTPS. Le stockage des données dans un emplacement centralisé facilite l’analyse, la manipulation et le partage des données en cas de besoin.

Aucune de ces données n’est envoyée à Microsoft dans le cadre du fonctionnement de la fonctionnalité. Les fonctions et données de la journalisation de l’inventaire logiciel sont réservées aux administrateurs et au propriétaire titulaire d’une licence du logiciel serveur.

Pour plus d’informations et pour obtenir de la documentation sur les applets de commande de journalisation de l’inventaire logiciel, consultez les ressources en ligne de Windows Server 2012 R2 à l’adresse <http://technet.microsoft.com/library/dn383584.aspx>.

