---
title: Élément de nom de type pour les Types (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083788"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="c5255-102">TypeName, élément pour Types (Format)</span><span class="sxs-lookup"><span data-stu-id="c5255-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="c5255-103">Spécifie le type .NET d’un objet qui appartient au jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="c5255-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="c5255-104">Types de configuration élément (Format) SelectionSets (Format) SelectionSet élément (Format) (Format) TypeName Element de Types (Format)</span><span class="sxs-lookup"><span data-stu-id="c5255-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c5255-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5255-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c5255-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="c5255-106">Attributes and Elements</span></span>

<span data-ttu-id="c5255-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="c5255-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="c5255-108">Au moins un `TypeName` élément doit être inclus dans le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="c5255-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5255-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c5255-109">Attributes</span></span>

<span data-ttu-id="c5255-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c5255-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c5255-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c5255-111">Child Elements</span></span>

<span data-ttu-id="c5255-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c5255-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c5255-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c5255-113">Parent Elements</span></span>

|<span data-ttu-id="c5255-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c5255-114">Element</span></span>|<span data-ttu-id="c5255-115">Description</span><span class="sxs-lookup"><span data-stu-id="c5255-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5255-116">Élément de types (Format)</span><span class="sxs-lookup"><span data-stu-id="c5255-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="c5255-117">Définit les objets .NET qui sont définies dans la sélection.</span><span class="sxs-lookup"><span data-stu-id="c5255-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c5255-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="c5255-118">Text Value</span></span>

<span data-ttu-id="c5255-119">Spécifiez le nom qualifié complet pour le type .NET.</span><span class="sxs-lookup"><span data-stu-id="c5255-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5255-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5255-120">Remarks</span></span>

<span data-ttu-id="c5255-121">Vous pouvez utiliser des jeux de sélection lorsque vous avez un ensemble d’objets connexes que vous souhaitez faire référence à l’aide d’un nom unique, comme un ensemble d’objets qui sont liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="c5255-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="c5255-122">Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom de la sélection définie au lieu de répertorier tous les objets au sein de chaque vue.</span><span class="sxs-lookup"><span data-stu-id="c5255-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="c5255-123">Ensembles communs de sélection sont spécifiés par leur nom lorsque vous définissez les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="c5255-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="c5255-124">Dans ce cas, le `SelectionSetName` élément enfant de le `ViewSelectedBy` élément pour l’affichage spécifie le jeu.</span><span class="sxs-lookup"><span data-stu-id="c5255-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="c5255-125">Toutefois, des entrées différentes d’une vue peuvent également spécifier un jeu de sélection s’applique à uniquement l’entrée de la vue.</span><span class="sxs-lookup"><span data-stu-id="c5255-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="c5255-126">Pour plus d’informations sur les jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c5255-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="c5255-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="c5255-127">Example</span></span>

<span data-ttu-id="c5255-128">L’exemple suivant montre un `SelectionSet` élément qui définit les quatre types de .NET.</span><span class="sxs-lookup"><span data-stu-id="c5255-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c5255-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5255-129">See Also</span></span>

[<span data-ttu-id="c5255-130">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="c5255-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c5255-131">Élément SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="c5255-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="c5255-132">Élément SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="c5255-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="c5255-133">Élément de types (Format)</span><span class="sxs-lookup"><span data-stu-id="c5255-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="c5255-134">Écriture d’un fichier de mise en forme de PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="c5255-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
