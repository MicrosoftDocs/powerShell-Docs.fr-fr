---
title: Élément SelectionSetName pour EntrySelectedBy pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364748"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="ec18a-102">SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ec18a-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="ec18a-103">Spécifie un ensemble d’objets .NET pour l’entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="ec18a-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="ec18a-104">Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="ec18a-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="ec18a-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour la vue (format) EntrySelectedBy Élément pour CustomEntry pour l’élément SelectionSetName View (format) pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ec18a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ec18a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec18a-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec18a-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ec18a-107">Attributes and Elements</span></span>

<span data-ttu-id="ec18a-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="ec18a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec18a-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="ec18a-109">Attributes</span></span>

<span data-ttu-id="ec18a-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ec18a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec18a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ec18a-111">Child Elements</span></span>

<span data-ttu-id="ec18a-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ec18a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec18a-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ec18a-113">Parent Elements</span></span>

|<span data-ttu-id="ec18a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="ec18a-114">Element</span></span>|<span data-ttu-id="ec18a-115">Description</span><span class="sxs-lookup"><span data-stu-id="ec18a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec18a-116">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="ec18a-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="ec18a-117">Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="ec18a-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ec18a-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="ec18a-118">Text Value</span></span>

<span data-ttu-id="ec18a-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="ec18a-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec18a-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="ec18a-120">Remarks</span></span>

<span data-ttu-id="ec18a-121">Au moins un nom de type, un jeu de sélection ou une condition de sélection doit être défini pour chaque entrée de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ec18a-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ec18a-122">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="ec18a-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="ec18a-123">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="ec18a-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="ec18a-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ec18a-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ec18a-125">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ec18a-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec18a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec18a-126">See Also</span></span>

[<span data-ttu-id="ec18a-127">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="ec18a-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ec18a-128">Affichage de contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="ec18a-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ec18a-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec18a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
