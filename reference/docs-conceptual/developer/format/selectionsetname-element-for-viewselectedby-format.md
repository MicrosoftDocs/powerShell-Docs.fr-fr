---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour ViewSelectedBy (Format)
description: SelectionSetName, élément pour ViewSelectedBy (Format)
ms.openlocfilehash: a1a1816761715a138bcb3c2bd4cb9dbbb2f9cb92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654912"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="ceea6-103">SelectionSetName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ceea6-103">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="ceea6-104">Spécifie un jeu d’objets .NET qui sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="ceea6-104">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="ceea6-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément ViewSelectedBy (format) élément SelectionSetName pour ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ceea6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ceea6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ceea6-106">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ceea6-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ceea6-107">Attributes and Elements</span></span>

<span data-ttu-id="ceea6-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="ceea6-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ceea6-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="ceea6-109">Attributes</span></span>

<span data-ttu-id="ceea6-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ceea6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ceea6-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ceea6-111">Child Elements</span></span>

<span data-ttu-id="ceea6-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ceea6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ceea6-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ceea6-113">Parent Elements</span></span>

|<span data-ttu-id="ceea6-114">Élément</span><span class="sxs-lookup"><span data-stu-id="ceea6-114">Element</span></span>|<span data-ttu-id="ceea6-115">Description</span><span class="sxs-lookup"><span data-stu-id="ceea6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ceea6-116">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ceea6-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="ceea6-117">Définit les objets .NET affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="ceea6-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ceea6-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="ceea6-118">Text Value</span></span>

<span data-ttu-id="ceea6-119">Spécifiez le nom du jeu de sélection défini par l' `Name` élément pour le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="ceea6-119">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ceea6-120">Notes</span><span class="sxs-lookup"><span data-stu-id="ceea6-120">Remarks</span></span>

<span data-ttu-id="ceea6-121">Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="ceea6-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="ceea6-122">Pour plus d’informations sur la définition et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ceea6-122">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="ceea6-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="ceea6-123">Example</span></span>

<span data-ttu-id="ceea6-124">L’exemple suivant montre comment spécifier un jeu de sélection pour un mode liste.</span><span class="sxs-lookup"><span data-stu-id="ceea6-124">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="ceea6-125">Le même schéma est utilisé pour les vues de table, larges et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="ceea6-125">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="ceea6-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ceea6-126">See Also</span></span>

[<span data-ttu-id="ceea6-127">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="ceea6-127">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ceea6-128">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ceea6-128">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="ceea6-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ceea6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
