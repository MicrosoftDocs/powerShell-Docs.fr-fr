---
title: Élément ViewDefinitions (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361418"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="75a95-102">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="75a95-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="75a95-103">Définit les vues utilisées pour afficher des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="75a95-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="75a95-104">Ces vues peuvent afficher les propriétés et les valeurs de script d’un objet dans un format de tableau, un format de liste, un format étendu et un format de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75a95-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="75a95-105">Élément de configuration (format) ViewDefinitions (format XML)</span><span class="sxs-lookup"><span data-stu-id="75a95-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="75a95-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75a95-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75a95-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="75a95-107">Attributes and Elements</span></span>

<span data-ttu-id="75a95-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ViewDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="75a95-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="75a95-109">Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme et ils peuvent être ajoutés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="75a95-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="75a95-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="75a95-110">Attributes</span></span>

<span data-ttu-id="75a95-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="75a95-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75a95-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="75a95-112">Child Elements</span></span>

|<span data-ttu-id="75a95-113">Élément</span><span class="sxs-lookup"><span data-stu-id="75a95-113">Element</span></span>|<span data-ttu-id="75a95-114">Description</span><span class="sxs-lookup"><span data-stu-id="75a95-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75a95-115">View, élément (format)</span><span class="sxs-lookup"><span data-stu-id="75a95-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="75a95-116">Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="75a95-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="75a95-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="75a95-117">Parent Elements</span></span>

|<span data-ttu-id="75a95-118">Élément</span><span class="sxs-lookup"><span data-stu-id="75a95-118">Element</span></span>|<span data-ttu-id="75a95-119">Description</span><span class="sxs-lookup"><span data-stu-id="75a95-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75a95-120">Élément configuration (format)</span><span class="sxs-lookup"><span data-stu-id="75a95-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="75a95-121">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="75a95-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="75a95-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="75a95-122">Remarks</span></span>

<span data-ttu-id="75a95-123">Pour plus d’informations sur les composants des différents types d’affichages, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="75a95-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="75a95-124">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="75a95-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="75a95-125">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="75a95-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="75a95-126">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="75a95-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="75a95-127">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="75a95-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="75a95-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="75a95-128">Example</span></span>

<span data-ttu-id="75a95-129">Cet exemple montre un élément `ViewDefinitions` qui contient les éléments parents d’une vue de table et d’une vue liste.</span><span class="sxs-lookup"><span data-stu-id="75a95-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="75a95-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75a95-130">See Also</span></span>

[<span data-ttu-id="75a95-131">Élément configuration (format)</span><span class="sxs-lookup"><span data-stu-id="75a95-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="75a95-132">View, élément (format)</span><span class="sxs-lookup"><span data-stu-id="75a95-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="75a95-133">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="75a95-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="75a95-134">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="75a95-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="75a95-135">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="75a95-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="75a95-136">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="75a95-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="75a95-137">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="75a95-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
