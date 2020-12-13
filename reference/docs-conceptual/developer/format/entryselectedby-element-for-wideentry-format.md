---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour WideEntry (Format)
description: EntrySelectedBy, élément pour WideEntry (Format)
ms.openlocfilehash: 246a1967300ab0551f376c4799deac275068308c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660249"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="cef3b-103">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cef3b-103">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="cef3b-104">Définit les types .NET qui utilisent cette définition de la vue étendue ou de la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="cef3b-104">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="cef3b-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) EntrySelectedBy, élément pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="cef3b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cef3b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cef3b-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cef3b-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cef3b-107">Attributes and Elements</span></span>

<span data-ttu-id="cef3b-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="cef3b-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cef3b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="cef3b-109">Attributes</span></span>

<span data-ttu-id="cef3b-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cef3b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cef3b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cef3b-111">Child Elements</span></span>

|<span data-ttu-id="cef3b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="cef3b-112">Element</span></span>|<span data-ttu-id="cef3b-113">Description</span><span class="sxs-lookup"><span data-stu-id="cef3b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cef3b-114">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="cef3b-114">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="cef3b-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cef3b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="cef3b-116">Définit la condition qui doit exister pour cette définition de vue étendue à utiliser.</span><span class="sxs-lookup"><span data-stu-id="cef3b-116">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="cef3b-117">Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="cef3b-117">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="cef3b-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cef3b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="cef3b-119">Spécifie un ensemble de types .NET qui utilisent cette définition de vue étendue.</span><span class="sxs-lookup"><span data-stu-id="cef3b-119">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="cef3b-120">TypeName, élément pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cef3b-120">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="cef3b-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cef3b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="cef3b-122">Spécifie un type .NET qui utilise cette définition de vue étendue.</span><span class="sxs-lookup"><span data-stu-id="cef3b-122">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cef3b-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cef3b-123">Parent Elements</span></span>

|<span data-ttu-id="cef3b-124">Élément</span><span class="sxs-lookup"><span data-stu-id="cef3b-124">Element</span></span>|<span data-ttu-id="cef3b-125">Description</span><span class="sxs-lookup"><span data-stu-id="cef3b-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cef3b-126">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="cef3b-126">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="cef3b-127">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="cef3b-127">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cef3b-128">Notes</span><span class="sxs-lookup"><span data-stu-id="cef3b-128">Remarks</span></span>

<span data-ttu-id="cef3b-129">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition de vue étendue.</span><span class="sxs-lookup"><span data-stu-id="cef3b-129">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="cef3b-130">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="cef3b-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="cef3b-131">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou une valeur de script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="cef3b-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="cef3b-132">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cef3b-132">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="cef3b-133">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="cef3b-133">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cef3b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cef3b-134">See Also</span></span>

[<span data-ttu-id="cef3b-135">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="cef3b-135">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="cef3b-136">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="cef3b-136">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="cef3b-137">Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="cef3b-137">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="cef3b-138">TypeName, élément pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cef3b-138">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="cef3b-139">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="cef3b-139">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="cef3b-140">Définition de conditions pour l’affichage de données</span><span class="sxs-lookup"><span data-stu-id="cef3b-140">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cef3b-141">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="cef3b-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
