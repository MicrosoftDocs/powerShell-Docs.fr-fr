---
title: Élément SelectionSetName pour EntrySelectedBy pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364738"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="d80f7-102">SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d80f7-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="d80f7-103">Spécifie un ensemble d’objets .NET pour l’entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="d80f7-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="d80f7-104">Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="d80f7-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="d80f7-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="d80f7-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d80f7-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément EntrySelectedBy pour CustomEntry pour GroupBy (format) élément SelectionSetName pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="d80f7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d80f7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d80f7-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d80f7-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d80f7-108">Attributes and Elements</span></span>

<span data-ttu-id="d80f7-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="d80f7-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d80f7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d80f7-110">Attributes</span></span>

<span data-ttu-id="d80f7-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d80f7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d80f7-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d80f7-112">Child Elements</span></span>

<span data-ttu-id="d80f7-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d80f7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d80f7-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d80f7-114">Parent Elements</span></span>

|<span data-ttu-id="d80f7-115">Élément</span><span class="sxs-lookup"><span data-stu-id="d80f7-115">Element</span></span>|<span data-ttu-id="d80f7-116">Description</span><span class="sxs-lookup"><span data-stu-id="d80f7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d80f7-117">Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="d80f7-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="d80f7-118">Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="d80f7-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d80f7-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="d80f7-119">Text Value</span></span>

<span data-ttu-id="d80f7-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="d80f7-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d80f7-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="d80f7-121">Remarks</span></span>

<span data-ttu-id="d80f7-122">Chaque définition de contrôle personnalisé doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="d80f7-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d80f7-123">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="d80f7-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d80f7-124">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="d80f7-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d80f7-125">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d80f7-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d80f7-126">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d80f7-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d80f7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d80f7-127">See Also</span></span>

[<span data-ttu-id="d80f7-128">Élément EntrySelectedBy pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="d80f7-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="d80f7-129">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="d80f7-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d80f7-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d80f7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
