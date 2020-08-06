---
title: Élément ViewSelectedBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8704c1504c6e24c9cac6bc8bc25e92a0d9110cc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785011"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="38fd4-102">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="38fd4-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="38fd4-103">Définit les objets .NET affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="38fd4-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="38fd4-104">Chaque vue doit spécifier au moins un objet .NET.</span><span class="sxs-lookup"><span data-stu-id="38fd4-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="38fd4-105">Élément ViewDefinitions (format), élément de vue (format) élément ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="38fd4-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38fd4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38fd4-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38fd4-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="38fd4-107">Attributes and Elements</span></span>

<span data-ttu-id="38fd4-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ViewSelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="38fd4-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="38fd4-109">Cet élément doit contenir au moins un `TypeName` `SelectionSetName` élément enfant ou.</span><span class="sxs-lookup"><span data-stu-id="38fd4-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="38fd4-110">Il n’existe aucune limite quant au nombre d’éléments enfants qui peuvent être spécifiés et dont l’ordre est significatif.</span><span class="sxs-lookup"><span data-stu-id="38fd4-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="38fd4-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="38fd4-111">Attributes</span></span>

<span data-ttu-id="38fd4-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="38fd4-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38fd4-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38fd4-113">Child Elements</span></span>

|<span data-ttu-id="38fd4-114">Élément</span><span class="sxs-lookup"><span data-stu-id="38fd4-114">Element</span></span>|<span data-ttu-id="38fd4-115">Description</span><span class="sxs-lookup"><span data-stu-id="38fd4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38fd4-116">TypeName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="38fd4-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="38fd4-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="38fd4-117">Optional element.</span></span><br /><br /> <span data-ttu-id="38fd4-118">Spécifie un objet .NET qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="38fd4-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="38fd4-119">SelectionSetName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="38fd4-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="38fd4-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="38fd4-120">Optional element.</span></span><br /><br /> <span data-ttu-id="38fd4-121">Spécifie un jeu d’objets .NET qui sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="38fd4-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38fd4-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38fd4-122">Parent Elements</span></span>

|<span data-ttu-id="38fd4-123">Élément</span><span class="sxs-lookup"><span data-stu-id="38fd4-123">Element</span></span>|<span data-ttu-id="38fd4-124">Description</span><span class="sxs-lookup"><span data-stu-id="38fd4-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38fd4-125">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="38fd4-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="38fd4-126">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="38fd4-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38fd4-127">Notes</span><span class="sxs-lookup"><span data-stu-id="38fd4-127">Remarks</span></span>

<span data-ttu-id="38fd4-128">Pour plus d’informations sur l’utilisation de cet élément dans différents affichages, consultez [composants de vue de table](./creating-a-table-view.md), composants de vue de [liste](./creating-a-list-view.md), composants de [vue larges](./creating-a-wide-view.md)et [composants de contrôle personnalisé](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="38fd4-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="38fd4-129">L' `SelectionSetName` élément est utilisé lorsque le fichier de mise en forme définit un ensemble d’objets qui sont affichés par plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="38fd4-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="38fd4-130">Pour plus d’informations sur la façon dont les jeux de sélection sont définis et référencés, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="38fd4-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="38fd4-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="38fd4-131">Example</span></span>

<span data-ttu-id="38fd4-132">L’exemple suivant montre comment spécifier l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) pour un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="38fd4-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="38fd4-133">Le même schéma est utilisé pour les vues de table, larges et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="38fd4-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="38fd4-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38fd4-134">See Also</span></span>

[<span data-ttu-id="38fd4-135">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="38fd4-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="38fd4-136">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="38fd4-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="38fd4-137">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="38fd4-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="38fd4-138">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="38fd4-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="38fd4-139">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="38fd4-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="38fd4-140">SelectionSetName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="38fd4-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="38fd4-141">TypeName, élément (format)</span><span class="sxs-lookup"><span data-stu-id="38fd4-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="38fd4-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="38fd4-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
