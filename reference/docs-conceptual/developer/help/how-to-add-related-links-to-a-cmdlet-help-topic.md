---
title: Comment ajouter des liens connexes à une rubrique d’aide sur une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: 0a6403e2dea16d73e2fdcb8cf5df39b2aa5b5dae
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560268"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="1dec4-102">Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="1dec4-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="1dec4-103">Cette section décrit comment ajouter des références à d’autres contenus liés à une rubrique d’aide de l’applet de commande® Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1dec4-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="1dec4-104">Étant donné que ces références s’affichent dans une fenêtre de commande, elles ne sont pas directement liées au contenu référencé.</span><span class="sxs-lookup"><span data-stu-id="1dec4-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="1dec4-105">Dans les rubriques d’aide sur les applets de commande incluses dans Windows PowerShell®, ces liens font référence à d’autres applets de commande, à un contenu conceptuel (« about_ »), ainsi qu’à d’autres documents et fichiers d’aide qui ne sont pas associés à des® Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1dec4-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="1dec4-106">Le code XML suivant montre comment ajouter un nœud RelatedLinks qui contient deux références à des rubriques connexes.</span><span class="sxs-lookup"><span data-stu-id="1dec4-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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
