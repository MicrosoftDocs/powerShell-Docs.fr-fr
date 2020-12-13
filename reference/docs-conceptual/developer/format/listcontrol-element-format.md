---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl, élément (Format)
description: ListControl, élément (Format)
ms.openlocfilehash: cd5687ac8e94e2245d1ae2de8b2206185e5b8ca4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666584"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="0f4a7-103">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="0f4a7-103">ListControl Element (Format)</span></span>

<span data-ttu-id="0f4a7-104">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="0f4a7-104">Defines a list format for the view.</span></span>

<span data-ttu-id="0f4a7-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) ListControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="0f4a7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f4a7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f4a7-106">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f4a7-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0f4a7-107">Attributes and Elements</span></span>

<span data-ttu-id="0f4a7-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListControl` élément.</span><span class="sxs-lookup"><span data-stu-id="0f4a7-108">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="0f4a7-109">Cet élément ne doit contenir qu’un seul élément enfant.</span><span class="sxs-lookup"><span data-stu-id="0f4a7-109">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f4a7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0f4a7-110">Attributes</span></span>

<span data-ttu-id="0f4a7-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0f4a7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f4a7-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0f4a7-112">Child Elements</span></span>

|<span data-ttu-id="0f4a7-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0f4a7-113">Element</span></span>|<span data-ttu-id="0f4a7-114">Description</span><span class="sxs-lookup"><span data-stu-id="0f4a7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f4a7-115">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="0f4a7-115">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="0f4a7-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="0f4a7-116">Required element.</span></span><br /><br /> <span data-ttu-id="0f4a7-117">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="0f4a7-117">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0f4a7-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0f4a7-118">Parent Elements</span></span>

|<span data-ttu-id="0f4a7-119">Élément</span><span class="sxs-lookup"><span data-stu-id="0f4a7-119">Element</span></span>|<span data-ttu-id="0f4a7-120">Description</span><span class="sxs-lookup"><span data-stu-id="0f4a7-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f4a7-121">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="0f4a7-121">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="0f4a7-122">Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="0f4a7-122">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0f4a7-123">Notes</span><span class="sxs-lookup"><span data-stu-id="0f4a7-123">Remarks</span></span>

<span data-ttu-id="0f4a7-124">Pour plus d’informations sur la création d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="0f4a7-124">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f4a7-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="0f4a7-125">Example</span></span>

<span data-ttu-id="0f4a7-126">Cet exemple montre un affichage de liste pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="0f4a7-126">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="0f4a7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f4a7-127">See Also</span></span>

[<span data-ttu-id="0f4a7-128">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="0f4a7-128">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="0f4a7-129">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="0f4a7-129">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="0f4a7-130">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="0f4a7-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0f4a7-131">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f4a7-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
