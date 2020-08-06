---
title: Élément Name pour SelectionSet (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1fc33eeb87a6912ed6793629ab1969cd65b5f0c5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773298"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="0e9c0-102">Name, élément pour SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="0e9c0-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="0e9c0-103">Spécifie le nom utilisé pour référencer le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="0e9c0-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="0e9c0-104">Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) élément Name de SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="0e9c0-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0e9c0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e9c0-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e9c0-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0e9c0-106">Attributes and Elements</span></span>

<span data-ttu-id="0e9c0-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Name` élément.</span><span class="sxs-lookup"><span data-stu-id="0e9c0-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e9c0-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="0e9c0-108">Attributes</span></span>

<span data-ttu-id="0e9c0-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0e9c0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0e9c0-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0e9c0-110">Child Elements</span></span>

<span data-ttu-id="0e9c0-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0e9c0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0e9c0-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0e9c0-112">Parent Elements</span></span>

|<span data-ttu-id="0e9c0-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0e9c0-113">Element</span></span>|<span data-ttu-id="0e9c0-114">Description</span><span class="sxs-lookup"><span data-stu-id="0e9c0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e9c0-115">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="0e9c0-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="0e9c0-116">Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="0e9c0-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0e9c0-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="0e9c0-117">Text Value</span></span>

<span data-ttu-id="0e9c0-118">Spécifiez le nom pour faire référence au jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="0e9c0-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="0e9c0-119">Il n’existe aucune restriction quant aux caractères qui peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="0e9c0-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e9c0-120">Notes</span><span class="sxs-lookup"><span data-stu-id="0e9c0-120">Remarks</span></span>

<span data-ttu-id="0e9c0-121">Le nom spécifié ici est utilisé dans l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="0e9c0-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="0e9c0-122">Jeu de sélection qui peut être utilisé par une vue, par une définition d’une vue (les vues peuvent avoir plusieurs définitions) ou lors de la spécification d’une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="0e9c0-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="0e9c0-123">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0e9c0-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="0e9c0-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="0e9c0-124">Example</span></span>

<span data-ttu-id="0e9c0-125">Cet exemple montre un `SelectionSet` élément qui définit quatre types .net.</span><span class="sxs-lookup"><span data-stu-id="0e9c0-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="0e9c0-126">Le nom du jeu de sélection est « FileSystemTypes ».</span><span class="sxs-lookup"><span data-stu-id="0e9c0-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0e9c0-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e9c0-127">See Also</span></span>

[<span data-ttu-id="0e9c0-128">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="0e9c0-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0e9c0-129">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="0e9c0-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="0e9c0-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e9c0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
