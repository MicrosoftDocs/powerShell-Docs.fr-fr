---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour ListEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368398"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="bf6f3-102">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="bf6f3-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="bf6f3-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="bf6f3-104">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="bf6f3-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format) SelectionSetName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="bf6f3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bf6f3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf6f3-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bf6f3-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="bf6f3-107">Attributes and Elements</span></span>

<span data-ttu-id="bf6f3-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bf6f3-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="bf6f3-109">Attributes</span></span>

<span data-ttu-id="bf6f3-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bf6f3-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bf6f3-111">Child Elements</span></span>

<span data-ttu-id="bf6f3-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bf6f3-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bf6f3-113">Parent Elements</span></span>

|<span data-ttu-id="bf6f3-114">Élément</span><span class="sxs-lookup"><span data-stu-id="bf6f3-114">Element</span></span>|<span data-ttu-id="bf6f3-115">Description</span><span class="sxs-lookup"><span data-stu-id="bf6f3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bf6f3-116">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="bf6f3-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="bf6f3-117">Définit la condition qui doit exister pour utiliser cette définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bf6f3-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="bf6f3-118">Text Value</span></span>

<span data-ttu-id="bf6f3-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf6f3-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="bf6f3-120">Remarks</span></span>

<span data-ttu-id="bf6f3-121">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="bf6f3-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bf6f3-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="bf6f3-123">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="bf6f3-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="bf6f3-124">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="bf6f3-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="bf6f3-125">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="bf6f3-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf6f3-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf6f3-126">See Also</span></span>

[<span data-ttu-id="bf6f3-127">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="bf6f3-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="bf6f3-128">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="bf6f3-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="bf6f3-129">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="bf6f3-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="bf6f3-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf6f3-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
