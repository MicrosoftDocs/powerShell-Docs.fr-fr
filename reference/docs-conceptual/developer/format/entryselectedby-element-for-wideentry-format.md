---
title: Élément EntrySelectedBy pour WideEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ba0a776839c39d753d12859335388c5326639fd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774080"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="ff1f6-102">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="ff1f6-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="ff1f6-103">Définit les types .NET qui utilisent cette définition de la vue étendue ou de la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="ff1f6-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) EntrySelectedBy, élément pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff1f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff1f6-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff1f6-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ff1f6-106">Attributes and Elements</span></span>

<span data-ttu-id="ff1f6-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff1f6-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="ff1f6-108">Attributes</span></span>

<span data-ttu-id="ff1f6-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff1f6-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ff1f6-110">Child Elements</span></span>

|<span data-ttu-id="ff1f6-111">Élément</span><span class="sxs-lookup"><span data-stu-id="ff1f6-111">Element</span></span>|<span data-ttu-id="ff1f6-112">Description</span><span class="sxs-lookup"><span data-stu-id="ff1f6-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff1f6-113">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f6-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ff1f6-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ff1f6-115">Définit la condition qui doit exister pour cette définition de vue étendue à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="ff1f6-116">Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f6-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ff1f6-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ff1f6-118">Spécifie un ensemble de types .NET qui utilisent cette définition de vue étendue.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="ff1f6-119">TypeName, élément pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="ff1f6-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="ff1f6-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ff1f6-121">Spécifie un type .NET qui utilise cette définition de vue étendue.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ff1f6-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ff1f6-122">Parent Elements</span></span>

|<span data-ttu-id="ff1f6-123">Élément</span><span class="sxs-lookup"><span data-stu-id="ff1f6-123">Element</span></span>|<span data-ttu-id="ff1f6-124">Description</span><span class="sxs-lookup"><span data-stu-id="ff1f6-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff1f6-125">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f6-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="ff1f6-126">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ff1f6-127">Notes</span><span class="sxs-lookup"><span data-stu-id="ff1f6-127">Remarks</span></span>

<span data-ttu-id="ff1f6-128">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition de vue étendue.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="ff1f6-129">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="ff1f6-130">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou qu’une valeur de propriété ou une valeur de script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="ff1f6-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="ff1f6-131">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ff1f6-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ff1f6-132">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ff1f6-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff1f6-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff1f6-133">See Also</span></span>

[<span data-ttu-id="ff1f6-134">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f6-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="ff1f6-135">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f6-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ff1f6-136">Élément SelectionSetName pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f6-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ff1f6-137">TypeName, élément pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="ff1f6-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="ff1f6-138">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="ff1f6-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ff1f6-139">Définition de conditions pour l’affichage de données</span><span class="sxs-lookup"><span data-stu-id="ff1f6-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ff1f6-140">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff1f6-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
