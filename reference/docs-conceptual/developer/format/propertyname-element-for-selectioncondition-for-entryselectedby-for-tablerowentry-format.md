---
title: PropertyName, élément de SelectionCondition pour EntrySelectedBy pour TableRowEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364998"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="c3acd-102">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c3acd-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="c3acd-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="c3acd-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c3acd-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et l’entrée de table est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c3acd-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="c3acd-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) EntrySelectedBy, élément pour TableRowEntry (format) Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format) PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c3acd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3acd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3acd-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3acd-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="c3acd-107">Attributes and Elements</span></span>

<span data-ttu-id="c3acd-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="c3acd-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3acd-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="c3acd-109">Attributes</span></span>

<span data-ttu-id="c3acd-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c3acd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3acd-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c3acd-111">Child Elements</span></span>

<span data-ttu-id="c3acd-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c3acd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3acd-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c3acd-113">Parent Elements</span></span>

|<span data-ttu-id="c3acd-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c3acd-114">Element</span></span>|<span data-ttu-id="c3acd-115">Description</span><span class="sxs-lookup"><span data-stu-id="c3acd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3acd-116">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c3acd-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="c3acd-117">Définit la condition qui doit exister pour que cette entrée de table soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="c3acd-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c3acd-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="c3acd-118">Text Value</span></span>

<span data-ttu-id="c3acd-119">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="c3acd-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3acd-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="c3acd-120">Remarks</span></span>

<span data-ttu-id="c3acd-121">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="c3acd-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="c3acd-122">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c3acd-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c3acd-123">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c3acd-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3acd-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3acd-124">See Also</span></span>

[<span data-ttu-id="c3acd-125">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="c3acd-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c3acd-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="c3acd-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c3acd-127">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c3acd-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c3acd-128">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c3acd-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c3acd-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3acd-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
