---
title: Élément EntrySelectedBy pour CustomEntry pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363858"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="cd2f2-102">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cd2f2-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="cd2f2-103">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="cd2f2-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cd2f2-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément EntrySelectedBy pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cd2f2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cd2f2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd2f2-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cd2f2-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="cd2f2-107">Attributes and Elements</span></span>

<span data-ttu-id="cd2f2-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="cd2f2-109">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="cd2f2-110">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="cd2f2-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="cd2f2-111">Attributes</span></span>

<span data-ttu-id="cd2f2-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cd2f2-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cd2f2-113">Child Elements</span></span>

|<span data-ttu-id="cd2f2-114">Élément</span><span class="sxs-lookup"><span data-stu-id="cd2f2-114">Element</span></span>|<span data-ttu-id="cd2f2-115">Description</span><span class="sxs-lookup"><span data-stu-id="cd2f2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd2f2-116">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cd2f2-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="cd2f2-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-117">Optional element.</span></span><br /><br /> <span data-ttu-id="cd2f2-118">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="cd2f2-119">Élément SelectionSetName pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cd2f2-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="cd2f2-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-120">Optional element.</span></span><br /><br /> <span data-ttu-id="cd2f2-121">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="cd2f2-122">Élément TypeName pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cd2f2-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="cd2f2-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-123">Optional element.</span></span><br /><br /> <span data-ttu-id="cd2f2-124">Spécifie un type .NET qui utilise cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cd2f2-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cd2f2-125">Parent Elements</span></span>

|<span data-ttu-id="cd2f2-126">Élément</span><span class="sxs-lookup"><span data-stu-id="cd2f2-126">Element</span></span>|<span data-ttu-id="cd2f2-127">Description</span><span class="sxs-lookup"><span data-stu-id="cd2f2-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd2f2-128">Élément CustomEntry pour CustomControl pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cd2f2-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="cd2f2-129">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cd2f2-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="cd2f2-130">Remarks</span></span>

<span data-ttu-id="cd2f2-131">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="cd2f2-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="cd2f2-132">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cd2f2-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd2f2-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd2f2-133">See Also</span></span>

[<span data-ttu-id="cd2f2-134">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cd2f2-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="cd2f2-135">Élément SelectionSetName pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cd2f2-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="cd2f2-136">Élément TypeName pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="cd2f2-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="cd2f2-137">Élément CustomEntry pour CustomEntries pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="cd2f2-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="cd2f2-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd2f2-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
