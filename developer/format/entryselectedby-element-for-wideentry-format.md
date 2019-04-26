---
title: Élément EntrySelectedBy pour WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066173"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="cb96e-102">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb96e-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="cb96e-103">Définit les types .NET qui utilisent cette définition de l’affichage plus large ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="cb96e-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="cb96e-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément de configuration pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb96e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cb96e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb96e-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cb96e-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="cb96e-106">Attributes and Elements</span></span>

<span data-ttu-id="cb96e-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="cb96e-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cb96e-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="cb96e-108">Attributes</span></span>

<span data-ttu-id="cb96e-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="cb96e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cb96e-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cb96e-110">Child Elements</span></span>

|<span data-ttu-id="cb96e-111">Élément</span><span class="sxs-lookup"><span data-stu-id="cb96e-111">Element</span></span>|<span data-ttu-id="cb96e-112">Description</span><span class="sxs-lookup"><span data-stu-id="cb96e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb96e-113">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb96e-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="cb96e-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cb96e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="cb96e-115">Définit la condition qui doit exister pour cette définition d’affichage plus large à utiliser.</span><span class="sxs-lookup"><span data-stu-id="cb96e-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="cb96e-116">Élément SelectionSetName pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb96e-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="cb96e-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cb96e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="cb96e-118">Spécifie un ensemble de types .NET qui utilisent cette définition d’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="cb96e-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="cb96e-119">Élément TypeName pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb96e-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="cb96e-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cb96e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="cb96e-121">Spécifie un type .NET qui utilise cette définition d’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="cb96e-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cb96e-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cb96e-122">Parent Elements</span></span>

|<span data-ttu-id="cb96e-123">Élément</span><span class="sxs-lookup"><span data-stu-id="cb96e-123">Element</span></span>|<span data-ttu-id="cb96e-124">Description</span><span class="sxs-lookup"><span data-stu-id="cb96e-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb96e-125">Élément WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb96e-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="cb96e-126">Fournit une définition de l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="cb96e-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cb96e-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="cb96e-127">Remarks</span></span>

<span data-ttu-id="cb96e-128">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour une définition d’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="cb96e-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="cb96e-129">Il n’existe aucune limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="cb96e-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="cb96e-130">Conditions de sélection permettent de définir une condition qui doit exister pour la définition à utiliser, par exemple quand un objet possède une propriété spécifique, ou qui a pour résultat une valeur de propriété spécifique ou la valeur de script `true`.</span><span class="sxs-lookup"><span data-stu-id="cb96e-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="cb96e-131">Pour plus d’informations sur les conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cb96e-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="cb96e-132">Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="cb96e-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb96e-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb96e-133">See Also</span></span>

[<span data-ttu-id="cb96e-134">Élément WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb96e-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="cb96e-135">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb96e-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="cb96e-136">Élément SelectionSetName pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb96e-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="cb96e-137">Élément TypeName pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb96e-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="cb96e-138">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="cb96e-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="cb96e-139">Définition des Conditions pour l’affichage des données</span><span class="sxs-lookup"><span data-stu-id="cb96e-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cb96e-140">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb96e-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
