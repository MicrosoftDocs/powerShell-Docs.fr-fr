---
title: Élément TypeName pour les types (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 40fad73c66124d6c3b0d969b4268713a492c963a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772533"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="72d06-102">TypeName, élément pour Types (Format)</span><span class="sxs-lookup"><span data-stu-id="72d06-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="72d06-103">Spécifie le type .NET d’un objet qui appartient au jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="72d06-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="72d06-104">Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) types élément (format) TypeName élément de types (format)</span><span class="sxs-lookup"><span data-stu-id="72d06-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="72d06-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72d06-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="72d06-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="72d06-106">Attributes and Elements</span></span>

<span data-ttu-id="72d06-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="72d06-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="72d06-108">Au moins un `TypeName` élément doit être inclus dans le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="72d06-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="72d06-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="72d06-109">Attributes</span></span>

<span data-ttu-id="72d06-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="72d06-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="72d06-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="72d06-111">Child Elements</span></span>

<span data-ttu-id="72d06-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="72d06-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="72d06-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="72d06-113">Parent Elements</span></span>

|<span data-ttu-id="72d06-114">Élément</span><span class="sxs-lookup"><span data-stu-id="72d06-114">Element</span></span>|<span data-ttu-id="72d06-115">Description</span><span class="sxs-lookup"><span data-stu-id="72d06-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72d06-116">Élément types (format)</span><span class="sxs-lookup"><span data-stu-id="72d06-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="72d06-117">Définit les objets .NET qui se trouvent dans le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="72d06-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="72d06-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="72d06-118">Text Value</span></span>

<span data-ttu-id="72d06-119">Spécifiez le nom qualifié complet du type .NET.</span><span class="sxs-lookup"><span data-stu-id="72d06-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="72d06-120">Notes</span><span class="sxs-lookup"><span data-stu-id="72d06-120">Remarks</span></span>

<span data-ttu-id="72d06-121">Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="72d06-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="72d06-122">Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.</span><span class="sxs-lookup"><span data-stu-id="72d06-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="72d06-123">Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="72d06-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="72d06-124">Dans ce cas, l' `SelectionSetName` élément enfant de l' `ViewSelectedBy` élément de la vue spécifie le jeu.</span><span class="sxs-lookup"><span data-stu-id="72d06-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="72d06-125">Toutefois, différentes entrées d’une vue peuvent également spécifier un jeu de sélection qui s’applique uniquement à cette entrée de la vue.</span><span class="sxs-lookup"><span data-stu-id="72d06-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="72d06-126">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="72d06-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="72d06-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="72d06-127">Example</span></span>

<span data-ttu-id="72d06-128">L’exemple suivant montre un `SelectionSet` élément qui définit quatre types .net.</span><span class="sxs-lookup"><span data-stu-id="72d06-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="72d06-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72d06-129">See Also</span></span>

[<span data-ttu-id="72d06-130">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="72d06-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="72d06-131">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="72d06-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="72d06-132">SelectionSets, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="72d06-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="72d06-133">Élément types (format)</span><span class="sxs-lookup"><span data-stu-id="72d06-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="72d06-134">Écriture d’un fichier de mise en forme Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="72d06-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
