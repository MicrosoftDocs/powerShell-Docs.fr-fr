---
title: Élément SelectionSetName pour EntrySelectedBy pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075560"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="0c38b-102">SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0c38b-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="0c38b-103">Spécifie un ensemble d’objets .NET pour l’entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="0c38b-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="0c38b-104">Il n’existe aucune limite au nombre de jeux de sélection peut être spécifié pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="0c38b-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="0c38b-105">Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) EntrySelectedBy élément d’élément de SelectionSetName ListEntry (Format) pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0c38b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c38b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c38b-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c38b-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="0c38b-107">Attributes and Elements</span></span>

<span data-ttu-id="0c38b-108">Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="0c38b-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c38b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="0c38b-109">Attributes</span></span>

<span data-ttu-id="0c38b-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0c38b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c38b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c38b-111">Child Elements</span></span>

<span data-ttu-id="0c38b-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0c38b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0c38b-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c38b-113">Parent Elements</span></span>

|<span data-ttu-id="0c38b-114">Élément</span><span class="sxs-lookup"><span data-stu-id="0c38b-114">Element</span></span>|<span data-ttu-id="0c38b-115">Description</span><span class="sxs-lookup"><span data-stu-id="0c38b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c38b-116">Élément EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0c38b-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0c38b-117">Définit les types .NET qui utilisent cette entrée de liste ou la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0c38b-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0c38b-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="0c38b-118">Text Value</span></span>

<span data-ttu-id="0c38b-119">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="0c38b-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c38b-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="0c38b-120">Remarks</span></span>

<span data-ttu-id="0c38b-121">Chaque entrée de liste doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="0c38b-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0c38b-122">Sélection jeux sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="0c38b-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="0c38b-123">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="0c38b-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="0c38b-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition définit des objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0c38b-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="0c38b-125">Pour plus d’informations sur les composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="0c38b-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0c38b-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c38b-126">Example</span></span>

<span data-ttu-id="0c38b-127">L’exemple suivant montre comment spécifier une jeu de sélection pour une entrée d’une vue liste.</span><span class="sxs-lookup"><span data-stu-id="0c38b-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="0c38b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c38b-128">See Also</span></span>

[<span data-ttu-id="0c38b-129">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="0c38b-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0c38b-130">Élément EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0c38b-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0c38b-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c38b-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
