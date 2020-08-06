---
title: Élément EntrySelectedBy pour CustomEntry pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4d4900cefb0d499397fc9dff7e037ce0a541f72f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783685"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="47468-102">EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="47468-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="47468-103">Définit les types .NET qui utilisent cette entrée personnalisée ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="47468-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="47468-104">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour l’élément View (format) EntrySelectedBy pour CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="47468-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="47468-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47468-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47468-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="47468-106">Attributes and Elements</span></span>

<span data-ttu-id="47468-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="47468-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="47468-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="47468-108">Attributes</span></span>

<span data-ttu-id="47468-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="47468-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47468-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="47468-110">Child Elements</span></span>

|<span data-ttu-id="47468-111">Élément</span><span class="sxs-lookup"><span data-stu-id="47468-111">Element</span></span>|<span data-ttu-id="47468-112">Description</span><span class="sxs-lookup"><span data-stu-id="47468-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47468-113">Élément SelectionCondition pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47468-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="47468-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="47468-114">Optional element.</span></span><br /><br /> <span data-ttu-id="47468-115">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="47468-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="47468-116">Élément SelectionSetName pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47468-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="47468-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="47468-117">Optional element.</span></span><br /><br /> <span data-ttu-id="47468-118">Spécifie un ensemble de types .NET qui utilisent cette définition de l’affichage de contrôle.</span><span class="sxs-lookup"><span data-stu-id="47468-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="47468-119">Élément TypeName pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47468-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="47468-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="47468-120">Optional element.</span></span><br /><br /> <span data-ttu-id="47468-121">Spécifie un type .NET qui utilise cette définition de l’affichage de contrôle.</span><span class="sxs-lookup"><span data-stu-id="47468-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="47468-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="47468-122">Parent Elements</span></span>

|<span data-ttu-id="47468-123">Élément</span><span class="sxs-lookup"><span data-stu-id="47468-123">Element</span></span>|<span data-ttu-id="47468-124">Description</span><span class="sxs-lookup"><span data-stu-id="47468-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47468-125">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="47468-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="47468-126">Définit les contrôles utilisés par des objets .NET spécifiques.</span><span class="sxs-lookup"><span data-stu-id="47468-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47468-127">Notes</span><span class="sxs-lookup"><span data-stu-id="47468-127">Remarks</span></span>

<span data-ttu-id="47468-128">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="47468-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="47468-129">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="47468-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="47468-130">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour l’entrée à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="47468-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="47468-131">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="47468-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="47468-132">Pour plus d’informations sur les composants d’un affichage de contrôle personnalisé, consultez [vue de contrôle personnalisé](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="47468-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="47468-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47468-133">See Also</span></span>

[<span data-ttu-id="47468-134">Élément SelectionCondition pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47468-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="47468-135">Élément SelectionSetName pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47468-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="47468-136">Élément TypeName pour EntrySelectedBy pour CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47468-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="47468-137">Élément CustomEntry pour CustomEntries pour View (format)</span><span class="sxs-lookup"><span data-stu-id="47468-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="47468-138">Affichage de contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="47468-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="47468-139">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="47468-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
