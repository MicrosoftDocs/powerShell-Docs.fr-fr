---
title: Élément ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863185"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="bbc33-102">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc33-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="bbc33-103">Définit les objets .NET qui sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="bbc33-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="bbc33-104">Chaque vue doit spécifier au moins un objet .NET.</span><span class="sxs-lookup"><span data-stu-id="bbc33-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="bbc33-105">ViewDefinitions élément (Format) vue (Format) ViewSelectedBy élément (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc33-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bbc33-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbc33-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbc33-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="bbc33-107">Attributes and Elements</span></span>

<span data-ttu-id="bbc33-108">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `ViewSelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="bbc33-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="bbc33-109">Cet élément doit contenir au moins un `TypeName` ou `SelectionSetName` élément enfant.</span><span class="sxs-lookup"><span data-stu-id="bbc33-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="bbc33-110">Il n’existe aucune limite au nombre d’éléments enfants qui peuvent être spécifiées, ni leur ordre n’est significative.</span><span class="sxs-lookup"><span data-stu-id="bbc33-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbc33-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="bbc33-111">Attributes</span></span>

<span data-ttu-id="bbc33-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="bbc33-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bbc33-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bbc33-113">Child Elements</span></span>

|<span data-ttu-id="bbc33-114">Élément</span><span class="sxs-lookup"><span data-stu-id="bbc33-114">Element</span></span>|<span data-ttu-id="bbc33-115">Description</span><span class="sxs-lookup"><span data-stu-id="bbc33-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbc33-116">Élément TypeName pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc33-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="bbc33-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="bbc33-117">Optional element.</span></span><br /><br /> <span data-ttu-id="bbc33-118">Spécifie un objet .NET qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="bbc33-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="bbc33-119">Élément SelectionSetName pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc33-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="bbc33-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="bbc33-120">Optional element.</span></span><br /><br /> <span data-ttu-id="bbc33-121">Spécifie un ensemble d’objets .NET qui sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="bbc33-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bbc33-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bbc33-122">Parent Elements</span></span>

|<span data-ttu-id="bbc33-123">Élément</span><span class="sxs-lookup"><span data-stu-id="bbc33-123">Element</span></span>|<span data-ttu-id="bbc33-124">Description</span><span class="sxs-lookup"><span data-stu-id="bbc33-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbc33-125">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc33-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="bbc33-126">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="bbc33-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bbc33-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="bbc33-127">Remarks</span></span>

<span data-ttu-id="bbc33-128">Pour plus d’informations sur la façon dont cet élément est utilisé dans les différentes vues, consultez [les composants de vue de Table](./creating-a-table-view.md), [les composants de vue de liste](./creating-a-list-view.md), [les composants de vue large](./creating-a-wide-view.md)et [Composants de contrôle personnalisé](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="bbc33-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="bbc33-129">Le `SelectionSetName` élément est utilisé lorsque le fichier de mise en forme définit un ensemble d’objets qui sont affichés par plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="bbc33-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="bbc33-130">Pour plus d’informations sur comment les jeux de sélection sont définis et référencés, consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="bbc33-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="bbc33-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="bbc33-131">Example</span></span>

<span data-ttu-id="bbc33-132">L’exemple suivant montre comment spécifier le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet pour un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="bbc33-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="bbc33-133">Le même schéma est utilisé pour les vues table, large et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="bbc33-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="bbc33-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbc33-134">See Also</span></span>

[<span data-ttu-id="bbc33-135">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="bbc33-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="bbc33-136">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="bbc33-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bbc33-137">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="bbc33-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="bbc33-138">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="bbc33-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="bbc33-139">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="bbc33-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="bbc33-140">Élément SelectionSetName pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc33-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="bbc33-141">TypeName, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc33-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="bbc33-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbc33-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
