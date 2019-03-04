---
title: Élément EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859535"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="e86e4-102">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e86e4-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="e86e4-103">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e86e4-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="e86e4-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="e86e4-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e86e4-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles pour l’élément d’affichage (Format) de EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e86e4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e86e4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e86e4-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e86e4-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e86e4-107">Attributes and Elements</span></span>

<span data-ttu-id="e86e4-108">Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="e86e4-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="e86e4-109">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection d’une définition.</span><span class="sxs-lookup"><span data-stu-id="e86e4-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="e86e4-110">Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="e86e4-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="e86e4-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="e86e4-111">Attributes</span></span>

<span data-ttu-id="e86e4-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e86e4-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e86e4-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e86e4-113">Child Elements</span></span>

|<span data-ttu-id="e86e4-114">Élément</span><span class="sxs-lookup"><span data-stu-id="e86e4-114">Element</span></span>|<span data-ttu-id="e86e4-115">Description</span><span class="sxs-lookup"><span data-stu-id="e86e4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e86e4-116">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e86e4-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e86e4-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e86e4-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e86e4-118">Définit la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e86e4-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="e86e4-119">Élément SelectionSetName pour EntrySelectedBy pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e86e4-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e86e4-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e86e4-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e86e4-121">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e86e4-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="e86e4-122">Élément TypeName pour EntrySelectedBy pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e86e4-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e86e4-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e86e4-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e86e4-124">Spécifie un type .NET qui utilise cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e86e4-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e86e4-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e86e4-125">Parent Elements</span></span>

|<span data-ttu-id="e86e4-126">Élément</span><span class="sxs-lookup"><span data-stu-id="e86e4-126">Element</span></span>|<span data-ttu-id="e86e4-127">Description</span><span class="sxs-lookup"><span data-stu-id="e86e4-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e86e4-128">Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e86e4-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="e86e4-129">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e86e4-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e86e4-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="e86e4-130">Remarks</span></span>

<span data-ttu-id="e86e4-131">Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique ou lorsqu’une valeur de propriété spécifique ou de script prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="e86e4-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="e86e4-132">Pour plus d’informations sur les conditions de sélection, consultez [définition Conditions pour lorsqu’une entrée de la vue ou d’élément est utilisé](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e86e4-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e86e4-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e86e4-133">See Also</span></span>

[<span data-ttu-id="e86e4-134">Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e86e4-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="e86e4-135">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e86e4-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
