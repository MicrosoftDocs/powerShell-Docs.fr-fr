---
ms.date: 10/20/2020
ms.topic: reference
title: Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande
description: Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande
ms.openlocfilehash: 61363c26ab0172277d1332ed1e9de080d8da200c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659559"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="676ca-103">Guide pratique pour ajouter des remarques à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="676ca-103">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="676ca-104">Cette section explique comment ajouter une section **NOTES** à la rubrique d’aide d’une cmdlet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="676ca-104">This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="676ca-105">La section **NOTES** permet de donner des détails qui entrent difficilement dans les autres sections structurées, par exemple une explication plus détaillée d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="676ca-105">The **NOTES** section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="676ca-106">Ce contenu peut comporter des commentaires sur le fonctionnement de la cmdlet avec un fournisseur spécifique, des utilisations uniques mais importantes de la cmdlet ou encore des moyens d’éviter des situations d’erreur potentielles.</span><span class="sxs-lookup"><span data-stu-id="676ca-106">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="676ca-107">La section **NOTES** est définie à l’aide d’un seul nœud `<maml:alertset>`.</span><span class="sxs-lookup"><span data-stu-id="676ca-107">The **NOTES** section is defined using a single `<maml:alertset>` node.</span></span> <span data-ttu-id="676ca-108">Le nombre de notes que l’on peut ajouter à une section NOTES n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="676ca-108">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="676ca-109">Pour chaque note, ajoutez une paire de balises `<maml:alert>` au nœud `<maml:alertset>`.</span><span class="sxs-lookup"><span data-stu-id="676ca-109">For each note, add a pair of `<maml:alert>` tags to the `<maml:alertset>` node.</span></span> <span data-ttu-id="676ca-110">Le contenu de chaque note est ajouté au sein d’un ensemble de balises `<maml:para>`.</span><span class="sxs-lookup"><span data-stu-id="676ca-110">The content of each note is added within a set of `<maml:para>` tags.</span></span> <span data-ttu-id="676ca-111">Utilisez des balises `<maml:para>` vides pour l’espacement.</span><span class="sxs-lookup"><span data-stu-id="676ca-111">Use blank `<maml:para>` tags for spacing.</span></span>

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
