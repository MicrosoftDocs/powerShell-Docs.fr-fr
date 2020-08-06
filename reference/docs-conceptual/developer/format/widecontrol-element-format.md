---
title: Élément WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b6f19cf94dcb440eeaf53547db407287e5462520
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784977"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="1db76-102">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="1db76-102">WideControl Element (Format)</span></span>

<span data-ttu-id="1db76-103">Définit un format de liste larges (à valeur unique) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="1db76-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="1db76-104">Cette vue affiche une valeur de propriété ou une valeur de script unique pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="1db76-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="1db76-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) WideControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="1db76-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1db76-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1db76-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1db76-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1db76-107">Attributes and Elements</span></span>

<span data-ttu-id="1db76-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideControl` élément.</span><span class="sxs-lookup"><span data-stu-id="1db76-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="1db76-109">Vous ne pouvez pas spécifier les `AutoSize` `ColumnNumber` éléments et en même temps.</span><span class="sxs-lookup"><span data-stu-id="1db76-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="1db76-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="1db76-110">Attributes</span></span>

<span data-ttu-id="1db76-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1db76-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1db76-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1db76-112">Child Elements</span></span>

|<span data-ttu-id="1db76-113">Élément</span><span class="sxs-lookup"><span data-stu-id="1db76-113">Element</span></span>|<span data-ttu-id="1db76-114">Description</span><span class="sxs-lookup"><span data-stu-id="1db76-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1db76-115">AutoSize, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1db76-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="1db76-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1db76-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1db76-117">Spécifie si la taille de colonne et le nombre de colonnes sont ajustés en fonction de la taille des données.</span><span class="sxs-lookup"><span data-stu-id="1db76-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="1db76-118">ColumnNumber, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1db76-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="1db76-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1db76-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1db76-120">Spécifie le nombre de colonnes affichées dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="1db76-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="1db76-121">Élément WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="1db76-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="1db76-122">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="1db76-122">Required element.</span></span><br /><br /> <span data-ttu-id="1db76-123">Fournit les définitions de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="1db76-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1db76-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1db76-124">Parent Elements</span></span>

|<span data-ttu-id="1db76-125">Élément</span><span class="sxs-lookup"><span data-stu-id="1db76-125">Element</span></span>|<span data-ttu-id="1db76-126">Description</span><span class="sxs-lookup"><span data-stu-id="1db76-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1db76-127">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="1db76-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="1db76-128">Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="1db76-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1db76-129">Notes</span><span class="sxs-lookup"><span data-stu-id="1db76-129">Remarks</span></span>

<span data-ttu-id="1db76-130">Lorsque vous définissez une vue étendue, vous pouvez ajouter l' `AutoSize` élément ou le, `ColumnNumber` mais vous ne pouvez pas ajouter les deux.</span><span class="sxs-lookup"><span data-stu-id="1db76-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="1db76-131">Dans la plupart des cas, une seule définition est requise pour chaque vue étendue, mais il est possible d’avoir plusieurs définitions si vous souhaitez utiliser la même vue pour afficher différents objets .NET.</span><span class="sxs-lookup"><span data-stu-id="1db76-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="1db76-132">Dans ce cas, vous pouvez fournir une définition distincte pour chaque objet ou ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="1db76-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="1db76-133">Pour plus d’informations sur les composants d’une vue étendue, consultez [composants de vue larges](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1db76-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1db76-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="1db76-134">Example</span></span>

<span data-ttu-id="1db76-135">L’exemple suivant montre un `WideControl` élément utilisé pour afficher une propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="1db76-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="1db76-136">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="1db76-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1db76-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1db76-137">See Also</span></span>

[<span data-ttu-id="1db76-138">AutoSize, élément de WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="1db76-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="1db76-139">ColumnNumber, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1db76-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="1db76-140">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="1db76-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="1db76-141">Élément WideEntries (format)</span><span class="sxs-lookup"><span data-stu-id="1db76-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="1db76-142">Vue large (De base)</span><span class="sxs-lookup"><span data-stu-id="1db76-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="1db76-143">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="1db76-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1db76-144">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1db76-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
