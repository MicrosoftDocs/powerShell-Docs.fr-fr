---
title: Guide pratique pour tester l’aide actualisable
ms.date: 09/12/2016
ms.openlocfilehash: 0602349f853fddd0cadae545eaf0302c150e3a28
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892963"
---
# <a name="how-to-test-updatable-help"></a>Guide pratique pour tester l’aide actualisable

Cette rubrique décrit les approches de test de l’aide actualisable pour un module.

## <a name="using-verbose-to-detect-errors"></a>Utilisation de verbose pour détecter les erreurs

Après avoir chargé le fichier XML HelpInfo et les fichiers CAB de votre module, testez les fichiers en exécutant une commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) avec le paramètre **Verbose** . Le paramètre **Verbose** indique `Update-Help` à de signaler les étapes critiques dans ses actions, de la lecture de la clé **HelpInfoUri** dans le manifeste de module à la validation des types de fichiers dans le fichier CAB décompressé et de la mise en place des fichiers dans le répertoire de module spécifique à la langue.

Lorsque tous les messages détaillés sont résolus, exécutez une `Update-Help` commande avec le paramètre **Debug** .
Ce paramètre doit détecter les problèmes restants avec les fichiers d’aide pouvant être mis à jour.
