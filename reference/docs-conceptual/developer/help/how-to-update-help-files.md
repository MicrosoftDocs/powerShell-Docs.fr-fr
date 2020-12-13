---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour mettre à jour les fichiers d’aide
description: Guide pratique pour mettre à jour les fichiers d’aide
ms.openlocfilehash: 19bf501cf91b1eb5dabb334c2179953590b40232
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649594"
---
# <a name="how-to-update-help-files"></a>Guide pratique pour mettre à jour les fichiers d’aide

Cette rubrique explique comment mettre à jour les fichiers d’aide d’un module qui prend en charge l’aide actualisable.

## <a name="updating-help-files"></a>Mise à jour des fichiers d’aide

Il existe de nombreuses raisons de mettre à jour les fichiers d’aide, tels que la correction des erreurs, la clarification d’un concept, la réponse à une question fréquemment posée, l’ajout de nouveaux fichiers ou l’ajout de nouveaux et de meilleurs exemples.

Pour mettre à jour un fichier d’aide :

1. Modifiez les fichiers.
1. Traduisez les fichiers dans d’autres cultures d’interface utilisateur.
1. Collecter tous les fichiers d’aide (nouveaux, modifiés et inchangés) pour le module dans chaque culture d’interface utilisateur.
1. Validez les fichiers par rapport au schéma XML.
1. Régénérez les fichiers CAB pour chaque culture d’interface utilisateur.
1. Dans le fichier XML HelpInfo, incrémentez les numéros de version du fichier CAB pour chaque culture d’interface utilisateur.
1. Chargez les nouveaux fichiers CAB à l’emplacement spécifié par la valeur de l’élément **HelpContentUri** dans le fichier XML HelpInfo. Remplacez les anciens fichiers CAB par les nouveaux fichiers CAB.
1. Téléchargez le fichier XML HelpInfo mis à jour à l’emplacement spécifié par la clé **HelpInfoUri** dans le manifeste de module. Remplacez l’ancien fichier XML HelpInfo par le nouveau fichier.
