---
title: Le Test d’aide actualisable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794261"
---
# <a name="how-to-test-updatable-help"></a>Guide pratique pour tester l’aide actualisable

Cette rubrique décrit les approches de test de l’aide actualisable pour un module.

## <a name="using-verbose-to-detect-errors"></a>À l’aide détaillée pour détecter les erreurs

Après avoir téléchargé le fichier XML HelpInfo et les fichiers CAB pour votre module, les fichiers de test en exécutant un [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) commande avec le **Verbose** paramètre. Le **Verbose** paramètre dirige `Update-Help` pour signaler les étapes critiques dans ses actions, de lire le **HelpInfoUri** clés dans le manifeste de module pour valider les types de fichiers dans le fichier CAB décompressé et placer les fichiers dans le répertoire de module spécifique au langage.

Quand tous les messages documentés sont résolues, exécutez une `Update-Help` commande avec le **déboguer** paramètre. Ce paramètre doit détecter les problèmes restants avec les fichiers d’aide actualisable.