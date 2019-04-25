---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085811"
---
# <a name="deliver-a-configuration-document-without-applying"></a>Remettre un document de configuration sans l’appliquer

L’applet de commande [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copie un fichier MOF de configuration sur un nœud cible, mais n’applique pas la configuration.
Cette configuration est appliquée durant le contrôle de cohérence suivant, ou quand vous exécutez l’applet de commande [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).
