---
ms.date: 09/13/2016
ms.topic: reference
title: WideItem, élément pour WideControl (Format)
description: WideItem, élément pour WideControl (Format)
ms.openlocfilehash: b9c416bbe3befcd689b8a2c0b72a8ff1301b9659
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647809"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="e0eab-103">WideItem, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e0eab-103">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="e0eab-104">Définit la propriété ou le script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="e0eab-104">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="e0eab-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry, élément (format) WideItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="e0eab-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0eab-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0eab-106">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0eab-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e0eab-107">Attributes and Elements</span></span>

<span data-ttu-id="e0eab-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideItem` élément.</span><span class="sxs-lookup"><span data-stu-id="e0eab-108">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="e0eab-109">L’élément `FormatString` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e0eab-109">The `FormatString` element is optional.</span></span> <span data-ttu-id="e0eab-110">Toutefois, vous devez spécifier un `PropertyName` `ScriptBlock` élément ou, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="e0eab-110">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0eab-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e0eab-111">Attributes</span></span>

<span data-ttu-id="e0eab-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e0eab-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0eab-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e0eab-113">Child Elements</span></span>

|<span data-ttu-id="e0eab-114">Élément</span><span class="sxs-lookup"><span data-stu-id="e0eab-114">Element</span></span>|<span data-ttu-id="e0eab-115">Description</span><span class="sxs-lookup"><span data-stu-id="e0eab-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0eab-116">FormatString, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e0eab-116">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e0eab-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e0eab-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e0eab-118">Spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="e0eab-118">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="e0eab-119">PropertyName, élément de WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="e0eab-119">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e0eab-120">Spécifie la propriété de l’objet dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="e0eab-120">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="e0eab-121">Élément ScriptBlock pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="e0eab-121">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e0eab-122">Spécifie le script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="e0eab-122">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0eab-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e0eab-123">Parent Elements</span></span>

|<span data-ttu-id="e0eab-124">Élément</span><span class="sxs-lookup"><span data-stu-id="e0eab-124">Element</span></span>|<span data-ttu-id="e0eab-125">Description</span><span class="sxs-lookup"><span data-stu-id="e0eab-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0eab-126">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e0eab-126">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="e0eab-127">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="e0eab-127">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0eab-128">Notes</span><span class="sxs-lookup"><span data-stu-id="e0eab-128">Remarks</span></span>

<span data-ttu-id="e0eab-129">Pour plus d’informations sur les composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e0eab-129">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e0eab-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="e0eab-130">Example</span></span>

<span data-ttu-id="e0eab-131">L’exemple suivant montre un `WideEntry` élément qui définit un `WideItem` élément unique.</span><span class="sxs-lookup"><span data-stu-id="e0eab-131">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="e0eab-132">L' `WideItem` élément définit la propriété ou le script dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="e0eab-132">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="e0eab-133">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="e0eab-133">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0eab-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0eab-134">See Also</span></span>

[<span data-ttu-id="e0eab-135">FormatString, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e0eab-135">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e0eab-136">PropertyName, élément de WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="e0eab-136">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e0eab-137">Élément ScriptBlock pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="e0eab-137">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e0eab-138">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e0eab-138">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="e0eab-139">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0eab-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
