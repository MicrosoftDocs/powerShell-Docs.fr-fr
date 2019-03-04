---
title: Élément EntrySelectedBy pour EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855585"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="6c4c4-102">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c4c4-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="6c4c4-103">Définit les types .NET qui utilisent cette définition ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="6c4c4-104">Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) élément EnumerableExpansion (Format) EntrySelectedBy élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c4c4-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6c4c4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c4c4-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c4c4-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="6c4c4-106">Attributes and Elements</span></span>

<span data-ttu-id="6c4c4-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c4c4-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="6c4c4-108">Attributes</span></span>

<span data-ttu-id="6c4c4-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c4c4-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6c4c4-110">Child Elements</span></span>

|<span data-ttu-id="6c4c4-111">Élément</span><span class="sxs-lookup"><span data-stu-id="6c4c4-111">Element</span></span>|<span data-ttu-id="6c4c4-112">Description</span><span class="sxs-lookup"><span data-stu-id="6c4c4-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c4c4-113">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c4c4-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6c4c4-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-114">Optional element.</span></span><br /><br /> <span data-ttu-id="6c4c4-115">Définit la condition qui doit exister pour développer la collection d’objets de cette définition.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="6c4c4-116">Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c4c4-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6c4c4-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-117">Optional element.</span></span><br /><br /> <span data-ttu-id="6c4c4-118">Spécifie un ensemble de types .NET qui utilisent cette définition de la façon dont les objets de collection sont développés.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="6c4c4-119">Élément TypeName pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c4c4-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6c4c4-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-120">Optional element.</span></span><br /><br /> <span data-ttu-id="6c4c4-121">Spécifie un type .NET qui utilise cette définition de la façon dont les objets de collection sont développés.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6c4c4-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6c4c4-122">Parent Elements</span></span>

|<span data-ttu-id="6c4c4-123">Élément</span><span class="sxs-lookup"><span data-stu-id="6c4c4-123">Element</span></span>|<span data-ttu-id="6c4c4-124">Description</span><span class="sxs-lookup"><span data-stu-id="6c4c4-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c4c4-125">Élément EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c4c4-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="6c4c4-126">Définit des collection .NET façon dont certains objets sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6c4c4-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="6c4c4-127">Remarks</span></span>

<span data-ttu-id="6c4c4-128">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour une entrée de définition.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="6c4c4-129">Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="6c4c4-130">Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique, ou qui a pour résultat une valeur de propriété spécifique ou un script `true`.</span><span class="sxs-lookup"><span data-stu-id="6c4c4-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="6c4c4-131">Pour plus d’informations sur les conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6c4c4-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c4c4-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c4c4-132">See Also</span></span>

[<span data-ttu-id="6c4c4-133">Définition des Conditions pour l’affichage des données</span><span class="sxs-lookup"><span data-stu-id="6c4c4-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6c4c4-134">Élément EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c4c4-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="6c4c4-135">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c4c4-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6c4c4-136">Élément SelectionSetName pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c4c4-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6c4c4-137">Élément TypeName pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6c4c4-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6c4c4-138">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c4c4-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
