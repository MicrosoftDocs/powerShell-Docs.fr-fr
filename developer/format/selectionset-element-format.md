---
title: Élément SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861155"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="cfd2a-102">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="cfd2a-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="cfd2a-103">Définit un ensemble d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="cfd2a-104">Configuration élément (Format) SelectionSets (Format) SelectionSet élément (Format)</span><span class="sxs-lookup"><span data-stu-id="cfd2a-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cfd2a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfd2a-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cfd2a-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="cfd2a-106">Attributes and Elements</span></span>

<span data-ttu-id="cfd2a-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSet` élément.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="cfd2a-108">Chaque jeu de sélection doit avoir un nom, et il doit spécifier les objets .NET de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="cfd2a-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="cfd2a-109">Attributes</span></span>

<span data-ttu-id="cfd2a-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cfd2a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cfd2a-111">Child Elements</span></span>

|<span data-ttu-id="cfd2a-112">Élément</span><span class="sxs-lookup"><span data-stu-id="cfd2a-112">Element</span></span>|<span data-ttu-id="cfd2a-113">Description</span><span class="sxs-lookup"><span data-stu-id="cfd2a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cfd2a-114">Name, élément pour SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="cfd2a-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="cfd2a-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-115">Required element.</span></span><br /><br /> <span data-ttu-id="cfd2a-116">Spécifie le nom utilisé pour référencer le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="cfd2a-117">Élément de types (Format)</span><span class="sxs-lookup"><span data-stu-id="cfd2a-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="cfd2a-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-118">Required element.</span></span><br /><br /> <span data-ttu-id="cfd2a-119">Définit les objets .NET qui sont définies dans la sélection.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cfd2a-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cfd2a-120">Parent Elements</span></span>

|<span data-ttu-id="cfd2a-121">Élément</span><span class="sxs-lookup"><span data-stu-id="cfd2a-121">Element</span></span>|<span data-ttu-id="cfd2a-122">Description</span><span class="sxs-lookup"><span data-stu-id="cfd2a-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cfd2a-123">Format d’élément de SelectionSets</span><span class="sxs-lookup"><span data-stu-id="cfd2a-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="cfd2a-124">Définit les jeux d’objets .NET qui peuvent être utilisées par toutes les vues du fichier de mise en forme courants.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cfd2a-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="cfd2a-125">Remarks</span></span>

<span data-ttu-id="cfd2a-126">Vous pouvez utiliser des jeux de sélection lorsque vous avez un ensemble d’objets connexes que vous souhaitez faire référence à l’aide d’un nom unique, comme un ensemble d’objets qui sont liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="cfd2a-127">Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom de la sélection définie au lieu de répertorier tous les objets au sein de chaque vue.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="cfd2a-128">Ensembles communs de sélection sont spécifiés par leur nom lorsque vous définissez les vues du fichier de mise en forme ou les définitions des vues.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="cfd2a-129">Dans ce cas, le `SelectionSetName` élément enfant de le `ViewSelectedBy` et `EntrySelectedBy` éléments spécifie le jeu à utiliser.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="cfd2a-130">Pour plus d’informations sur les jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="cfd2a-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="cfd2a-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="cfd2a-131">Example</span></span>

<span data-ttu-id="cfd2a-132">L’exemple suivant montre un `SelectionSet` élément qui définit les quatre types de .NET.</span><span class="sxs-lookup"><span data-stu-id="cfd2a-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cfd2a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfd2a-133">See Also</span></span>

[<span data-ttu-id="cfd2a-134">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="cfd2a-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="cfd2a-135">Name, élément de SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="cfd2a-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="cfd2a-136">Élément SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="cfd2a-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="cfd2a-137">Élément de types (Format)</span><span class="sxs-lookup"><span data-stu-id="cfd2a-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="cfd2a-138">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfd2a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
