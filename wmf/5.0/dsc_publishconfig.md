---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225672"
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="2adbc-102">Remettre un document de configuration sans l’appliquer</span><span class="sxs-lookup"><span data-stu-id="2adbc-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="2adbc-103">L’applet de commande [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copie un fichier MOF de configuration sur un nœud cible, mais n’applique pas la configuration.</span><span class="sxs-lookup"><span data-stu-id="2adbc-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="2adbc-104">Cette configuration est appliquée durant le contrôle de cohérence suivant, ou quand vous exécutez l’applet de commande [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).</span><span class="sxs-lookup"><span data-stu-id="2adbc-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>
