---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour Types (Format)
description: TypeName, élément pour Types (Format)
ms.openlocfilehash: c656b8e7e5877b72ff2164e5b417857273cada61
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664617"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="055c6-103">TypeName, élément pour Types (Format)</span><span class="sxs-lookup"><span data-stu-id="055c6-103">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="055c6-104">Spécifie le type .NET d’un objet qui appartient au jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="055c6-104">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="055c6-105">Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) types élément (format) TypeName élément de types (format)</span><span class="sxs-lookup"><span data-stu-id="055c6-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="055c6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="055c6-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="055c6-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="055c6-107">Attributes and Elements</span></span>

<span data-ttu-id="055c6-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="055c6-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="055c6-109">Au moins un `TypeName` élément doit être inclus dans le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="055c6-109">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="055c6-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="055c6-110">Attributes</span></span>

<span data-ttu-id="055c6-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="055c6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="055c6-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="055c6-112">Child Elements</span></span>

<span data-ttu-id="055c6-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="055c6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="055c6-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="055c6-114">Parent Elements</span></span>

|<span data-ttu-id="055c6-115">Élément</span><span class="sxs-lookup"><span data-stu-id="055c6-115">Element</span></span>|<span data-ttu-id="055c6-116">Description</span><span class="sxs-lookup"><span data-stu-id="055c6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="055c6-117">Élément types (format)</span><span class="sxs-lookup"><span data-stu-id="055c6-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="055c6-118">Définit les objets .NET qui se trouvent dans le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="055c6-118">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="055c6-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="055c6-119">Text Value</span></span>

<span data-ttu-id="055c6-120">Spécifiez le nom qualifié complet du type .NET.</span><span class="sxs-lookup"><span data-stu-id="055c6-120">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="055c6-121">Notes</span><span class="sxs-lookup"><span data-stu-id="055c6-121">Remarks</span></span>

<span data-ttu-id="055c6-122">Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="055c6-122">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="055c6-123">Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.</span><span class="sxs-lookup"><span data-stu-id="055c6-123">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="055c6-124">Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="055c6-124">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="055c6-125">Dans ce cas, l' `SelectionSetName` élément enfant de l' `ViewSelectedBy` élément de la vue spécifie le jeu.</span><span class="sxs-lookup"><span data-stu-id="055c6-125">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="055c6-126">Toutefois, différentes entrées d’une vue peuvent également spécifier un jeu de sélection qui s’applique uniquement à cette entrée de la vue.</span><span class="sxs-lookup"><span data-stu-id="055c6-126">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="055c6-127">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="055c6-127">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="055c6-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="055c6-128">Example</span></span>

<span data-ttu-id="055c6-129">L’exemple suivant montre un `SelectionSet` élément qui définit quatre types .net.</span><span class="sxs-lookup"><span data-stu-id="055c6-129">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="055c6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="055c6-130">See Also</span></span>

[<span data-ttu-id="055c6-131">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="055c6-131">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="055c6-132">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="055c6-132">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="055c6-133">SelectionSets, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="055c6-133">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="055c6-134">Élément types (format)</span><span class="sxs-lookup"><span data-stu-id="055c6-134">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="055c6-135">Écriture d’un fichier de mise en forme Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="055c6-135">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
