---
title: Élément ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0173b9797bffcca74f1a32903686f771366ebb1b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785725"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="397c5-102">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="397c5-102">ListControl Element (Format)</span></span>

<span data-ttu-id="397c5-103">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="397c5-103">Defines a list format for the view.</span></span>

<span data-ttu-id="397c5-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) ListControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="397c5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="397c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="397c5-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="397c5-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="397c5-106">Attributes and Elements</span></span>

<span data-ttu-id="397c5-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListControl` élément.</span><span class="sxs-lookup"><span data-stu-id="397c5-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="397c5-108">Cet élément ne doit contenir qu’un seul élément enfant.</span><span class="sxs-lookup"><span data-stu-id="397c5-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="397c5-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="397c5-109">Attributes</span></span>

<span data-ttu-id="397c5-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="397c5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="397c5-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="397c5-111">Child Elements</span></span>

|<span data-ttu-id="397c5-112">Élément</span><span class="sxs-lookup"><span data-stu-id="397c5-112">Element</span></span>|<span data-ttu-id="397c5-113">Description</span><span class="sxs-lookup"><span data-stu-id="397c5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="397c5-114">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="397c5-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="397c5-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="397c5-115">Required element.</span></span><br /><br /> <span data-ttu-id="397c5-116">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="397c5-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="397c5-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="397c5-117">Parent Elements</span></span>

|<span data-ttu-id="397c5-118">Élément</span><span class="sxs-lookup"><span data-stu-id="397c5-118">Element</span></span>|<span data-ttu-id="397c5-119">Description</span><span class="sxs-lookup"><span data-stu-id="397c5-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="397c5-120">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="397c5-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="397c5-121">Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="397c5-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="397c5-122">Notes</span><span class="sxs-lookup"><span data-stu-id="397c5-122">Remarks</span></span>

<span data-ttu-id="397c5-123">Pour plus d’informations sur la création d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="397c5-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="397c5-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="397c5-124">Example</span></span>

<span data-ttu-id="397c5-125">Cet exemple montre un affichage de liste pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="397c5-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="397c5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="397c5-126">See Also</span></span>

[<span data-ttu-id="397c5-127">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="397c5-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="397c5-128">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="397c5-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="397c5-129">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="397c5-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="397c5-130">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="397c5-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
