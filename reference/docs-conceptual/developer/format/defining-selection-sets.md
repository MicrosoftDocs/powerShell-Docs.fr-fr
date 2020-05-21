---
title: Définition des jeux de sélection | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 95eeb037b3b9190fec1212a68029624993f3fd9f
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692284"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="d0914-102">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="d0914-102">Defining Selection Sets</span></span>

<span data-ttu-id="d0914-103">Lorsque vous créez plusieurs vues et contrôles, vous pouvez définir des ensembles d’objets appelés jeux de sélection.</span><span class="sxs-lookup"><span data-stu-id="d0914-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="d0914-104">Un jeu de sélection vous permet de définir les objets une seule fois, sans avoir à les définir à plusieurs reprises pour chaque vue ou contrôle.</span><span class="sxs-lookup"><span data-stu-id="d0914-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="d0914-105">En règle générale, les jeux de sélection sont utilisés lorsque vous avez un ensemble d’objets .NET associés.</span><span class="sxs-lookup"><span data-stu-id="d0914-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="d0914-106">Par exemple, le `FileSystem` fichier de mise en forme (FileSystem. format. ps1xml) définit un jeu de sélection des types de système de fichiers utilisés par plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="d0914-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="d0914-107">Où les jeux de sélection sont définis et référencés</span><span class="sxs-lookup"><span data-stu-id="d0914-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="d0914-108">Vous définissez des jeux de sélection dans le cadre des données communes qui peuvent être utilisées par toutes les vues et tous les contrôles définis dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d0914-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="d0914-109">L’exemple suivant montre comment définir trois jeux de sélection.</span><span class="sxs-lookup"><span data-stu-id="d0914-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="d0914-110">Vous pouvez référencer un jeu de sélection des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="d0914-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="d0914-111">Chaque vue a un `ViewSelectedBy` élément qui définit les objets qui sont affichés à l’aide de la vue.</span><span class="sxs-lookup"><span data-stu-id="d0914-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="d0914-112">L' `ViewSelectedBy` élément a un `SelectionSetName` élément enfant qui spécifie le jeu de sélection utilisé par toutes les définitions de la vue.</span><span class="sxs-lookup"><span data-stu-id="d0914-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="d0914-113">Il n’existe aucune restriction sur le nombre de jeux de sélection que vous pouvez référencer à partir d’une vue.</span><span class="sxs-lookup"><span data-stu-id="d0914-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="d0914-114">Dans chaque définition d’une vue ou d’un contrôle, l' `EntrySelectedBy` élément définit les objets qui sont affichés à l’aide de cette définition.</span><span class="sxs-lookup"><span data-stu-id="d0914-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="d0914-115">En général, une vue ou un contrôle n’a qu’une seule définition, de sorte que les objets sont définis par l' `ViewSelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="d0914-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="d0914-116">L' `EntrySelectedBy` élément de la définition a un `SelectionSetName` élément enfant qui spécifie le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="d0914-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="d0914-117">Si vous spécifiez le jeu de sélection pour une définition, vous ne pouvez pas spécifier d’autres éléments enfants de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="d0914-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="d0914-118">Dans chaque définition d’une vue ou d’un contrôle, l' `SelectionCondition` élément peut être utilisé pour spécifier une condition lorsque la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d0914-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="d0914-119">L' `SelectionCondition` élément a un `SelectionSetName` élément enfant qui spécifie le jeu de sélection qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="d0914-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="d0914-120">La condition est déclenchée lorsque l’un des objets définis dans le jeu de sélection est affiché.</span><span class="sxs-lookup"><span data-stu-id="d0914-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="d0914-121">Pour plus d’informations sur la façon de définir ces conditions, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d0914-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="d0914-122">Exemple de jeu de sélection</span><span class="sxs-lookup"><span data-stu-id="d0914-122">Selection Set Example</span></span>

<span data-ttu-id="d0914-123">L’exemple suivant montre un jeu de sélection provenant directement du fichier de `FileSystem` mise en forme fourni par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0914-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="d0914-124">Pour plus d’informations sur les autres fichiers de mise en forme Windows PowerShell, consultez [fichiers de mise en forme Windows PowerShell](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="d0914-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="d0914-125">Le jeu de sélection précédent est référencé dans l' `ViewSelectedBy` élément d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="d0914-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="d0914-126">Éléments XML</span><span class="sxs-lookup"><span data-stu-id="d0914-126">XML Elements</span></span>

 <span data-ttu-id="d0914-127">Il n’existe aucune limite au nombre de jeux de sélection que vous pouvez définir.</span><span class="sxs-lookup"><span data-stu-id="d0914-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="d0914-128">Les éléments XML suivants sont utilisés pour créer un jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="d0914-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="d0914-129">L’élément [SelectionSets](./selectionsets-element-format.md) définit les jeux d’objets .net référencés par les vues et les contrôles du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d0914-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="d0914-130">L’élément [SelectionSet](./selectionset-element-format.md) définit un ensemble unique d’objets .net.</span><span class="sxs-lookup"><span data-stu-id="d0914-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="d0914-131">L’élément [Name](./name-element-for-selectionset-format.md) spécifie le nom utilisé pour référencer le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="d0914-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="d0914-132">L’élément [types](./types-element-for-selectionset-format.md) spécifie les types .net des objets du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="d0914-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="d0914-133">(Dans les fichiers de mise en forme, les objets sont spécifiés par leur type .NET.)</span><span class="sxs-lookup"><span data-stu-id="d0914-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="d0914-134">Les éléments XML suivants sont utilisés pour spécifier un jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="d0914-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="d0914-135">L’élément suivant spécifie le jeu de sélection à utiliser dans toutes les définitions de la vue :</span><span class="sxs-lookup"><span data-stu-id="d0914-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

  - [<span data-ttu-id="d0914-136">SelectionSetName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

  - [<span data-ttu-id="d0914-137">SelectionSetName, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="d0914-138">Les éléments suivants spécifient le jeu de sélection utilisé par une définition de vue unique :</span><span class="sxs-lookup"><span data-stu-id="d0914-138">The following elements specify the selection set used by a single view definition:</span></span>

  - [<span data-ttu-id="d0914-139">SelectionSetName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="d0914-140">SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="d0914-141">SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="d0914-142">SelectionSetName, élément pour EntrySelectedBy pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="d0914-143">Les éléments suivants spécifient le jeu de sélection utilisé par les définitions courantes et de contrôle d’affichage :</span><span class="sxs-lookup"><span data-stu-id="d0914-143">The following elements specify the selection set used by common and view control definitions:</span></span>

  - [<span data-ttu-id="d0914-144">SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [<span data-ttu-id="d0914-145">SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="d0914-146">Les éléments suivants spécifient le jeu de sélection utilisé lorsque vous définissez l’objet à développer :</span><span class="sxs-lookup"><span data-stu-id="d0914-146">The following elements specify the selection set used when you define which object to expand:</span></span>

  - [<span data-ttu-id="d0914-147">SelectionSetName, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="d0914-148">Les éléments suivants spécifient le jeu de sélection utilisé par les conditions de sélection.</span><span class="sxs-lookup"><span data-stu-id="d0914-148">The following elements specify the selection set used by selection conditions.</span></span>

  - [<span data-ttu-id="d0914-149">SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="d0914-150">SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [<span data-ttu-id="d0914-151">SelectionSetName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [<span data-ttu-id="d0914-152">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [<span data-ttu-id="d0914-153">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [<span data-ttu-id="d0914-154">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="d0914-155">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [<span data-ttu-id="d0914-156">SelectionSetName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0914-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="d0914-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0914-157">See Also</span></span>

[<span data-ttu-id="d0914-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="d0914-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="d0914-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="d0914-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="d0914-160">Nom</span><span class="sxs-lookup"><span data-stu-id="d0914-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="d0914-161">Types</span><span class="sxs-lookup"><span data-stu-id="d0914-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="d0914-162">Fichiers de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0914-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="d0914-163">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="d0914-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d0914-164">Écriture d’un fichier de mise en forme et de types PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0914-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
