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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362778"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="052c1-102">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="052c1-102">ListControl Element (Format)</span></span>

<span data-ttu-id="052c1-103">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="052c1-103">Defines a list format for the view.</span></span>

<span data-ttu-id="052c1-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) ListControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="052c1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="052c1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="052c1-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="052c1-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="052c1-106">Attributes and Elements</span></span>

<span data-ttu-id="052c1-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ListControl`.</span><span class="sxs-lookup"><span data-stu-id="052c1-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="052c1-108">Cet élément ne doit contenir qu’un seul élément enfant.</span><span class="sxs-lookup"><span data-stu-id="052c1-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="052c1-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="052c1-109">Attributes</span></span>

<span data-ttu-id="052c1-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="052c1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="052c1-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="052c1-111">Child Elements</span></span>

|<span data-ttu-id="052c1-112">Élément</span><span class="sxs-lookup"><span data-stu-id="052c1-112">Element</span></span>|<span data-ttu-id="052c1-113">Description</span><span class="sxs-lookup"><span data-stu-id="052c1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="052c1-114">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="052c1-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="052c1-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="052c1-115">Required element.</span></span><br /><br /> <span data-ttu-id="052c1-116">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="052c1-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="052c1-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="052c1-117">Parent Elements</span></span>

|<span data-ttu-id="052c1-118">Élément</span><span class="sxs-lookup"><span data-stu-id="052c1-118">Element</span></span>|<span data-ttu-id="052c1-119">Description</span><span class="sxs-lookup"><span data-stu-id="052c1-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="052c1-120">View, élément (format)</span><span class="sxs-lookup"><span data-stu-id="052c1-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="052c1-121">Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="052c1-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="052c1-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="052c1-122">Remarks</span></span>

<span data-ttu-id="052c1-123">Pour plus d’informations sur la création d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="052c1-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="052c1-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="052c1-124">Example</span></span>

<span data-ttu-id="052c1-125">Cet exemple montre un affichage de liste pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="052c1-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="052c1-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="052c1-126">See Also</span></span>

[<span data-ttu-id="052c1-127">View, élément (format)</span><span class="sxs-lookup"><span data-stu-id="052c1-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="052c1-128">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="052c1-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="052c1-129">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="052c1-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="052c1-130">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="052c1-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
