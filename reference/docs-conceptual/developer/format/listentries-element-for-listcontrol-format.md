---
ms.date: 09/13/2016
ms.topic: reference
title: ListEntries, élément pour ListControl (Format)
description: ListEntries, élément pour ListControl (Format)
ms.openlocfilehash: d4d6625bb92ea27863fc30d5bf5625f9275e4f69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666601"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="a632b-103">ListEntries, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a632b-103">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="a632b-104">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="a632b-104">Provides the definitions of the list view.</span></span> <span data-ttu-id="a632b-105">Le mode liste doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="a632b-105">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="a632b-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="a632b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a632b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a632b-107">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a632b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a632b-108">Attributes and Elements</span></span>

<span data-ttu-id="a632b-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="a632b-109">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="a632b-110">Au moins un élément enfant doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="a632b-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="a632b-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a632b-111">Attributes</span></span>

<span data-ttu-id="a632b-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a632b-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a632b-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a632b-113">Child Elements</span></span>

|<span data-ttu-id="a632b-114">Élément</span><span class="sxs-lookup"><span data-stu-id="a632b-114">Element</span></span>|<span data-ttu-id="a632b-115">Description</span><span class="sxs-lookup"><span data-stu-id="a632b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a632b-116">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a632b-116">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="a632b-117">Fournit une définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="a632b-117">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a632b-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a632b-118">Parent Elements</span></span>

|<span data-ttu-id="a632b-119">Élément</span><span class="sxs-lookup"><span data-stu-id="a632b-119">Element</span></span>|<span data-ttu-id="a632b-120">Description</span><span class="sxs-lookup"><span data-stu-id="a632b-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a632b-121">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a632b-121">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="a632b-122">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="a632b-122">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a632b-123">Notes</span><span class="sxs-lookup"><span data-stu-id="a632b-123">Remarks</span></span>

<span data-ttu-id="a632b-124">Pour plus d’informations sur les affichages de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a632b-124">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a632b-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="a632b-125">Example</span></span>

<span data-ttu-id="a632b-126">Cet exemple montre les éléments XML qui définissent le mode liste de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="a632b-126">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a632b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a632b-127">See Also</span></span>

[<span data-ttu-id="a632b-128">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a632b-128">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="a632b-129">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a632b-129">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="a632b-130">Mode liste</span><span class="sxs-lookup"><span data-stu-id="a632b-130">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a632b-131">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a632b-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
