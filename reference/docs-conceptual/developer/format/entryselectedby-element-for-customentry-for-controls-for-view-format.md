---
title: Élément EntrySelectedBy pour CustomEntry pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363888"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="e1815-102">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e1815-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="e1815-103">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e1815-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="e1815-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="e1815-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e1815-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles de l’élément View (format) CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) EntrySelectedBy pour CustomEntry pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e1815-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1815-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1815-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1815-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e1815-107">Attributes and Elements</span></span>

<span data-ttu-id="e1815-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="e1815-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="e1815-109">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition.</span><span class="sxs-lookup"><span data-stu-id="e1815-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="e1815-110">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="e1815-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1815-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e1815-111">Attributes</span></span>

<span data-ttu-id="e1815-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e1815-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1815-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e1815-113">Child Elements</span></span>

|<span data-ttu-id="e1815-114">Élément</span><span class="sxs-lookup"><span data-stu-id="e1815-114">Element</span></span>|<span data-ttu-id="e1815-115">Description</span><span class="sxs-lookup"><span data-stu-id="e1815-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1815-116">Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e1815-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e1815-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e1815-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e1815-118">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e1815-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="e1815-119">Élément SelectionSetName pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e1815-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e1815-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e1815-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e1815-121">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e1815-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="e1815-122">Élément TypeName pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e1815-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e1815-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e1815-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e1815-124">Spécifie un type .NET qui utilise cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e1815-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e1815-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e1815-125">Parent Elements</span></span>

|<span data-ttu-id="e1815-126">Élément</span><span class="sxs-lookup"><span data-stu-id="e1815-126">Element</span></span>|<span data-ttu-id="e1815-127">Description</span><span class="sxs-lookup"><span data-stu-id="e1815-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1815-128">Élément CustomEntry pour CustomEntries pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e1815-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="e1815-129">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e1815-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e1815-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="e1815-130">Remarks</span></span>

<span data-ttu-id="e1815-131">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="e1815-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="e1815-132">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e1815-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1815-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1815-133">See Also</span></span>

[<span data-ttu-id="e1815-134">Élément CustomEntry pour CustomEntries pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e1815-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="e1815-135">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1815-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
