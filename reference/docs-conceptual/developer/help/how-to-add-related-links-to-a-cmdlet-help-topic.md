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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="fbd1e-103">Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="fbd1e-103">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="fbd1e-104">Cette section décrit comment ajouter des références à d’autres contenus liés à une rubrique d’aide sur une applet de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbd1e-104">This section describes how to add references to other content that is related to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="fbd1e-105">Étant donné que ces références s’affichent dans une fenêtre de commande, elles ne sont pas directement liées au contenu référencé.</span><span class="sxs-lookup"><span data-stu-id="fbd1e-105">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="fbd1e-106">Dans les rubriques d’aide sur les applets de commande incluses dans PowerShell, ces liens font référence à d’autres applets de commande, contenu conceptuel ( `about_` ), ainsi qu’à d’autres documents et fichiers d’aide qui ne sont pas associés à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbd1e-106">In the cmdlet Help topics that are included in PowerShell, these links reference other cmdlets, conceptual content (`about_`), and other documents and Help files that are not related to PowerShell.</span></span>

<span data-ttu-id="fbd1e-107">Le code XML suivant montre comment ajouter un nœud **relatedlinks** qui contient deux références à des rubriques connexes.</span><span class="sxs-lookup"><span data-stu-id="fbd1e-107">The following XML shows how to add a **RelatedLinks** node that contains two references to related topics.</span></span>

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
