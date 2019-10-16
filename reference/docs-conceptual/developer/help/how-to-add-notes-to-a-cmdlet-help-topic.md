---
title: Guide pratique pour ajouter des notes à une rubrique d’aide sur une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361268"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="7aa97-102">Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="7aa97-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7aa97-103">Cette section décrit comment ajouter une section Remarques à une rubrique d’aide de l’applet de commande® Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7aa97-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="7aa97-104">La section Remarques est utilisée pour expliquer des détails qui ne tiennent pas facilement dans les autres sections structurées, par exemple une explication plus détaillée d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="7aa97-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="7aa97-105">Ce contenu peut inclure des commentaires sur le fonctionnement de l’applet de commande avec un fournisseur spécifique, des utilisations uniques, mais importantes, de l’applet de commande ou des moyens d’éviter des conditions d’erreur possibles.</span><span class="sxs-lookup"><span data-stu-id="7aa97-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="7aa97-106">Il n’existe aucune limite quant au nombre de notes que vous pouvez ajouter à une section Remarques.</span><span class="sxs-lookup"><span data-stu-id="7aa97-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="7aa97-107">Pour chaque note, ajoutez une paire de balises de \<maml : Alert > au nœud \<maml : alertSet >.</span><span class="sxs-lookup"><span data-stu-id="7aa97-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="7aa97-108">Le contenu de chaque note est ajouté au sein d’un ensemble de balises \<maml : para >.</span><span class="sxs-lookup"><span data-stu-id="7aa97-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="7aa97-109">Utilisez Blank \<maml : para > balises pour l’espacement.</span><span class="sxs-lookup"><span data-stu-id="7aa97-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="7aa97-110">Le code XML suivant montre un nœud \<maml : alertSet > avec deux notes.</span><span class="sxs-lookup"><span data-stu-id="7aa97-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="7aa97-111">Notez que chaque note a une balise facultative \<maml : title > (les titres peuvent être utilisés pour regrouper n’importe quel ensemble de balises de \<maml : Alert >), et que chaque note contient une ligne vide suivant le contenu pour l’espacement.</span><span class="sxs-lookup"><span data-stu-id="7aa97-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



