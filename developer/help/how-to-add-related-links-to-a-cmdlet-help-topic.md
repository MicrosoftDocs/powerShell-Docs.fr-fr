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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083336"
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



