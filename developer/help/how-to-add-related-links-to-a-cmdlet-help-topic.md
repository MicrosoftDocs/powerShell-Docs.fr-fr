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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="67b97-102">Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="67b97-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="67b97-103">Cette section décrit comment ajouter des références vers d’autres contenus qui est associé à une rubrique d’aide Windows PowerShell® applet de commande.</span><span class="sxs-lookup"><span data-stu-id="67b97-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="67b97-104">Ces références s’affichent dans une fenêtre de commande, c’est pourquoi ils ne pas lient directement au contenu référencé.</span><span class="sxs-lookup"><span data-stu-id="67b97-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="67b97-105">Dans les rubriques d’aide applet de commande qui sont inclus dans Windows PowerShell®, ces liens référencent les autres applets de commande, le contenu conceptuel (« about_ ») et autres documents et les fichiers d’aide qui ne sont pas liées à Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="67b97-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="67b97-106">Le code XML suivant montre comment ajouter un nœud RelatedLinks qui contient deux références vers des rubriques connexes.</span><span class="sxs-lookup"><span data-stu-id="67b97-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



