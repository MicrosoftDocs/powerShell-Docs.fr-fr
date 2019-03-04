---
title: Élément objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857455"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="b5dd8-102">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b5dd8-102">ListControl Element (Format)</span></span>

<span data-ttu-id="b5dd8-103">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-103">Defines a list format for the view.</span></span>

<span data-ttu-id="b5dd8-104">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément objet ListControl élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b5dd8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5dd8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5dd8-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5dd8-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="b5dd8-106">Attributes and Elements</span></span>

<span data-ttu-id="b5dd8-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ListControl` élément.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="b5dd8-108">Cet élément doit contenir uniquement un seul élément enfant.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5dd8-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="b5dd8-109">Attributes</span></span>

<span data-ttu-id="b5dd8-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5dd8-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b5dd8-111">Child Elements</span></span>

|<span data-ttu-id="b5dd8-112">Élément</span><span class="sxs-lookup"><span data-stu-id="b5dd8-112">Element</span></span>|<span data-ttu-id="b5dd8-113">Description</span><span class="sxs-lookup"><span data-stu-id="b5dd8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5dd8-114">Élément situés (Format)</span><span class="sxs-lookup"><span data-stu-id="b5dd8-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="b5dd8-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-115">Required element.</span></span><br /><br /> <span data-ttu-id="b5dd8-116">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b5dd8-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b5dd8-117">Parent Elements</span></span>

|<span data-ttu-id="b5dd8-118">Élément</span><span class="sxs-lookup"><span data-stu-id="b5dd8-118">Element</span></span>|<span data-ttu-id="b5dd8-119">Description</span><span class="sxs-lookup"><span data-stu-id="b5dd8-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5dd8-120">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="b5dd8-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="b5dd8-121">Définit une vue qui est utilisée pour afficher les membres d’un ou plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b5dd8-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="b5dd8-122">Remarks</span></span>

<span data-ttu-id="b5dd8-123">Pour plus d’informations sur la création d’un affichage de liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b5dd8-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b5dd8-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5dd8-124">Example</span></span>

<span data-ttu-id="b5dd8-125">Cet exemple montre une vue de liste pour le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet.</span><span class="sxs-lookup"><span data-stu-id="b5dd8-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b5dd8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5dd8-126">See Also</span></span>

[<span data-ttu-id="b5dd8-127">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="b5dd8-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="b5dd8-128">Élément situés (Format)</span><span class="sxs-lookup"><span data-stu-id="b5dd8-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="b5dd8-129">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="b5dd8-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b5dd8-130">Écriture d’un mise en forme de Windows PowerShell et de Types de fichier</span><span class="sxs-lookup"><span data-stu-id="b5dd8-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
