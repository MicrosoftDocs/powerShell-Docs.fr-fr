---
ms.date: 09/13/2016
ms.topic: reference
title: Label, élément pour GroupBy (Format)
description: Label, élément pour GroupBy (Format)
ms.openlocfilehash: ff4b0dec01bb5b472b1813540661791b91568eed
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649796"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="74df5-103">Label, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="74df5-103">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="74df5-104">Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.</span><span class="sxs-lookup"><span data-stu-id="74df5-104">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="74df5-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément label View (format) pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="74df5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74df5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74df5-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74df5-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="74df5-107">Attributes and Elements</span></span>

<span data-ttu-id="74df5-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Label` élément.</span><span class="sxs-lookup"><span data-stu-id="74df5-108">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="74df5-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="74df5-109">Attributes</span></span>

<span data-ttu-id="74df5-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="74df5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74df5-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="74df5-111">Child Elements</span></span>

<span data-ttu-id="74df5-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="74df5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="74df5-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="74df5-113">Parent Elements</span></span>

|<span data-ttu-id="74df5-114">Élément</span><span class="sxs-lookup"><span data-stu-id="74df5-114">Element</span></span>|<span data-ttu-id="74df5-115">Description</span><span class="sxs-lookup"><span data-stu-id="74df5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74df5-116">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="74df5-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="74df5-117">Définit le mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="74df5-117">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="74df5-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="74df5-118">Text Value</span></span>

<span data-ttu-id="74df5-119">Spécifiez le texte qui s’affiche chaque fois que Windows PowerShell rencontre une nouvelle propriété ou une nouvelle valeur de script.</span><span class="sxs-lookup"><span data-stu-id="74df5-119">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="74df5-120">Notes</span><span class="sxs-lookup"><span data-stu-id="74df5-120">Remarks</span></span>

<span data-ttu-id="74df5-121">En plus du texte spécifié par cet élément, Windows PowerShell affiche la nouvelle valeur qui démarre le groupe et ajoute une ligne vide avant et après le groupe.</span><span class="sxs-lookup"><span data-stu-id="74df5-121">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="74df5-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="74df5-122">Example</span></span>

<span data-ttu-id="74df5-123">L’exemple suivant montre l’étiquette d’un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="74df5-123">The following example shows the label for a new group.</span></span> <span data-ttu-id="74df5-124">L’étiquette affichée devrait ressembler à ceci : `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="74df5-124">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="74df5-125">Pour obtenir un exemple de fichier de mise en forme complet qui comprend cet élément, consultez [vue étendue (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="74df5-125">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74df5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74df5-126">See Also</span></span>

[<span data-ttu-id="74df5-127">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="74df5-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="74df5-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="74df5-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
