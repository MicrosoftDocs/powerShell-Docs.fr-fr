---
title: Élément SelectionSetName pour EntrySelectedBy pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361978"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="90394-102">SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="90394-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="90394-103">Spécifie un jeu d’objets .NET pour la définition.</span><span class="sxs-lookup"><span data-stu-id="90394-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="90394-104">La définition est utilisée chaque fois que l’un de ces objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="90394-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="90394-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) SelectionSetName, élément pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="90394-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="90394-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90394-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="90394-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="90394-107">Attributes and Elements</span></span>

<span data-ttu-id="90394-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="90394-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="90394-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="90394-109">Attributes</span></span>

<span data-ttu-id="90394-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="90394-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90394-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="90394-111">Child Elements</span></span>

<span data-ttu-id="90394-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="90394-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="90394-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="90394-113">Parent Elements</span></span>

|<span data-ttu-id="90394-114">Élément</span><span class="sxs-lookup"><span data-stu-id="90394-114">Element</span></span>|<span data-ttu-id="90394-115">Description</span><span class="sxs-lookup"><span data-stu-id="90394-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90394-116">Élément EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="90394-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="90394-117">Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="90394-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="90394-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="90394-118">Text Value</span></span>

<span data-ttu-id="90394-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="90394-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="90394-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="90394-120">Remarks</span></span>

<span data-ttu-id="90394-121">Chaque définition doit spécifier un nom de type, un jeu de sélection ou une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="90394-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="90394-122">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="90394-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="90394-123">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="90394-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="90394-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux d’objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="90394-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="90394-125">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="90394-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90394-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90394-126">See Also</span></span>

[<span data-ttu-id="90394-127">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="90394-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="90394-128">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="90394-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="90394-129">Élément EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="90394-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="90394-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="90394-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
