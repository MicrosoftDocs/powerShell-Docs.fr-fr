---
title: Élément SelectionSetName pour EntrySelectedBy pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855025"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="1e4d4-102">SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="1e4d4-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="1e4d4-103">Spécifie un ensemble d’objets .NET pour l’entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="1e4d4-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="1e4d4-104">Il n’existe aucune limite au nombre de jeux de sélection peut être spécifié pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="1e4d4-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="1e4d4-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour EntrySelectedBy de vue (Format) Élément pour CustomEntry pour l’élément d’affichage (Format) de SelectionSetName pour EntrySelectedBy pour CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1e4d4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e4d4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e4d4-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e4d4-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="1e4d4-107">Attributes and Elements</span></span>

<span data-ttu-id="1e4d4-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="1e4d4-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e4d4-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="1e4d4-109">Attributes</span></span>

<span data-ttu-id="1e4d4-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1e4d4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e4d4-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1e4d4-111">Child Elements</span></span>

<span data-ttu-id="1e4d4-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1e4d4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1e4d4-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1e4d4-113">Parent Elements</span></span>

|<span data-ttu-id="1e4d4-114">Élément</span><span class="sxs-lookup"><span data-stu-id="1e4d4-114">Element</span></span>|<span data-ttu-id="1e4d4-115">Description</span><span class="sxs-lookup"><span data-stu-id="1e4d4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e4d4-116">Élément EntrySelectedBy pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="1e4d4-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1e4d4-117">Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1e4d4-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1e4d4-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="1e4d4-118">Text Value</span></span>

<span data-ttu-id="1e4d4-119">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="1e4d4-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e4d4-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="1e4d4-120">Remarks</span></span>

<span data-ttu-id="1e4d4-121">Chaque entrée de contrôle personnalisé doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="1e4d4-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="1e4d4-122">Sélection jeux sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="1e4d4-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="1e4d4-123">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="1e4d4-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="1e4d4-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition sélection définit](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1e4d4-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="1e4d4-125">Pour plus d’informations sur les composants d’une vue de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1e4d4-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e4d4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e4d4-126">See Also</span></span>

[<span data-ttu-id="1e4d4-127">Élément EntrySelectedBy pour CustomEntry pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="1e4d4-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1e4d4-128">Affichage de contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="1e4d4-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="1e4d4-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e4d4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
