---
title: Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande
ms.date: 10/20/2020
ms.openlocfilehash: 7f8be34a82de2c12cfd2a05deed139ddb30da95f
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92298312"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="80169-102">Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="80169-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="80169-103">Cette section explique comment ajouter une section **NOTES** à la rubrique d’aide d’une cmdlet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80169-103">This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="80169-104">La section **NOTES** permet de donner des détails qui entrent difficilement dans les autres sections structurées, par exemple une explication plus détaillée d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="80169-104">The **NOTES** section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="80169-105">Ce contenu peut comporter des commentaires sur le fonctionnement de la cmdlet avec un fournisseur spécifique, des utilisations uniques mais importantes de la cmdlet ou encore des moyens d’éviter des situations d’erreur potentielles.</span><span class="sxs-lookup"><span data-stu-id="80169-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="80169-106">La section **NOTES** est définie à l’aide d’un seul nœud `<maml:alertset>`.</span><span class="sxs-lookup"><span data-stu-id="80169-106">The **NOTES** section is defined using a single `<maml:alertset>` node.</span></span> <span data-ttu-id="80169-107">Le nombre de notes que l’on peut ajouter à une section NOTES n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="80169-107">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="80169-108">Pour chaque note, ajoutez une paire de balises `<maml:alert>` au nœud `<maml:alertset>`.</span><span class="sxs-lookup"><span data-stu-id="80169-108">For each note, add a pair of `<maml:alert>` tags to the `<maml:alertset>` node.</span></span> <span data-ttu-id="80169-109">Le contenu de chaque note est ajouté au sein d’un ensemble de balises `<maml:para>`.</span><span class="sxs-lookup"><span data-stu-id="80169-109">The content of each note is added within a set of `<maml:para>` tags.</span></span> <span data-ttu-id="80169-110">Utilisez des balises `<maml:para>` vides pour l’espacement.</span><span class="sxs-lookup"><span data-stu-id="80169-110">Use blank `<maml:para>` tags for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>Optional title for Note</maml:title>
  <maml:alert>
    <maml:para>Note 1</maml:para>
    <maml:para>Note a</maml:para>
  </maml:alert>
  <maml:alert>
    <maml:para>Note 2</maml:para>
  </maml:alert>
</maml:alertSet>
```
