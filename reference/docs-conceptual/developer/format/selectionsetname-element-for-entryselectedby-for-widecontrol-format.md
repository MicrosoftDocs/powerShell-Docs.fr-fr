---
title: Élément SelectionSetName pour EntrySelectedBy pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 546225b0619ebec83d04a7e27bbc298ffef0a14d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785249"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="98f62-102">SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="98f62-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="98f62-103">Spécifie un jeu d’objets .NET pour la définition.</span><span class="sxs-lookup"><span data-stu-id="98f62-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="98f62-104">La définition est utilisée chaque fois que l’un de ces objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="98f62-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="98f62-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) EntrySelectedBy élément pour WideEntry (format) SelectionSetName élément pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="98f62-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98f62-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98f62-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="98f62-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="98f62-107">Attributes and Elements</span></span>

<span data-ttu-id="98f62-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="98f62-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98f62-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="98f62-109">Attributes</span></span>

<span data-ttu-id="98f62-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="98f62-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98f62-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="98f62-111">Child Elements</span></span>

<span data-ttu-id="98f62-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="98f62-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="98f62-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="98f62-113">Parent Elements</span></span>

|<span data-ttu-id="98f62-114">Élément</span><span class="sxs-lookup"><span data-stu-id="98f62-114">Element</span></span>|<span data-ttu-id="98f62-115">Description</span><span class="sxs-lookup"><span data-stu-id="98f62-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98f62-116">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="98f62-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="98f62-117">Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="98f62-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="98f62-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="98f62-118">Text Value</span></span>

<span data-ttu-id="98f62-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="98f62-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="98f62-120">Notes</span><span class="sxs-lookup"><span data-stu-id="98f62-120">Remarks</span></span>

<span data-ttu-id="98f62-121">Chaque définition doit spécifier un nom de type, un jeu de sélection ou une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="98f62-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="98f62-122">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="98f62-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="98f62-123">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="98f62-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="98f62-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="98f62-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="98f62-125">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="98f62-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="98f62-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98f62-126">See Also</span></span>

[<span data-ttu-id="98f62-127">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="98f62-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="98f62-128">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="98f62-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="98f62-129">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="98f62-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="98f62-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="98f62-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
