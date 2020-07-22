---
title: Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande
ms.date: 09/12/2016
ms.openlocfilehash: d3679126ea34d7e86bcda700d0d050d8312a7aa2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893405"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="4a2d2-102">Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="4a2d2-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="4a2d2-103">Cette section décrit comment ajouter une section **Remarques** à une rubrique d’aide sur une applet de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a2d2-103">This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="4a2d2-104">La section **Remarques** est utilisée pour expliquer des détails qui ne tiennent pas facilement dans les autres sections structurées, par exemple une explication plus détaillée d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="4a2d2-104">The **NOTES** section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="4a2d2-105">Ce contenu peut inclure des commentaires sur le fonctionnement de l’applet de commande avec un fournisseur spécifique, des utilisations uniques, mais importantes, de l’applet de commande ou des moyens d’éviter des conditions d’erreur possibles.</span><span class="sxs-lookup"><span data-stu-id="4a2d2-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="4a2d2-106">Il n’existe aucune limite quant au nombre de notes que vous pouvez ajouter à une section Remarques.</span><span class="sxs-lookup"><span data-stu-id="4a2d2-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="4a2d2-107">Pour chaque note, ajoutez une paire de `<maml:alert>` balises au `<maml:alertset>` nœud.</span><span class="sxs-lookup"><span data-stu-id="4a2d2-107">For each note, add a pair of `<maml:alert>` tags to the `<maml:alertset>` node.</span></span> <span data-ttu-id="4a2d2-108">Le contenu de chaque note est ajouté dans un ensemble de `<maml:para>` balises.</span><span class="sxs-lookup"><span data-stu-id="4a2d2-108">The content of each note is added within a set of `<maml:para>` tags.</span></span> <span data-ttu-id="4a2d2-109">Utilisez `<maml:para>` des balises vides pour l’espacement.</span><span class="sxs-lookup"><span data-stu-id="4a2d2-109">Use blank `<maml:para>` tags for spacing.</span></span>

<span data-ttu-id="4a2d2-110">Le code XML suivant montre un `<maml:alertset>` nœud avec deux notes.</span><span class="sxs-lookup"><span data-stu-id="4a2d2-110">The following XML shows an `<maml:alertset>` node with two notes.</span></span> <span data-ttu-id="4a2d2-111">Notez que chaque note a une `<maml:title>` balise facultative (les titres peuvent être utilisés pour regrouper n’importe quel ensemble de `<maml:alert>` balises), et que chaque note contient une ligne vide qui suit le contenu pour l’espacement.</span><span class="sxs-lookup"><span data-stu-id="4a2d2-111">Notice that each note has an optional `<maml:title>` tag (titles can be used to group any set of `<maml:alert>` tags), and that each note has a blank line following the content for spacing.</span></span>

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
