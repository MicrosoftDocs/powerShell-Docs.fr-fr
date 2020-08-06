---
title: Élément WideItem pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6b2f7c97978c20350caeec894589c5995ae7ccc4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779894"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="fb238-102">WideItem, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fb238-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="fb238-103">Définit la propriété ou le script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="fb238-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="fb238-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry, élément (format) WideItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="fb238-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb238-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb238-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb238-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fb238-106">Attributes and Elements</span></span>

<span data-ttu-id="fb238-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideItem` élément.</span><span class="sxs-lookup"><span data-stu-id="fb238-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="fb238-108">L’élément `FormatString` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="fb238-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="fb238-109">Toutefois, vous devez spécifier un `PropertyName` `ScriptBlock` élément ou, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="fb238-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb238-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="fb238-110">Attributes</span></span>

<span data-ttu-id="fb238-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fb238-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb238-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fb238-112">Child Elements</span></span>

|<span data-ttu-id="fb238-113">Élément</span><span class="sxs-lookup"><span data-stu-id="fb238-113">Element</span></span>|<span data-ttu-id="fb238-114">Description</span><span class="sxs-lookup"><span data-stu-id="fb238-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb238-115">FormatString, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fb238-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="fb238-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="fb238-116">Optional element.</span></span><br /><br /> <span data-ttu-id="fb238-117">Spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="fb238-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="fb238-118">PropertyName, élément de WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="fb238-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="fb238-119">Spécifie la propriété de l’objet dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="fb238-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="fb238-120">Élément ScriptBlock pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="fb238-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="fb238-121">Spécifie le script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="fb238-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fb238-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fb238-122">Parent Elements</span></span>

|<span data-ttu-id="fb238-123">Élément</span><span class="sxs-lookup"><span data-stu-id="fb238-123">Element</span></span>|<span data-ttu-id="fb238-124">Description</span><span class="sxs-lookup"><span data-stu-id="fb238-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb238-125">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fb238-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="fb238-126">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="fb238-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fb238-127">Notes</span><span class="sxs-lookup"><span data-stu-id="fb238-127">Remarks</span></span>

<span data-ttu-id="fb238-128">Pour plus d’informations sur les composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="fb238-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fb238-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="fb238-129">Example</span></span>

<span data-ttu-id="fb238-130">L’exemple suivant montre un `WideEntry` élément qui définit un `WideItem` élément unique.</span><span class="sxs-lookup"><span data-stu-id="fb238-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="fb238-131">L' `WideItem` élément définit la propriété ou le script dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="fb238-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="fb238-132">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="fb238-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb238-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb238-133">See Also</span></span>

[<span data-ttu-id="fb238-134">FormatString, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fb238-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="fb238-135">PropertyName, élément de WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="fb238-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="fb238-136">Élément ScriptBlock pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="fb238-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="fb238-137">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="fb238-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="fb238-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb238-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
