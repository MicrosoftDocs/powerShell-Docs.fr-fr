---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande
description: Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande
ms.openlocfilehash: 7f1baefea69310bdf835c52461f8d3f49c4d94e8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92662002"
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
