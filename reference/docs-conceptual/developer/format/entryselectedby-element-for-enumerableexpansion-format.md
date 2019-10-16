---
title: Élément EntrySelectedBy pour EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368798"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="db0e1-102">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="db0e1-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="db0e1-103">Définit les types .NET qui utilisent cette définition ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="db0e1-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="db0e1-104">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) EntrySelectedBy élément pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="db0e1-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db0e1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db0e1-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db0e1-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="db0e1-106">Attributes and Elements</span></span>

<span data-ttu-id="db0e1-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="db0e1-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db0e1-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="db0e1-108">Attributes</span></span>

<span data-ttu-id="db0e1-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="db0e1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db0e1-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db0e1-110">Child Elements</span></span>

|<span data-ttu-id="db0e1-111">Élément</span><span class="sxs-lookup"><span data-stu-id="db0e1-111">Element</span></span>|<span data-ttu-id="db0e1-112">Description</span><span class="sxs-lookup"><span data-stu-id="db0e1-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db0e1-113">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="db0e1-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="db0e1-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db0e1-114">Optional element.</span></span><br /><br /> <span data-ttu-id="db0e1-115">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="db0e1-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="db0e1-116">Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="db0e1-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="db0e1-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db0e1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="db0e1-118">Spécifie un ensemble de types .NET qui utilisent cette définition de la façon dont les objets de collection sont développés.</span><span class="sxs-lookup"><span data-stu-id="db0e1-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="db0e1-119">Élément TypeName pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="db0e1-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="db0e1-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db0e1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="db0e1-121">Spécifie un type .NET qui utilise cette définition de la façon dont les objets de la collection sont développés.</span><span class="sxs-lookup"><span data-stu-id="db0e1-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="db0e1-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db0e1-122">Parent Elements</span></span>

|<span data-ttu-id="db0e1-123">Élément</span><span class="sxs-lookup"><span data-stu-id="db0e1-123">Element</span></span>|<span data-ttu-id="db0e1-124">Description</span><span class="sxs-lookup"><span data-stu-id="db0e1-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db0e1-125">Élément EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="db0e1-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="db0e1-126">Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="db0e1-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="db0e1-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="db0e1-127">Remarks</span></span>

<span data-ttu-id="db0e1-128">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une entrée de définition.</span><span class="sxs-lookup"><span data-stu-id="db0e1-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="db0e1-129">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="db0e1-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="db0e1-130">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou un script spécifique prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="db0e1-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="db0e1-131">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="db0e1-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db0e1-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db0e1-132">See Also</span></span>

[<span data-ttu-id="db0e1-133">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="db0e1-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="db0e1-134">Élément EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="db0e1-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="db0e1-135">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="db0e1-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="db0e1-136">Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="db0e1-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="db0e1-137">Élément TypeName pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="db0e1-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="db0e1-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="db0e1-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
