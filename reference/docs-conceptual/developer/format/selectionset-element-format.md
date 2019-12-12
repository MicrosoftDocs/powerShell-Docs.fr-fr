---
title: Élément SelectionSet (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368378"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="5b430-102">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="5b430-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="5b430-103">Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="5b430-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="5b430-104">Élément de configuration (format) élément SelectionSets (format) SelectionSet, élément (format)</span><span class="sxs-lookup"><span data-stu-id="5b430-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b430-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b430-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b430-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5b430-106">Attributes and Elements</span></span>

<span data-ttu-id="5b430-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSet`.</span><span class="sxs-lookup"><span data-stu-id="5b430-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="5b430-108">Chaque jeu de sélection doit avoir un nom et doit spécifier les objets .NET de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="5b430-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b430-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="5b430-109">Attributes</span></span>

<span data-ttu-id="5b430-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5b430-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b430-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5b430-111">Child Elements</span></span>

|<span data-ttu-id="5b430-112">Élément</span><span class="sxs-lookup"><span data-stu-id="5b430-112">Element</span></span>|<span data-ttu-id="5b430-113">Description</span><span class="sxs-lookup"><span data-stu-id="5b430-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b430-114">Élément Name pour SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="5b430-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="5b430-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="5b430-115">Required element.</span></span><br /><br /> <span data-ttu-id="5b430-116">Spécifie le nom utilisé pour référencer le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="5b430-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="5b430-117">Élément types (format)</span><span class="sxs-lookup"><span data-stu-id="5b430-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="5b430-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="5b430-118">Required element.</span></span><br /><br /> <span data-ttu-id="5b430-119">Définit les objets .NET qui se trouvent dans le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="5b430-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5b430-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5b430-120">Parent Elements</span></span>

|<span data-ttu-id="5b430-121">Élément</span><span class="sxs-lookup"><span data-stu-id="5b430-121">Element</span></span>|<span data-ttu-id="5b430-122">Description</span><span class="sxs-lookup"><span data-stu-id="5b430-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b430-123">Format de l’élément SelectionSets</span><span class="sxs-lookup"><span data-stu-id="5b430-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="5b430-124">Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="5b430-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5b430-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="5b430-125">Remarks</span></span>

<span data-ttu-id="5b430-126">Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="5b430-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="5b430-127">Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.</span><span class="sxs-lookup"><span data-stu-id="5b430-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="5b430-128">Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme ou des définitions des vues.</span><span class="sxs-lookup"><span data-stu-id="5b430-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="5b430-129">Dans ce cas, l' `SelectionSetName` élément enfant des éléments `ViewSelectedBy` et `EntrySelectedBy` spécifie le jeu à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5b430-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="5b430-130">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5b430-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="5b430-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b430-131">Example</span></span>

<span data-ttu-id="5b430-132">L’exemple suivant montre un élément `SelectionSet` qui définit quatre types .NET.</span><span class="sxs-lookup"><span data-stu-id="5b430-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5b430-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b430-133">See Also</span></span>

[<span data-ttu-id="5b430-134">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="5b430-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="5b430-135">Élément Name de SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="5b430-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="5b430-136">Élément SelectionSets (format)</span><span class="sxs-lookup"><span data-stu-id="5b430-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="5b430-137">Élément types (format)</span><span class="sxs-lookup"><span data-stu-id="5b430-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="5b430-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b430-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
