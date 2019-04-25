---
title: L’étiquette d’élément pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065408"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="307b0-102">Label, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="307b0-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="307b0-103">Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.</span><span class="sxs-lookup"><span data-stu-id="307b0-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="307b0-104">Configuration élément (Format) ViewDefinitions, élément (Format) (Format) d’élément GroupBy élément d’affichage pour l’élément Label de vue (Format) pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="307b0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="307b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="307b0-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="307b0-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="307b0-106">Attributes and Elements</span></span>

<span data-ttu-id="307b0-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `Label` élément.</span><span class="sxs-lookup"><span data-stu-id="307b0-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="307b0-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="307b0-108">Attributes</span></span>

<span data-ttu-id="307b0-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="307b0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="307b0-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="307b0-110">Child Elements</span></span>

<span data-ttu-id="307b0-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="307b0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="307b0-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="307b0-112">Parent Elements</span></span>

|<span data-ttu-id="307b0-113">Élément</span><span class="sxs-lookup"><span data-stu-id="307b0-113">Element</span></span>|<span data-ttu-id="307b0-114">Description</span><span class="sxs-lookup"><span data-stu-id="307b0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="307b0-115">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="307b0-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="307b0-116">Définit comment un nouveau groupe d’objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="307b0-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="307b0-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="307b0-117">Text Value</span></span>

<span data-ttu-id="307b0-118">Spécifiez le texte qui s’affiche chaque fois que Windows PowerShell rencontre une nouvelle propriété ou la valeur de script.</span><span class="sxs-lookup"><span data-stu-id="307b0-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="307b0-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="307b0-119">Remarks</span></span>

<span data-ttu-id="307b0-120">En plus du texte spécifié par cet élément, Windows PowerShell affiche la nouvelle valeur qui démarre le groupe et ajoute une ligne vide avant et après le groupe.</span><span class="sxs-lookup"><span data-stu-id="307b0-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="307b0-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="307b0-121">Example</span></span>

<span data-ttu-id="307b0-122">L’exemple suivant montre l’étiquette pour un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="307b0-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="307b0-123">L’étiquette affichée ressemblerait à ceci : `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="307b0-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="307b0-124">Pour obtenir un exemple d’un fichier de mise en forme complète qui inclut cet élément, consultez [affichage plus large (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="307b0-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="307b0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="307b0-125">See Also</span></span>

[<span data-ttu-id="307b0-126">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="307b0-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="307b0-127">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="307b0-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
