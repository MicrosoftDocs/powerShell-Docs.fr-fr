---
title: Élément EntrySelectedBy pour WideEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363328"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="e3ac8-102">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e3ac8-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="e3ac8-103">Définit les types .NET qui utilisent cette définition de la vue étendue ou de la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="e3ac8-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) EntrySelectedBy, élément pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e3ac8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3ac8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3ac8-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3ac8-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e3ac8-106">Attributes and Elements</span></span>

<span data-ttu-id="e3ac8-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3ac8-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="e3ac8-108">Attributes</span></span>

<span data-ttu-id="e3ac8-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3ac8-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e3ac8-110">Child Elements</span></span>

|<span data-ttu-id="e3ac8-111">Élément</span><span class="sxs-lookup"><span data-stu-id="e3ac8-111">Element</span></span>|<span data-ttu-id="e3ac8-112">Description</span><span class="sxs-lookup"><span data-stu-id="e3ac8-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3ac8-113">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e3ac8-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="e3ac8-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e3ac8-115">Définit la condition qui doit exister pour cette définition de vue étendue à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="e3ac8-116">Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e3ac8-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="e3ac8-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e3ac8-118">Spécifie un ensemble de types .NET qui utilisent cette définition de vue étendue.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="e3ac8-119">Élément TypeName pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e3ac8-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="e3ac8-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e3ac8-121">Spécifie un type .NET qui utilise cette définition de vue étendue.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e3ac8-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e3ac8-122">Parent Elements</span></span>

|<span data-ttu-id="e3ac8-123">Élément</span><span class="sxs-lookup"><span data-stu-id="e3ac8-123">Element</span></span>|<span data-ttu-id="e3ac8-124">Description</span><span class="sxs-lookup"><span data-stu-id="e3ac8-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3ac8-125">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e3ac8-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="e3ac8-126">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e3ac8-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="e3ac8-127">Remarks</span></span>

<span data-ttu-id="e3ac8-128">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition de vue étendue.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="e3ac8-129">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="e3ac8-130">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou de script spécifique prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="e3ac8-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="e3ac8-131">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e3ac8-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e3ac8-132">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e3ac8-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3ac8-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3ac8-133">See Also</span></span>

[<span data-ttu-id="e3ac8-134">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e3ac8-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="e3ac8-135">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e3ac8-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e3ac8-136">Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e3ac8-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e3ac8-137">Élément TypeName pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e3ac8-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="e3ac8-138">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="e3ac8-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e3ac8-139">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="e3ac8-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e3ac8-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3ac8-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
