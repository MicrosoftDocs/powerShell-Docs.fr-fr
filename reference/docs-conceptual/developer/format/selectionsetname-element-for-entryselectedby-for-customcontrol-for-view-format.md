---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)
ms.openlocfilehash: a158c5476fb3a168a146ce67565c0ed6f7859519
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651918"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="dbdab-103">SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="dbdab-103">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="dbdab-104">Spécifie un ensemble d’objets .NET pour l’entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="dbdab-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="dbdab-105">Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="dbdab-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="dbdab-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour l’élément View (format) SelectionSetName pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="dbdab-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dbdab-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbdab-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dbdab-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dbdab-108">Attributes and Elements</span></span>

<span data-ttu-id="dbdab-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="dbdab-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dbdab-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="dbdab-110">Attributes</span></span>

<span data-ttu-id="dbdab-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dbdab-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dbdab-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dbdab-112">Child Elements</span></span>

<span data-ttu-id="dbdab-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dbdab-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dbdab-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dbdab-114">Parent Elements</span></span>

|<span data-ttu-id="dbdab-115">Élément</span><span class="sxs-lookup"><span data-stu-id="dbdab-115">Element</span></span>|<span data-ttu-id="dbdab-116">Description</span><span class="sxs-lookup"><span data-stu-id="dbdab-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dbdab-117">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="dbdab-117">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="dbdab-118">Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="dbdab-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dbdab-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="dbdab-119">Text Value</span></span>

<span data-ttu-id="dbdab-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="dbdab-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="dbdab-121">Notes</span><span class="sxs-lookup"><span data-stu-id="dbdab-121">Remarks</span></span>

<span data-ttu-id="dbdab-122">Au moins un nom de type, un jeu de sélection ou une condition de sélection doit être défini pour chaque entrée de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="dbdab-122">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="dbdab-123">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="dbdab-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="dbdab-124">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="dbdab-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="dbdab-125">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="dbdab-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="dbdab-126">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="dbdab-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dbdab-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbdab-127">See Also</span></span>

[<span data-ttu-id="dbdab-128">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="dbdab-128">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="dbdab-129">Affichage de contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="dbdab-129">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="dbdab-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbdab-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
