---
ms.date: 09/13/2016
ms.topic: reference
title: Définition de jeux de sélections
description: Définition de jeux de sélections
ms.openlocfilehash: d709a368a45623d56fdbf4e98a11a5e5f8a193fa
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648253"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="417ad-103">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="417ad-103">Defining Selection Sets</span></span>

<span data-ttu-id="417ad-104">Lorsque vous créez plusieurs vues et contrôles, vous pouvez définir des ensembles d’objets appelés jeux de sélection.</span><span class="sxs-lookup"><span data-stu-id="417ad-104">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="417ad-105">Un jeu de sélection vous permet de définir les objets une seule fois, sans avoir à les définir à plusieurs reprises pour chaque vue ou contrôle.</span><span class="sxs-lookup"><span data-stu-id="417ad-105">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="417ad-106">En règle générale, les jeux de sélection sont utilisés lorsque vous avez un ensemble d’objets .NET associés.</span><span class="sxs-lookup"><span data-stu-id="417ad-106">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="417ad-107">Par exemple, le `FileSystem` fichier de mise en forme (FileSystem.format.ps1XML) définit un jeu de sélection des types de système de fichiers utilisés par plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="417ad-107">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="417ad-108">Où les jeux de sélection sont définis et référencés</span><span class="sxs-lookup"><span data-stu-id="417ad-108">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="417ad-109">Vous définissez des jeux de sélection dans le cadre des données communes qui peuvent être utilisées par toutes les vues et tous les contrôles définis dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="417ad-109">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="417ad-110">L’exemple suivant montre comment définir trois jeux de sélection.</span><span class="sxs-lookup"><span data-stu-id="417ad-110">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="417ad-111">Vous pouvez référencer un jeu de sélection des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="417ad-111">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="417ad-112">Chaque vue a un `ViewSelectedBy` élément qui définit les objets qui sont affichés à l’aide de la vue.</span><span class="sxs-lookup"><span data-stu-id="417ad-112">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="417ad-113">L' `ViewSelectedBy` élément a un `SelectionSetName` élément enfant qui spécifie le jeu de sélection utilisé par toutes les définitions de la vue.</span><span class="sxs-lookup"><span data-stu-id="417ad-113">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="417ad-114">Il n’existe aucune restriction sur le nombre de jeux de sélection que vous pouvez référencer à partir d’une vue.</span><span class="sxs-lookup"><span data-stu-id="417ad-114">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="417ad-115">Dans chaque définition d’une vue ou d’un contrôle, l' `EntrySelectedBy` élément définit les objets qui sont affichés à l’aide de cette définition.</span><span class="sxs-lookup"><span data-stu-id="417ad-115">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="417ad-116">En général, une vue ou un contrôle n’a qu’une seule définition, de sorte que les objets sont définis par l' `ViewSelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="417ad-116">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="417ad-117">L' `EntrySelectedBy` élément de la définition a un `SelectionSetName` élément enfant qui spécifie le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="417ad-117">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="417ad-118">Si vous spécifiez le jeu de sélection pour une définition, vous ne pouvez pas spécifier d’autres éléments enfants de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="417ad-118">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="417ad-119">Dans chaque définition d’une vue ou d’un contrôle, l' `SelectionCondition` élément peut être utilisé pour spécifier une condition lorsque la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="417ad-119">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="417ad-120">L' `SelectionCondition` élément a un `SelectionSetName` élément enfant qui spécifie le jeu de sélection qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="417ad-120">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="417ad-121">La condition est déclenchée lorsque l’un des objets définis dans le jeu de sélection est affiché.</span><span class="sxs-lookup"><span data-stu-id="417ad-121">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="417ad-122">Pour plus d’informations sur la façon de définir ces conditions, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="417ad-122">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="417ad-123">Exemple de jeu de sélection</span><span class="sxs-lookup"><span data-stu-id="417ad-123">Selection Set Example</span></span>

<span data-ttu-id="417ad-124">L’exemple suivant montre un jeu de sélection provenant directement du fichier de `FileSystem` mise en forme fourni par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="417ad-124">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="417ad-125">Pour plus d’informations sur les autres fichiers de mise en forme Windows PowerShell, consultez [fichiers de mise en forme Windows PowerShell](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="417ad-125">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="417ad-126">Le jeu de sélection précédent est référencé dans l' `ViewSelectedBy` élément d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="417ad-126">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="417ad-127">Éléments XML</span><span class="sxs-lookup"><span data-stu-id="417ad-127">XML Elements</span></span>

 <span data-ttu-id="417ad-128">Il n’existe aucune limite au nombre de jeux de sélection que vous pouvez définir.</span><span class="sxs-lookup"><span data-stu-id="417ad-128">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="417ad-129">Les éléments XML suivants sont utilisés pour créer un jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="417ad-129">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="417ad-130">L’élément [SelectionSets](./selectionsets-element-format.md) définit les jeux d’objets .net référencés par les vues et les contrôles du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="417ad-130">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="417ad-131">L’élément [SelectionSet](./selectionset-element-format.md) définit un ensemble unique d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="417ad-131">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="417ad-132">L’élément [Name](./name-element-for-selectionset-format.md) spécifie le nom utilisé pour référencer le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="417ad-132">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="417ad-133">L’élément [types](./types-element-for-selectionset-format.md) spécifie les types .net des objets du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="417ad-133">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="417ad-134">(Dans les fichiers de mise en forme, les objets sont spécifiés par leur type .NET.)</span><span class="sxs-lookup"><span data-stu-id="417ad-134">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="417ad-135">Les éléments XML suivants sont utilisés pour spécifier un jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="417ad-135">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="417ad-136">L’élément suivant spécifie le jeu de sélection à utiliser dans toutes les définitions de la vue :</span><span class="sxs-lookup"><span data-stu-id="417ad-136">The following element specifies the selection set to use in all the definitions of the view:</span></span>

  - [<span data-ttu-id="417ad-137">SelectionSetName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-137">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

  - [<span data-ttu-id="417ad-138">SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-138">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="417ad-139">Les éléments suivants spécifient le jeu de sélection utilisé par une définition de vue unique :</span><span class="sxs-lookup"><span data-stu-id="417ad-139">The following elements specify the selection set used by a single view definition:</span></span>

  - [<span data-ttu-id="417ad-140">SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="417ad-141">SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-141">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="417ad-142">SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-142">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="417ad-143">SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-143">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="417ad-144">Les éléments suivants spécifient le jeu de sélection utilisé par les définitions courantes et de contrôle d’affichage :</span><span class="sxs-lookup"><span data-stu-id="417ad-144">The following elements specify the selection set used by common and view control definitions:</span></span>

  - [<span data-ttu-id="417ad-145">SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-145">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [<span data-ttu-id="417ad-146">SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-146">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="417ad-147">Les éléments suivants spécifient le jeu de sélection utilisé lorsque vous définissez l’objet à développer :</span><span class="sxs-lookup"><span data-stu-id="417ad-147">The following elements specify the selection set used when you define which object to expand:</span></span>

  - [<span data-ttu-id="417ad-148">SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-148">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="417ad-149">Les éléments suivants spécifient le jeu de sélection utilisé par les conditions de sélection.</span><span class="sxs-lookup"><span data-stu-id="417ad-149">The following elements specify the selection set used by selection conditions.</span></span>

  - [<span data-ttu-id="417ad-150">SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-150">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="417ad-151">SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-151">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [<span data-ttu-id="417ad-152">SelectionSetName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-152">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [<span data-ttu-id="417ad-153">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [<span data-ttu-id="417ad-154">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [<span data-ttu-id="417ad-155">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="417ad-156">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-156">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [<span data-ttu-id="417ad-157">SelectionSetName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="417ad-157">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="417ad-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="417ad-158">See Also</span></span>

[<span data-ttu-id="417ad-159">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="417ad-159">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="417ad-160">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="417ad-160">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="417ad-161">Nom</span><span class="sxs-lookup"><span data-stu-id="417ad-161">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="417ad-162">Types</span><span class="sxs-lookup"><span data-stu-id="417ad-162">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="417ad-163">Fichiers de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="417ad-163">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="417ad-164">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="417ad-164">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="417ad-165">Écriture d’un fichier de mise en forme et de types PowerShell</span><span class="sxs-lookup"><span data-stu-id="417ad-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
