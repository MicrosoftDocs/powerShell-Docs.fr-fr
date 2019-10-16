---
title: Comment mettre à jour les fichiers d’aide | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367138"
---
# <a name="how-to-update-help-files"></a>Guide pratique pour mettre à jour les fichiers d’aide

Cette rubrique explique comment mettre à jour les fichiers d’aide d’un module qui prend en charge l’aide actualisable.

## <a name="updating-help-files"></a>Mise à jour des fichiers d’aide

Il existe de nombreuses raisons de mettre à jour les fichiers d’aide, tels que la correction des erreurs, la clarification d’un concept, la réponse à une question fréquemment posée, l’ajout de nouveaux fichiers ou l’ajout de nouveaux et de meilleurs exemples.

Pour mettre à jour un fichier d’aide :

1. Modifiez les fichiers.

2. Traduisez les fichiers dans d’autres cultures d’interface utilisateur.

3. Collecter tous les fichiers d’aide (nouveaux, modifiés et inchangés) pour le module dans chaque culture d’interface utilisateur.

4. Validez les fichiers par rapport au schéma XML.

5. Régénérez les fichiers CAB pour chaque culture d’interface utilisateur.

6. Dans le fichier XML HelpInfo, incrémentez les numéros de version du fichier CAB pour chaque culture d’interface utilisateur.

7. Chargez les nouveaux fichiers CAB à l’emplacement spécifié par la valeur de l’élément **HelpContentUri** dans le fichier XML HelpInfo. Remplacez les anciens fichiers CAB par les nouveaux fichiers CAB.

8. Téléchargez le fichier XML HelpInfo mis à jour à l’emplacement spécifié par la clé **HelpInfoUri** dans le manifeste de module. Remplacez l’ancien fichier XML HelpInfo par le nouveau fichier.