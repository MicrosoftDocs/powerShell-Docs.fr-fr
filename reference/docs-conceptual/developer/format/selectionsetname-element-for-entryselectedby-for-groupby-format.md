---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)
ms.openlocfilehash: 7ebe5d884061243c8b4af196788187d84c15a92e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651851"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="fd3aa-103">SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fd3aa-103">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="fd3aa-104">Spécifie un ensemble d’objets .NET pour l’entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="fd3aa-105">Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="fd3aa-106">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="fd3aa-107">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) EntrySelectedBy élément pour CustomEntry pour GroupBy (format) élément SelectionSetName pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="fd3aa-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fd3aa-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd3aa-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd3aa-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fd3aa-109">Attributes and Elements</span></span>

<span data-ttu-id="fd3aa-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd3aa-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="fd3aa-111">Attributes</span></span>

<span data-ttu-id="fd3aa-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd3aa-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fd3aa-113">Child Elements</span></span>

<span data-ttu-id="fd3aa-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fd3aa-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fd3aa-115">Parent Elements</span></span>

|<span data-ttu-id="fd3aa-116">Élément</span><span class="sxs-lookup"><span data-stu-id="fd3aa-116">Element</span></span>|<span data-ttu-id="fd3aa-117">Description</span><span class="sxs-lookup"><span data-stu-id="fd3aa-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd3aa-118">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fd3aa-118">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="fd3aa-119">Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-119">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fd3aa-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="fd3aa-120">Text Value</span></span>

<span data-ttu-id="fd3aa-121">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd3aa-122">Notes</span><span class="sxs-lookup"><span data-stu-id="fd3aa-122">Remarks</span></span>

<span data-ttu-id="fd3aa-123">Chaque définition de contrôle personnalisé doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-123">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="fd3aa-124">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-124">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="fd3aa-125">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="fd3aa-125">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="fd3aa-126">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="fd3aa-126">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="fd3aa-127">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="fd3aa-127">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fd3aa-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd3aa-128">See Also</span></span>

[<span data-ttu-id="fd3aa-129">EntrySelectedBy, élément pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fd3aa-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="fd3aa-130">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="fd3aa-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="fd3aa-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd3aa-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
