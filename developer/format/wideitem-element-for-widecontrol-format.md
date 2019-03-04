---
title: Élément WideItem pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862625"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="4d3c1-102">WideItem, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4d3c1-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="4d3c1-103">Définit la propriété ou un script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="4d3c1-104">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) WideItem élément (Format)</span><span class="sxs-lookup"><span data-stu-id="4d3c1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4d3c1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d3c1-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4d3c1-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="4d3c1-106">Attributes and Elements</span></span>

<span data-ttu-id="4d3c1-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `WideItem` élément.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="4d3c1-108">L'élément `FormatString` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="4d3c1-109">Toutefois, vous devez spécifier un `PropertyName` ou `ScriptBlock` élément, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="4d3c1-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="4d3c1-110">Attributes</span></span>

<span data-ttu-id="4d3c1-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4d3c1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4d3c1-112">Child Elements</span></span>

|<span data-ttu-id="4d3c1-113">Élément</span><span class="sxs-lookup"><span data-stu-id="4d3c1-113">Element</span></span>|<span data-ttu-id="4d3c1-114">Description</span><span class="sxs-lookup"><span data-stu-id="4d3c1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d3c1-115">Élément FormatString pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4d3c1-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="4d3c1-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4d3c1-117">Spécifie un modèle de format qui définit comment la valeur de propriété ou un script est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="4d3c1-118">Élément PropertyName pour WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="4d3c1-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="4d3c1-119">Spécifie la propriété de l’objet dont la valeur est affichée dans l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="4d3c1-120">Élément ScriptBlock pour WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="4d3c1-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="4d3c1-121">Spécifie le script dont la valeur est affichée dans l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4d3c1-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4d3c1-122">Parent Elements</span></span>

|<span data-ttu-id="4d3c1-123">Élément</span><span class="sxs-lookup"><span data-stu-id="4d3c1-123">Element</span></span>|<span data-ttu-id="4d3c1-124">Description</span><span class="sxs-lookup"><span data-stu-id="4d3c1-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d3c1-125">Élément WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4d3c1-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="4d3c1-126">Fournit une définition de l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4d3c1-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="4d3c1-127">Remarks</span></span>

<span data-ttu-id="4d3c1-128">Pour plus d’informations sur les composants d’un affichage plus large, consultez [Affichage large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="4d3c1-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4d3c1-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d3c1-129">Example</span></span>

<span data-ttu-id="4d3c1-130">L’exemple suivant montre un `WideEntry` élément qui définit un seul `WideItem` élément.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="4d3c1-131">Le `WideItem` élément définit la propriété ou un script dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="4d3c1-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="4d3c1-132">Pour obtenir un exemple complet d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="4d3c1-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d3c1-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d3c1-133">See Also</span></span>

[<span data-ttu-id="4d3c1-134">Élément FormatString pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4d3c1-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="4d3c1-135">Élément PropertyName pour WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="4d3c1-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="4d3c1-136">Élément ScriptBlock pour WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="4d3c1-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="4d3c1-137">Élément WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4d3c1-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="4d3c1-138">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d3c1-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
