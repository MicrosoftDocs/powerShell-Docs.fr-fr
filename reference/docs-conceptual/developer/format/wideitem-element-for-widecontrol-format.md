---
title: Élément WideItem pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361398"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="d8bba-102">WideItem, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d8bba-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="d8bba-103">Définit la propriété ou le script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="d8bba-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="d8bba-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry, élément (format) WideItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="d8bba-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8bba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8bba-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8bba-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d8bba-106">Attributes and Elements</span></span>

<span data-ttu-id="d8bba-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="d8bba-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="d8bba-108">L’élément `FormatString` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d8bba-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="d8bba-109">Toutefois, vous devez spécifier un élément `PropertyName` ou `ScriptBlock`, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="d8bba-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8bba-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d8bba-110">Attributes</span></span>

<span data-ttu-id="d8bba-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d8bba-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8bba-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d8bba-112">Child Elements</span></span>

|<span data-ttu-id="d8bba-113">Élément</span><span class="sxs-lookup"><span data-stu-id="d8bba-113">Element</span></span>|<span data-ttu-id="d8bba-114">Description</span><span class="sxs-lookup"><span data-stu-id="d8bba-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8bba-115">FormatString, élément de WideItem pour WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="d8bba-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="d8bba-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d8bba-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d8bba-117">Spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="d8bba-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="d8bba-118">PropertyName, élément de WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="d8bba-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="d8bba-119">Spécifie la propriété de l’objet dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="d8bba-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="d8bba-120">Élément ScriptBlock pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="d8bba-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="d8bba-121">Spécifie le script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="d8bba-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d8bba-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d8bba-122">Parent Elements</span></span>

|<span data-ttu-id="d8bba-123">Élément</span><span class="sxs-lookup"><span data-stu-id="d8bba-123">Element</span></span>|<span data-ttu-id="d8bba-124">Description</span><span class="sxs-lookup"><span data-stu-id="d8bba-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8bba-125">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d8bba-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="d8bba-126">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="d8bba-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d8bba-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8bba-127">Remarks</span></span>

<span data-ttu-id="d8bba-128">Pour plus d’informations sur les composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d8bba-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d8bba-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8bba-129">Example</span></span>

<span data-ttu-id="d8bba-130">L’exemple suivant montre un élément `WideEntry` qui définit un seul élément `WideItem`.</span><span class="sxs-lookup"><span data-stu-id="d8bba-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="d8bba-131">L’élément `WideItem` définit la propriété ou le script dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="d8bba-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="d8bba-132">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d8bba-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8bba-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8bba-133">See Also</span></span>

[<span data-ttu-id="d8bba-134">FormatString, élément de WideItem pour WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="d8bba-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="d8bba-135">PropertyName, élément de WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="d8bba-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="d8bba-136">Élément ScriptBlock pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="d8bba-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="d8bba-137">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d8bba-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="d8bba-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8bba-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
