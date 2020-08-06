---
title: PropertyName, élément de GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e83ebd49e4f3087c817b3cc8772889dbe85113aa
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785606"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="bb3e6-102">PropertyName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bb3e6-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="bb3e6-103">Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="bb3e6-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="bb3e6-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) PropertyName pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bb3e6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bb3e6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb3e6-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bb3e6-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bb3e6-106">Attributes and Elements</span></span>

<span data-ttu-id="bb3e6-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="bb3e6-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bb3e6-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="bb3e6-108">Attributes</span></span>

<span data-ttu-id="bb3e6-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bb3e6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bb3e6-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bb3e6-110">Child Elements</span></span>

<span data-ttu-id="bb3e6-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bb3e6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bb3e6-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bb3e6-112">Parent Elements</span></span>

|<span data-ttu-id="bb3e6-113">Élément</span><span class="sxs-lookup"><span data-stu-id="bb3e6-113">Element</span></span>|<span data-ttu-id="bb3e6-114">Description</span><span class="sxs-lookup"><span data-stu-id="bb3e6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bb3e6-115">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="bb3e6-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="bb3e6-116">Définit le mode d’affichage d’un groupe d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="bb3e6-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bb3e6-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="bb3e6-117">Text Value</span></span>

<span data-ttu-id="bb3e6-118">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="bb3e6-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb3e6-119">Notes</span><span class="sxs-lookup"><span data-stu-id="bb3e6-119">Remarks</span></span>

<span data-ttu-id="bb3e6-120">Windows PowerShell démarre un nouveau groupe chaque fois que la valeur de cette propriété change.</span><span class="sxs-lookup"><span data-stu-id="bb3e6-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="bb3e6-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-groupby-format.md) pour démarrer un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="bb3e6-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="bb3e6-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb3e6-122">Example</span></span>

<span data-ttu-id="bb3e6-123">L’exemple suivant montre comment démarrer un nouveau groupe lorsque la valeur d’une propriété change.</span><span class="sxs-lookup"><span data-stu-id="bb3e6-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="bb3e6-124">Pour obtenir un exemple de fichier de mise en forme complet qui comprend cet élément, consultez [vue étendue (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="bb3e6-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb3e6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb3e6-125">See Also</span></span>

[<span data-ttu-id="bb3e6-126">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="bb3e6-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="bb3e6-127">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bb3e6-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="bb3e6-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="bb3e6-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
