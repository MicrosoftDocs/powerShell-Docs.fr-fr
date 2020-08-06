---
title: Élément SelectionSetName pour EntrySelectedBy pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3728a1886d5406b8fa4888125d1c031d0f9b1b03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785300"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="ca99c-102">SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ca99c-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="ca99c-103">Spécifie un ensemble d’objets .NET pour l’entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="ca99c-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="ca99c-104">Il n’existe aucune limite au nombre de jeux de sélection qui peuvent être spécifiés pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="ca99c-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="ca99c-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour l’élément View (format) SelectionSetName pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ca99c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca99c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca99c-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca99c-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ca99c-107">Attributes and Elements</span></span>

<span data-ttu-id="ca99c-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="ca99c-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca99c-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="ca99c-109">Attributes</span></span>

<span data-ttu-id="ca99c-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ca99c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca99c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ca99c-111">Child Elements</span></span>

<span data-ttu-id="ca99c-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ca99c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ca99c-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ca99c-113">Parent Elements</span></span>

|<span data-ttu-id="ca99c-114">Élément</span><span class="sxs-lookup"><span data-stu-id="ca99c-114">Element</span></span>|<span data-ttu-id="ca99c-115">Description</span><span class="sxs-lookup"><span data-stu-id="ca99c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca99c-116">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="ca99c-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="ca99c-117">Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="ca99c-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ca99c-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="ca99c-118">Text Value</span></span>

<span data-ttu-id="ca99c-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="ca99c-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ca99c-120">Notes</span><span class="sxs-lookup"><span data-stu-id="ca99c-120">Remarks</span></span>

<span data-ttu-id="ca99c-121">Au moins un nom de type, un jeu de sélection ou une condition de sélection doit être défini pour chaque entrée de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ca99c-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ca99c-122">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="ca99c-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="ca99c-123">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="ca99c-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="ca99c-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ca99c-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ca99c-125">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ca99c-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca99c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca99c-126">See Also</span></span>

[<span data-ttu-id="ca99c-127">Élément EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="ca99c-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ca99c-128">Affichage de contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="ca99c-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ca99c-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca99c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
