---
title: Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande
ms.date: 09/12/2016
ms.openlocfilehash: 7557b3856d8470434070dd286cd7e30c9ba015c5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893371"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter des références à d’autres contenus liés à une rubrique d’aide sur une applet de commande PowerShell. Étant donné que ces références s’affichent dans une fenêtre de commande, elles ne sont pas directement liées au contenu référencé.

Dans les rubriques d’aide sur les applets de commande incluses dans PowerShell, ces liens font référence à d’autres applets de commande, contenu conceptuel ( `about_` ), ainsi qu’à d’autres documents et fichiers d’aide qui ne sont pas associés à PowerShell.

Le code XML suivant montre comment ajouter un nœud **relatedlinks** qui contient deux références à des rubriques connexes.

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```
