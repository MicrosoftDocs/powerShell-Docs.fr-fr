---
title: Élément ListEntries pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362758"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="a3ec7-102">ListEntries, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a3ec7-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="a3ec7-103">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="a3ec7-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="a3ec7-104">Le mode liste doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="a3ec7-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="a3ec7-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="a3ec7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a3ec7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3ec7-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a3ec7-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="a3ec7-107">Attributes and Elements</span></span>

<span data-ttu-id="a3ec7-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ListEntries`.</span><span class="sxs-lookup"><span data-stu-id="a3ec7-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="a3ec7-109">Au moins un élément enfant doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="a3ec7-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="a3ec7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a3ec7-110">Attributes</span></span>

<span data-ttu-id="a3ec7-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="a3ec7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a3ec7-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a3ec7-112">Child Elements</span></span>

|<span data-ttu-id="a3ec7-113">Élément</span><span class="sxs-lookup"><span data-stu-id="a3ec7-113">Element</span></span>|<span data-ttu-id="a3ec7-114">Description</span><span class="sxs-lookup"><span data-stu-id="a3ec7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3ec7-115">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a3ec7-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="a3ec7-116">Fournit une définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="a3ec7-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a3ec7-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a3ec7-117">Parent Elements</span></span>

|<span data-ttu-id="a3ec7-118">Élément</span><span class="sxs-lookup"><span data-stu-id="a3ec7-118">Element</span></span>|<span data-ttu-id="a3ec7-119">Description</span><span class="sxs-lookup"><span data-stu-id="a3ec7-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3ec7-120">Élément ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="a3ec7-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="a3ec7-121">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="a3ec7-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a3ec7-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="a3ec7-122">Remarks</span></span>

<span data-ttu-id="a3ec7-123">Pour plus d’informations sur les affichages de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a3ec7-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a3ec7-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="a3ec7-124">Example</span></span>

<span data-ttu-id="a3ec7-125">Cet exemple montre les éléments XML qui définissent le mode liste de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="a3ec7-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="a3ec7-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3ec7-126">See Also</span></span>

[<span data-ttu-id="a3ec7-127">Élément ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="a3ec7-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="a3ec7-128">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a3ec7-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="a3ec7-129">Mode liste</span><span class="sxs-lookup"><span data-stu-id="a3ec7-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a3ec7-130">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3ec7-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
