---
title: Élément ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362778"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="33c49-102">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="33c49-102">ListControl Element (Format)</span></span>

<span data-ttu-id="33c49-103">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="33c49-103">Defines a list format for the view.</span></span>

<span data-ttu-id="33c49-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) ListControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="33c49-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33c49-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33c49-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="33c49-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="33c49-106">Attributes and Elements</span></span>

<span data-ttu-id="33c49-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ListControl`.</span><span class="sxs-lookup"><span data-stu-id="33c49-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="33c49-108">Cet élément ne doit contenir qu’un seul élément enfant.</span><span class="sxs-lookup"><span data-stu-id="33c49-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33c49-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="33c49-109">Attributes</span></span>

<span data-ttu-id="33c49-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="33c49-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33c49-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="33c49-111">Child Elements</span></span>

|<span data-ttu-id="33c49-112">Élément</span><span class="sxs-lookup"><span data-stu-id="33c49-112">Element</span></span>|<span data-ttu-id="33c49-113">Description</span><span class="sxs-lookup"><span data-stu-id="33c49-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33c49-114">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="33c49-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="33c49-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="33c49-115">Required element.</span></span><br /><br /> <span data-ttu-id="33c49-116">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="33c49-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33c49-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="33c49-117">Parent Elements</span></span>

|<span data-ttu-id="33c49-118">Élément</span><span class="sxs-lookup"><span data-stu-id="33c49-118">Element</span></span>|<span data-ttu-id="33c49-119">Description</span><span class="sxs-lookup"><span data-stu-id="33c49-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33c49-120">View, élément (format)</span><span class="sxs-lookup"><span data-stu-id="33c49-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="33c49-121">Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="33c49-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="33c49-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="33c49-122">Remarks</span></span>

<span data-ttu-id="33c49-123">Pour plus d’informations sur la création d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="33c49-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="33c49-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="33c49-124">Example</span></span>

<span data-ttu-id="33c49-125">Cet exemple montre un affichage de liste pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="33c49-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="33c49-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33c49-126">See Also</span></span>

[<span data-ttu-id="33c49-127">View, élément (format)</span><span class="sxs-lookup"><span data-stu-id="33c49-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="33c49-128">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="33c49-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="33c49-129">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="33c49-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="33c49-130">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="33c49-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
