---
title: Élément ViewDefinitions (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a108c4f8b03e3dec3905181b390aee2c82ab0028
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772482"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="fd9bf-102">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="fd9bf-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="fd9bf-103">Définit les vues utilisées pour afficher des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="fd9bf-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="fd9bf-104">Ces vues peuvent afficher les propriétés et les valeurs de script d’un objet dans un format de tableau, un format de liste, un format étendu et un format de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fd9bf-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="fd9bf-105">Élément de configuration (format) ViewDefinitions (format XML)</span><span class="sxs-lookup"><span data-stu-id="fd9bf-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="fd9bf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd9bf-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd9bf-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fd9bf-107">Attributes and Elements</span></span>

<span data-ttu-id="fd9bf-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ViewDefinitions` élément.</span><span class="sxs-lookup"><span data-stu-id="fd9bf-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="fd9bf-109">Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme et ils peuvent être ajoutés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="fd9bf-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd9bf-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="fd9bf-110">Attributes</span></span>

<span data-ttu-id="fd9bf-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fd9bf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd9bf-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fd9bf-112">Child Elements</span></span>

|<span data-ttu-id="fd9bf-113">Élément</span><span class="sxs-lookup"><span data-stu-id="fd9bf-113">Element</span></span>|<span data-ttu-id="fd9bf-114">Description</span><span class="sxs-lookup"><span data-stu-id="fd9bf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd9bf-115">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="fd9bf-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="fd9bf-116">Définit une vue qui est utilisée pour afficher un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="fd9bf-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fd9bf-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fd9bf-117">Parent Elements</span></span>

|<span data-ttu-id="fd9bf-118">Élément</span><span class="sxs-lookup"><span data-stu-id="fd9bf-118">Element</span></span>|<span data-ttu-id="fd9bf-119">Description</span><span class="sxs-lookup"><span data-stu-id="fd9bf-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd9bf-120">Configuration, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="fd9bf-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="fd9bf-121">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="fd9bf-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fd9bf-122">Notes</span><span class="sxs-lookup"><span data-stu-id="fd9bf-122">Remarks</span></span>

<span data-ttu-id="fd9bf-123">Pour plus d’informations sur les composants des différents types d’affichages, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="fd9bf-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="fd9bf-124">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="fd9bf-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="fd9bf-125">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="fd9bf-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="fd9bf-126">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="fd9bf-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="fd9bf-127">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="fd9bf-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="fd9bf-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd9bf-128">Example</span></span>

<span data-ttu-id="fd9bf-129">Cet exemple montre un `ViewDefinitions` élément qui contient les éléments parents d’une vue de table et d’une vue liste.</span><span class="sxs-lookup"><span data-stu-id="fd9bf-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fd9bf-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd9bf-130">See Also</span></span>

[<span data-ttu-id="fd9bf-131">Configuration, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="fd9bf-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="fd9bf-132">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="fd9bf-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="fd9bf-133">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="fd9bf-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fd9bf-134">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="fd9bf-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fd9bf-135">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="fd9bf-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fd9bf-136">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="fd9bf-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="fd9bf-137">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd9bf-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
