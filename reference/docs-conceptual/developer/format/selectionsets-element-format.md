---
title: Élément SelectionSets (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 718b08e02220f285ef215fdca727492fd4407466
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785198"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="cfb16-102">SelectionSets, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="cfb16-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="cfb16-103">Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cfb16-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="cfb16-104">Les vues et les contrôles du fichier de mise en forme peuvent faire référence à l’ensemble complet d’objets en utilisant uniquement le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="cfb16-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="cfb16-105">Format d’élément SelectionSets de l’élément de configuration</span><span class="sxs-lookup"><span data-stu-id="cfb16-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="cfb16-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfb16-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cfb16-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cfb16-107">Attributes and Elements</span></span>

<span data-ttu-id="cfb16-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSets` élément.</span><span class="sxs-lookup"><span data-stu-id="cfb16-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="cfb16-109">Chaque élément enfant définit un ensemble d’objets qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="cfb16-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="cfb16-110">L’ordre des éléments enfants n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="cfb16-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="cfb16-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="cfb16-111">Attributes</span></span>

<span data-ttu-id="cfb16-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cfb16-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cfb16-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cfb16-113">Child Elements</span></span>

|<span data-ttu-id="cfb16-114">Élément</span><span class="sxs-lookup"><span data-stu-id="cfb16-114">Element</span></span>|<span data-ttu-id="cfb16-115">Description</span><span class="sxs-lookup"><span data-stu-id="cfb16-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cfb16-116">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="cfb16-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="cfb16-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="cfb16-117">Required element.</span></span><br /><br /> <span data-ttu-id="cfb16-118">Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="cfb16-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cfb16-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cfb16-119">Parent Elements</span></span>

|<span data-ttu-id="cfb16-120">Élément</span><span class="sxs-lookup"><span data-stu-id="cfb16-120">Element</span></span>|<span data-ttu-id="cfb16-121">Description</span><span class="sxs-lookup"><span data-stu-id="cfb16-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cfb16-122">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="cfb16-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="cfb16-123">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cfb16-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cfb16-124">Notes</span><span class="sxs-lookup"><span data-stu-id="cfb16-124">Remarks</span></span>

<span data-ttu-id="cfb16-125">Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="cfb16-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="cfb16-126">Lorsque vous définissez vos vues, vous pouvez spécifier le jeu d’objets en utilisant le nom du jeu de sélection au lieu de répertorier tous les objets dans chaque vue.</span><span class="sxs-lookup"><span data-stu-id="cfb16-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="cfb16-127">Les jeux de sélection communs sont spécifiés par leur nom lors de la définition des vues du fichier de mise en forme ou des définitions des vues.</span><span class="sxs-lookup"><span data-stu-id="cfb16-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="cfb16-128">Dans ce cas, l' `SelectionSetName` élément enfant des `ViewSelectedBy` éléments et `EntrySelectedBy` spécifie le jeu à utiliser.</span><span class="sxs-lookup"><span data-stu-id="cfb16-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="cfb16-129">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="cfb16-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cfb16-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfb16-130">See Also</span></span>

[<span data-ttu-id="cfb16-131">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="cfb16-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="cfb16-132">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="cfb16-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="cfb16-133">SelectionSet, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="cfb16-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="cfb16-134">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfb16-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
