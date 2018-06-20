---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225587"
---
# <a name="new-guid"></a>New-Guid
Bien souvent, lors de l’écriture de scripts (ou même d’une ressource DSC), vous devez utiliser un identificateur unique. Les GUID fonctionnent correctement, et il est facile d’appeler la classe Guid du .NET Framework pour en générer un, mais le fait de disposer d’une applet de commande rend cela plus simple à découvrir pour les utilisateurs qui ne se sont pas encore familiarisés avec la classe .NET Framework :

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
