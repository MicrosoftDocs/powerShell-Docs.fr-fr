---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour GroupBy (Format)
description: PropertyName, élément pour GroupBy (Format)
ms.openlocfilehash: 44351c46ff2386f967644fef4f423b3858dc1619
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666142"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="4bc8d-103">PropertyName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4bc8d-103">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="4bc8d-104">Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="4bc8d-104">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="4bc8d-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) PropertyName pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="4bc8d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4bc8d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bc8d-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4bc8d-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4bc8d-107">Attributes and Elements</span></span>

<span data-ttu-id="4bc8d-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="4bc8d-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4bc8d-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="4bc8d-109">Attributes</span></span>

<span data-ttu-id="4bc8d-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4bc8d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4bc8d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4bc8d-111">Child Elements</span></span>

<span data-ttu-id="4bc8d-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4bc8d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4bc8d-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4bc8d-113">Parent Elements</span></span>

|<span data-ttu-id="4bc8d-114">Élément</span><span class="sxs-lookup"><span data-stu-id="4bc8d-114">Element</span></span>|<span data-ttu-id="4bc8d-115">Description</span><span class="sxs-lookup"><span data-stu-id="4bc8d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4bc8d-116">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="4bc8d-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="4bc8d-117">Définit le mode d’affichage d’un groupe d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="4bc8d-117">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4bc8d-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="4bc8d-118">Text Value</span></span>

<span data-ttu-id="4bc8d-119">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="4bc8d-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bc8d-120">Notes</span><span class="sxs-lookup"><span data-stu-id="4bc8d-120">Remarks</span></span>

<span data-ttu-id="4bc8d-121">Windows PowerShell démarre un nouveau groupe chaque fois que la valeur de cette propriété change.</span><span class="sxs-lookup"><span data-stu-id="4bc8d-121">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="4bc8d-122">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-groupby-format.md) pour démarrer un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="4bc8d-122">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="4bc8d-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="4bc8d-123">Example</span></span>

<span data-ttu-id="4bc8d-124">L’exemple suivant montre comment démarrer un nouveau groupe lorsque la valeur d’une propriété change.</span><span class="sxs-lookup"><span data-stu-id="4bc8d-124">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="4bc8d-125">Pour obtenir un exemple de fichier de mise en forme complet qui comprend cet élément, consultez [vue étendue (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="4bc8d-125">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4bc8d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bc8d-126">See Also</span></span>

[<span data-ttu-id="4bc8d-127">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="4bc8d-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="4bc8d-128">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4bc8d-128">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="4bc8d-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="4bc8d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
