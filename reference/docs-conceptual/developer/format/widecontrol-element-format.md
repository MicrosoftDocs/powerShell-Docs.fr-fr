---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl, élément (Format)
description: WideControl, élément (Format)
ms.openlocfilehash: f88e1ce18f87e5e47de473298b3ecf070b71c192
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651272"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="75ec4-103">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="75ec4-103">WideControl Element (Format)</span></span>

<span data-ttu-id="75ec4-104">Définit un format de liste larges (à valeur unique) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="75ec4-104">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="75ec4-105">Cette vue affiche une valeur de propriété ou une valeur de script unique pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="75ec4-105">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="75ec4-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) WideControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="75ec4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75ec4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75ec4-107">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75ec4-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="75ec4-108">Attributes and Elements</span></span>

<span data-ttu-id="75ec4-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideControl` élément.</span><span class="sxs-lookup"><span data-stu-id="75ec4-109">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="75ec4-110">Vous ne pouvez pas spécifier les `AutoSize` `ColumnNumber` éléments et en même temps.</span><span class="sxs-lookup"><span data-stu-id="75ec4-110">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="75ec4-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="75ec4-111">Attributes</span></span>

<span data-ttu-id="75ec4-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="75ec4-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75ec4-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="75ec4-113">Child Elements</span></span>

|<span data-ttu-id="75ec4-114">Élément</span><span class="sxs-lookup"><span data-stu-id="75ec4-114">Element</span></span>|<span data-ttu-id="75ec4-115">Description</span><span class="sxs-lookup"><span data-stu-id="75ec4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75ec4-116">AutoSize, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="75ec4-116">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="75ec4-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="75ec4-117">Optional element.</span></span><br /><br /> <span data-ttu-id="75ec4-118">Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.</span><span class="sxs-lookup"><span data-stu-id="75ec4-118">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="75ec4-119">ColumnNumber, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="75ec4-119">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="75ec4-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="75ec4-120">Optional element.</span></span><br /><br /> <span data-ttu-id="75ec4-121">Spécifie le nombre de colonnes affichées dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="75ec4-121">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="75ec4-122">Élément WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="75ec4-122">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="75ec4-123">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="75ec4-123">Required element.</span></span><br /><br /> <span data-ttu-id="75ec4-124">Fournit les définitions de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="75ec4-124">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="75ec4-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="75ec4-125">Parent Elements</span></span>

|<span data-ttu-id="75ec4-126">Élément</span><span class="sxs-lookup"><span data-stu-id="75ec4-126">Element</span></span>|<span data-ttu-id="75ec4-127">Description</span><span class="sxs-lookup"><span data-stu-id="75ec4-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75ec4-128">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="75ec4-128">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="75ec4-129">Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="75ec4-129">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="75ec4-130">Notes</span><span class="sxs-lookup"><span data-stu-id="75ec4-130">Remarks</span></span>

<span data-ttu-id="75ec4-131">Lorsque vous définissez une vue étendue, vous pouvez ajouter l' `AutoSize` élément ou le, `ColumnNumber` mais vous ne pouvez pas ajouter les deux.</span><span class="sxs-lookup"><span data-stu-id="75ec4-131">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="75ec4-132">Dans la plupart des cas, une seule définition est requise pour chaque vue étendue, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="75ec4-132">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="75ec4-133">Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="75ec4-133">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="75ec4-134">Pour plus d’informations sur les composants d’une vue étendue, consultez [composants de vue larges](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="75ec4-134">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="75ec4-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="75ec4-135">Example</span></span>

<span data-ttu-id="75ec4-136">L’exemple suivant montre un `WideControl` élément utilisé pour afficher une propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="75ec4-136">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="75ec4-137">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="75ec4-137">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75ec4-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75ec4-138">See Also</span></span>

[<span data-ttu-id="75ec4-139">AutoSize, élément de WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="75ec4-139">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="75ec4-140">ColumnNumber, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="75ec4-140">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="75ec4-141">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="75ec4-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="75ec4-142">Élément WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="75ec4-142">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="75ec4-143">Vue large (De base)</span><span class="sxs-lookup"><span data-stu-id="75ec4-143">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="75ec4-144">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="75ec4-144">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="75ec4-145">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="75ec4-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
