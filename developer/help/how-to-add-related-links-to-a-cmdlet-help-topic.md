---
title: Comment ajouter des liens connexes à une rubrique d’aide applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855395"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter des références vers d’autres contenus qui est associé à une rubrique d’aide Windows PowerShell® applet de commande. Ces références s’affichent dans une fenêtre de commande, c’est pourquoi ils ne pas lient directement au contenu référencé.

Dans les rubriques d’aide applet de commande qui sont inclus dans Windows PowerShell®, ces liens référencent les autres applets de commande, le contenu conceptuel (« about_ ») et autres documents et les fichiers d’aide qui ne sont pas liées à Windows PowerShell®.

Le code XML suivant montre comment ajouter un nœud RelatedLinks qui contient deux références vers des rubriques connexes.

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



