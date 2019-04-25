---
title: Élément ViewDefinitions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083703"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="cea30-102">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="cea30-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="cea30-103">Définit les vues utilisées pour afficher les objets .NET.</span><span class="sxs-lookup"><span data-stu-id="cea30-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="cea30-104">Ces vues peuvent afficher les propriétés et valeurs de script d’un objet dans un format de table, format de liste, format large et format de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="cea30-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="cea30-105">Élément de configuration (Format) d’élément ViewDefinitions (Format XML)</span><span class="sxs-lookup"><span data-stu-id="cea30-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="cea30-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cea30-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cea30-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="cea30-107">Attributes and Elements</span></span>

<span data-ttu-id="cea30-108">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `ViewDefinitions` élément.</span><span class="sxs-lookup"><span data-stu-id="cea30-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="cea30-109">Il n’existe aucune limite au nombre de vues qui peuvent être définies dans un fichier de mise en forme, et ils peuvent être ajoutés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="cea30-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="cea30-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="cea30-110">Attributes</span></span>

<span data-ttu-id="cea30-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="cea30-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cea30-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cea30-112">Child Elements</span></span>

|<span data-ttu-id="cea30-113">Élément</span><span class="sxs-lookup"><span data-stu-id="cea30-113">Element</span></span>|<span data-ttu-id="cea30-114">Description</span><span class="sxs-lookup"><span data-stu-id="cea30-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cea30-115">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="cea30-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="cea30-116">Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="cea30-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cea30-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cea30-117">Parent Elements</span></span>

|<span data-ttu-id="cea30-118">Élément</span><span class="sxs-lookup"><span data-stu-id="cea30-118">Element</span></span>|<span data-ttu-id="cea30-119">Description</span><span class="sxs-lookup"><span data-stu-id="cea30-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cea30-120">Élément de configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="cea30-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="cea30-121">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cea30-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cea30-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="cea30-122">Remarks</span></span>

<span data-ttu-id="cea30-123">Pour plus d’informations sur les composants des différents types de vues, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="cea30-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="cea30-124">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="cea30-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="cea30-125">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="cea30-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="cea30-126">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="cea30-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="cea30-127">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="cea30-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="cea30-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="cea30-128">Example</span></span>

<span data-ttu-id="cea30-129">Cet exemple montre un `ViewDefinitions` élément qui contient les éléments parents pour une vue de table et une vue de liste.</span><span class="sxs-lookup"><span data-stu-id="cea30-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cea30-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cea30-130">See Also</span></span>

[<span data-ttu-id="cea30-131">Élément de configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="cea30-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="cea30-132">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="cea30-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="cea30-133">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="cea30-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cea30-134">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="cea30-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="cea30-135">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="cea30-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="cea30-136">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="cea30-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="cea30-137">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cea30-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
