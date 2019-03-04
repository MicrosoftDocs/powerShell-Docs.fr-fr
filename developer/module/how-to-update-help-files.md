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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855525"
---
# <a name="how-to-update-help-files"></a>Guide pratique pour mettre à jour les fichiers d’aide

Cette rubrique explique comment mettre à jour les fichiers d’aide pour un module qui prend en charge de l’aide actualisable.

## <a name="updating-help-files"></a>La mise à jour des fichiers d’aide

Il existe de nombreuses raisons pour mettre à jour les fichiers d’aide, telles que la correction des erreurs, clarifier un concept, répondre à une question fréquemment posées, ajout de nouveaux fichiers ou ajout d’exemples de nouvelles et meilleures.

Pour mettre à jour un fichier d’aide :

1. Modifier les fichiers.

2. Traduire les fichiers dans les autres cultures d’interface utilisateur.

3. Collecter tous les fichiers d’aide (nouvelles, modifiées et inchangées) pour le module dans chaque culture d’interface utilisateur.

4. Validez les fichiers par rapport au schéma XML.

5. Reconstruire les fichiers CAB pour chaque culture d’interface utilisateur.

6. Dans le fichier XML HelpInfo, incrémenter les numéros de version du fichier CAB pour chaque culture d’interface utilisateur.

7. Télécharger les nouveaux fichiers CAB à l’emplacement spécifié par la valeur de la **HelpContentUri** élément dans le fichier XML HelpInfo. Remplacez les anciens fichiers CAB avec les nouveaux fichiers CAB.

8. Télécharger le fichier XML HelpInfo mis à jour à l’emplacement spécifié par le **HelpInfoUri** clés dans le manifeste de module. Remplacez l’ancien fichier XML HelpInfo avec le nouveau fichier.