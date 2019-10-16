---
title: PropertyName, élément de GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362518"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="0d6c3-102">PropertyName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="0d6c3-103">Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="0d6c3-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) PropertyName pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d6c3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d6c3-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d6c3-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="0d6c3-106">Attributes and Elements</span></span>

<span data-ttu-id="0d6c3-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d6c3-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="0d6c3-108">Attributes</span></span>

<span data-ttu-id="0d6c3-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d6c3-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0d6c3-110">Child Elements</span></span>

<span data-ttu-id="0d6c3-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0d6c3-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0d6c3-112">Parent Elements</span></span>

|<span data-ttu-id="0d6c3-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0d6c3-113">Element</span></span>|<span data-ttu-id="0d6c3-114">Description</span><span class="sxs-lookup"><span data-stu-id="0d6c3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d6c3-115">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="0d6c3-116">Définit le mode d’affichage d’un groupe d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0d6c3-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="0d6c3-117">Text Value</span></span>

<span data-ttu-id="0d6c3-118">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d6c3-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="0d6c3-119">Remarks</span></span>

<span data-ttu-id="0d6c3-120">Windows PowerShell démarre un nouveau groupe chaque fois que la valeur de cette propriété change.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="0d6c3-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-groupby-format.md) pour démarrer un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="0d6c3-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="0d6c3-122">Example</span></span>

<span data-ttu-id="0d6c3-123">L’exemple suivant montre comment démarrer un nouveau groupe lorsque la valeur d’une propriété change.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="0d6c3-124">Pour obtenir un exemple de fichier de mise en forme complet qui comprend cet élément, consultez [vue étendue (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="0d6c3-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d6c3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d6c3-125">See Also</span></span>

[<span data-ttu-id="0d6c3-126">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="0d6c3-127">Élément ScriptBlock pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="0d6c3-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d6c3-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
