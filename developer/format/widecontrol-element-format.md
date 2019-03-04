---
title: Élément WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859825"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="d1196-102">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="d1196-102">WideControl Element (Format)</span></span>

<span data-ttu-id="d1196-103">Définit un (valeur unique) à l’échelle du format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d1196-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="d1196-104">Cette vue affiche une valeur de propriété unique ou une valeur de script pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="d1196-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="d1196-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) WideControl élément (Format)</span><span class="sxs-lookup"><span data-stu-id="d1196-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d1196-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1196-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d1196-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d1196-107">Attributes and Elements</span></span>

<span data-ttu-id="d1196-108">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `WideControl` élément.</span><span class="sxs-lookup"><span data-stu-id="d1196-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="d1196-109">Vous ne pouvez pas spécifier le `AutoSize` et `ColumnNumber` éléments en même temps.</span><span class="sxs-lookup"><span data-stu-id="d1196-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="d1196-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d1196-110">Attributes</span></span>

<span data-ttu-id="d1196-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d1196-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d1196-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d1196-112">Child Elements</span></span>

|<span data-ttu-id="d1196-113">Élément</span><span class="sxs-lookup"><span data-stu-id="d1196-113">Element</span></span>|<span data-ttu-id="d1196-114">Description</span><span class="sxs-lookup"><span data-stu-id="d1196-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d1196-115">Élément AutoSize pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d1196-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="d1196-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1196-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d1196-117">Spécifie si la taille de colonne et le nombre de colonnes sont ajustées en fonction de la taille des données.</span><span class="sxs-lookup"><span data-stu-id="d1196-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="d1196-118">Élément ColumnNumber pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d1196-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="d1196-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1196-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d1196-120">Spécifie le nombre de colonnes affichées dans l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="d1196-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="d1196-121">Élément WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="d1196-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="d1196-122">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="d1196-122">Required element.</span></span><br /><br /> <span data-ttu-id="d1196-123">Fournit les définitions de l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="d1196-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d1196-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d1196-124">Parent Elements</span></span>

|<span data-ttu-id="d1196-125">Élément</span><span class="sxs-lookup"><span data-stu-id="d1196-125">Element</span></span>|<span data-ttu-id="d1196-126">Description</span><span class="sxs-lookup"><span data-stu-id="d1196-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d1196-127">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="d1196-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d1196-128">Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="d1196-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d1196-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="d1196-129">Remarks</span></span>

<span data-ttu-id="d1196-130">Lorsque vous définissez un affichage plus large, vous pouvez ajouter la `AutoSize` élément ou le `ColumnNumber` , mais vous ne pouvez pas ajouter à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1196-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="d1196-131">Dans la plupart des cas, qu’une seule définition est requise pour chaque affichage plus large, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher les différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="d1196-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="d1196-132">Dans ce cas, vous pouvez fournir une définition séparée pour chaque objet ou un ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="d1196-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="d1196-133">Pour plus d’informations sur les composants d’un affichage plus large, consultez [les composants de vue large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d1196-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d1196-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1196-134">Example</span></span>

<span data-ttu-id="d1196-135">L’exemple suivant montre un `WideControl` élément qui est utilisé pour afficher une propriété de la [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.</span><span class="sxs-lookup"><span data-stu-id="d1196-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="d1196-136">Pour obtenir un exemple complet d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d1196-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1196-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1196-137">See Also</span></span>

[<span data-ttu-id="d1196-138">Élément AutoSize pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d1196-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="d1196-139">Élément ColumnNumber pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d1196-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="d1196-140">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="d1196-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d1196-141">Élément WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="d1196-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="d1196-142">Affichage plus large (Basic)</span><span class="sxs-lookup"><span data-stu-id="d1196-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="d1196-143">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="d1196-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d1196-144">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1196-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
