---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)
ms.openlocfilehash: 3211b7cacd7e57770b48b03f4aade33da506f180
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664736"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="b4f36-103">SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="b4f36-103">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="b4f36-104">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b4f36-104">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="b4f36-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="b4f36-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b4f36-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément d’affichage (format) CustomEntry pour CustomEntries pour les contrôles de l’élément EntrySelectedBy (format) pour CustomEntry pour les contrôles de l’élément View (format) SelectionSetName pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="b4f36-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4f36-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4f36-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4f36-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b4f36-108">Attributes and Elements</span></span>

<span data-ttu-id="b4f36-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="b4f36-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4f36-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b4f36-110">Attributes</span></span>

<span data-ttu-id="b4f36-111">None</span><span class="sxs-lookup"><span data-stu-id="b4f36-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4f36-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b4f36-112">Child Elements</span></span>

<span data-ttu-id="b4f36-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b4f36-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b4f36-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b4f36-114">Parent Elements</span></span>

|<span data-ttu-id="b4f36-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b4f36-115">Element</span></span>|<span data-ttu-id="b4f36-116">Description</span><span class="sxs-lookup"><span data-stu-id="b4f36-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4f36-117">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="b4f36-117">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="b4f36-118">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="b4f36-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b4f36-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="b4f36-119">Text Value</span></span>

<span data-ttu-id="b4f36-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="b4f36-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4f36-121">Notes</span><span class="sxs-lookup"><span data-stu-id="b4f36-121">Remarks</span></span>

<span data-ttu-id="b4f36-122">Chaque définition de contrôle doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="b4f36-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b4f36-123">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="b4f36-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="b4f36-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b4f36-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4f36-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4f36-125">See Also</span></span>

[<span data-ttu-id="b4f36-126">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="b4f36-126">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="b4f36-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4f36-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
