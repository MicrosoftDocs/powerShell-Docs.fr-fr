---
title: Élément PropertyName pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863265"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="56a2c-102">PropertyName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="56a2c-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="56a2c-103">Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="56a2c-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="56a2c-104">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément d’affichage (Format) PropertyName élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="56a2c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="56a2c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56a2c-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="56a2c-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="56a2c-106">Attributes and Elements</span></span>

<span data-ttu-id="56a2c-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="56a2c-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="56a2c-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="56a2c-108">Attributes</span></span>

<span data-ttu-id="56a2c-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="56a2c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="56a2c-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="56a2c-110">Child Elements</span></span>

<span data-ttu-id="56a2c-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="56a2c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="56a2c-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="56a2c-112">Parent Elements</span></span>

|<span data-ttu-id="56a2c-113">Élément</span><span class="sxs-lookup"><span data-stu-id="56a2c-113">Element</span></span>|<span data-ttu-id="56a2c-114">Description</span><span class="sxs-lookup"><span data-stu-id="56a2c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56a2c-115">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="56a2c-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="56a2c-116">Définit la façon dont un groupe d’objets .NET est affiché.</span><span class="sxs-lookup"><span data-stu-id="56a2c-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="56a2c-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="56a2c-117">Text Value</span></span>

<span data-ttu-id="56a2c-118">Spécifiez le nom de propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="56a2c-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="56a2c-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="56a2c-119">Remarks</span></span>

<span data-ttu-id="56a2c-120">Windows PowerShell démarre un nouveau groupe chaque fois que la valeur de cette propriété change.</span><span class="sxs-lookup"><span data-stu-id="56a2c-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="56a2c-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [ScriptBlock](./scriptblock-element-for-groupby-format.md) élément pour démarrer un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="56a2c-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="56a2c-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="56a2c-122">Example</span></span>

<span data-ttu-id="56a2c-123">L’exemple suivant montre comment démarrer un nouveau groupe lorsque la valeur d’une propriété change.</span><span class="sxs-lookup"><span data-stu-id="56a2c-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="56a2c-124">Pour obtenir un exemple d’un fichier de mise en forme complète qui inclut cet élément, consultez [affichage plus large (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="56a2c-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="56a2c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56a2c-125">See Also</span></span>

[<span data-ttu-id="56a2c-126">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="56a2c-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="56a2c-127">Élément ScriptBlock pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="56a2c-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="56a2c-128">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="56a2c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
