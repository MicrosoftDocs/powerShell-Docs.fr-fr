---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour tester l’aide actualisable
description: Guide pratique pour tester l’aide actualisable
ms.openlocfilehash: 47873089bfa1b918ea9970915e829a22aa7254c5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667621"
---
# <a name="how-to-test-updatable-help"></a>Guide pratique pour tester l’aide actualisable

Cette rubrique décrit les approches de test de l’aide actualisable pour un module.

## <a name="using-verbose-to-detect-errors"></a>Utilisation de verbose pour détecter les erreurs

Après avoir chargé le fichier XML HelpInfo et les fichiers CAB de votre module, testez les fichiers en exécutant une commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) avec le paramètre **Verbose** . Le paramètre **Verbose** indique `Update-Help` à de signaler les étapes critiques dans ses actions, de la lecture de la clé **HelpInfoUri** dans le manifeste de module à la validation des types de fichiers dans le fichier CAB décompressé et de la mise en place des fichiers dans le répertoire de module spécifique à la langue.

Lorsque tous les messages détaillés sont résolus, exécutez une `Update-Help` commande avec le paramètre **Debug** .
Ce paramètre doit détecter les problèmes restants avec les fichiers d’aide pouvant être mis à jour.
