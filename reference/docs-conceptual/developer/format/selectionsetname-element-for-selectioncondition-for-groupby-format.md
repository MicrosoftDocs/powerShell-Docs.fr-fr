---
title: Élément SelectionSetName pour SelectionCondition pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361858"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="6dfa6-102">SelectionSetName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6dfa6-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="6dfa6-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="6dfa6-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="6dfa6-104">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="6dfa6-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="6dfa6-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="6dfa6-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6dfa6-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément EntrySelectedBy pour CustomEntry pour GroupBy (format) élément SelectionCondition pour EntrySelectedBy pour l’élément GroupBy (format) SelectionSetName pour l’élément SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6dfa6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6dfa6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dfa6-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6dfa6-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="6dfa6-108">Attributes and Elements</span></span>

<span data-ttu-id="6dfa6-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="6dfa6-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6dfa6-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="6dfa6-110">Attributes</span></span>

<span data-ttu-id="6dfa6-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6dfa6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6dfa6-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6dfa6-112">Child Elements</span></span>

<span data-ttu-id="6dfa6-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6dfa6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6dfa6-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6dfa6-114">Parent Elements</span></span>

|<span data-ttu-id="6dfa6-115">Élément</span><span class="sxs-lookup"><span data-stu-id="6dfa6-115">Element</span></span>|<span data-ttu-id="6dfa6-116">Description</span><span class="sxs-lookup"><span data-stu-id="6dfa6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6dfa6-117">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6dfa6-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="6dfa6-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="6dfa6-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6dfa6-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="6dfa6-119">Text Value</span></span>

<span data-ttu-id="6dfa6-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="6dfa6-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="6dfa6-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="6dfa6-121">Remarks</span></span>

<span data-ttu-id="6dfa6-122">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="6dfa6-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="6dfa6-123">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6dfa6-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="6dfa6-124">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="6dfa6-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="6dfa6-125">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6dfa6-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6dfa6-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dfa6-126">See Also</span></span>

[<span data-ttu-id="6dfa6-127">Élément TypeName pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6dfa6-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="6dfa6-128">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6dfa6-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="6dfa6-129">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="6dfa6-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6dfa6-130">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="6dfa6-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6dfa6-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="6dfa6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
