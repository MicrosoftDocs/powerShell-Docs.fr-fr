---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075509"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="2f009-102">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2f009-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="2f009-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="2f009-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="2f009-104">Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de cette définition de la vue de liste.</span><span class="sxs-lookup"><span data-stu-id="2f009-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="2f009-105">Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) EntrySelectedBy élément d’élément de SelectionCondition ListEntry (Format) pour EntrySelectedBy d’élément de SelectionSetName ListEntry (Format) pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2f009-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f009-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f009-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f009-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="2f009-107">Attributes and Elements</span></span>

<span data-ttu-id="2f009-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="2f009-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f009-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="2f009-109">Attributes</span></span>

<span data-ttu-id="2f009-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="2f009-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f009-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2f009-111">Child Elements</span></span>

<span data-ttu-id="2f009-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="2f009-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2f009-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2f009-113">Parent Elements</span></span>

|<span data-ttu-id="2f009-114">Élément</span><span class="sxs-lookup"><span data-stu-id="2f009-114">Element</span></span>|<span data-ttu-id="2f009-115">Description</span><span class="sxs-lookup"><span data-stu-id="2f009-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f009-116">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2f009-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2f009-117">Définit la condition qui doit exister pour pouvoir utiliser cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="2f009-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2f009-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="2f009-118">Text Value</span></span>

<span data-ttu-id="2f009-119">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="2f009-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f009-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="2f009-120">Remarks</span></span>

<span data-ttu-id="2f009-121">La condition de sélection peut spécifier un jeu de sélection ou d’un type .NET, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="2f009-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="2f009-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2f009-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2f009-123">Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="2f009-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="2f009-124">Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2f009-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="2f009-125">Pour plus d’informations sur d’autres composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="2f009-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f009-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f009-126">See Also</span></span>

[<span data-ttu-id="2f009-127">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="2f009-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2f009-128">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="2f009-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2f009-129">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2f009-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2f009-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f009-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
