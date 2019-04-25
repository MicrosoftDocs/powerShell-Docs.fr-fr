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
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="c5d78-102">Remettre un document de configuration sans l’appliquer</span><span class="sxs-lookup"><span data-stu-id="c5d78-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="c5d78-103">L’applet de commande [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copie un fichier MOF de configuration sur un nœud cible, mais n’applique pas la configuration.</span><span class="sxs-lookup"><span data-stu-id="c5d78-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="c5d78-104">Cette configuration est appliquée durant le contrôle de cohérence suivant, ou quand vous exécutez l’applet de commande [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).</span><span class="sxs-lookup"><span data-stu-id="c5d78-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>
