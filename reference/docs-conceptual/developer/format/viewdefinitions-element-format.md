---
ms.date: 09/13/2016
ms.topic: reference
title: ViewDefinitions, élément (Format)
description: ViewDefinitions, élément (Format)
ms.openlocfilehash: fceef0e5ec91e8c59a7b2b90fd31ca422ff0c94d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664582"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="dbc9a-103">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="dbc9a-103">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="dbc9a-104">Définit les vues utilisées pour afficher des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="dbc9a-104">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="dbc9a-105">Ces vues peuvent afficher les propriétés et les valeurs de script d’un objet dans un format de tableau, un format de liste, un format étendu et un format de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="dbc9a-105">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="dbc9a-106">Élément de configuration (format) ViewDefinitions (format XML)</span><span class="sxs-lookup"><span data-stu-id="dbc9a-106">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="dbc9a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbc9a-107">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dbc9a-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dbc9a-108">Attributes and Elements</span></span>

<span data-ttu-id="dbc9a-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ViewDefinitions` élément.</span><span class="sxs-lookup"><span data-stu-id="dbc9a-109">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="dbc9a-110">Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme et ils peuvent être ajoutés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="dbc9a-110">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="dbc9a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="dbc9a-111">Attributes</span></span>

<span data-ttu-id="dbc9a-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dbc9a-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dbc9a-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dbc9a-113">Child Elements</span></span>

|<span data-ttu-id="dbc9a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="dbc9a-114">Element</span></span>|<span data-ttu-id="dbc9a-115">Description</span><span class="sxs-lookup"><span data-stu-id="dbc9a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dbc9a-116">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="dbc9a-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="dbc9a-117">Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="dbc9a-117">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dbc9a-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dbc9a-118">Parent Elements</span></span>

|<span data-ttu-id="dbc9a-119">Élément</span><span class="sxs-lookup"><span data-stu-id="dbc9a-119">Element</span></span>|<span data-ttu-id="dbc9a-120">Description</span><span class="sxs-lookup"><span data-stu-id="dbc9a-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dbc9a-121">Configuration, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="dbc9a-121">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="dbc9a-122">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="dbc9a-122">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dbc9a-123">Notes</span><span class="sxs-lookup"><span data-stu-id="dbc9a-123">Remarks</span></span>

<span data-ttu-id="dbc9a-124">Pour plus d’informations sur les composants des différents types d’affichages, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="dbc9a-124">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="dbc9a-125">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="dbc9a-125">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="dbc9a-126">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="dbc9a-126">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="dbc9a-127">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="dbc9a-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="dbc9a-128">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="dbc9a-128">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="dbc9a-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="dbc9a-129">Example</span></span>

<span data-ttu-id="dbc9a-130">Cet exemple montre un `ViewDefinitions` élément qui contient les éléments parents d’une vue de table et d’une vue liste.</span><span class="sxs-lookup"><span data-stu-id="dbc9a-130">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="dbc9a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbc9a-131">See Also</span></span>

[<span data-ttu-id="dbc9a-132">Configuration, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="dbc9a-132">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="dbc9a-133">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="dbc9a-133">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="dbc9a-134">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="dbc9a-134">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="dbc9a-135">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="dbc9a-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="dbc9a-136">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="dbc9a-136">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="dbc9a-137">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="dbc9a-137">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="dbc9a-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbc9a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
