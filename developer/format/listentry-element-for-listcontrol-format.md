---
title: Élément ListEntry pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862245"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="6963f-102">ListEntry, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6963f-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="6963f-103">Fournit une définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="6963f-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="6963f-104">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry élément (Format)</span><span class="sxs-lookup"><span data-stu-id="6963f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6963f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6963f-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6963f-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="6963f-106">Attributes and Elements</span></span>

<span data-ttu-id="6963f-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ListEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="6963f-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6963f-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="6963f-108">Attributes</span></span>

<span data-ttu-id="6963f-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6963f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6963f-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6963f-110">Child Elements</span></span>

|<span data-ttu-id="6963f-111">Élément</span><span class="sxs-lookup"><span data-stu-id="6963f-111">Element</span></span>|<span data-ttu-id="6963f-112">Description</span><span class="sxs-lookup"><span data-stu-id="6963f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6963f-113">Élément EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6963f-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="6963f-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="6963f-114">Optional element.</span></span><br /><br /> <span data-ttu-id="6963f-115">Définit les objets .NET qui utilisent cette définition de la vue liste ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6963f-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="6963f-116">Élément ListItems (Format)</span><span class="sxs-lookup"><span data-stu-id="6963f-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="6963f-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="6963f-117">Required element.</span></span><br /><br /> <span data-ttu-id="6963f-118">Définit les propriétés et les scripts dont les valeurs sont affichées par la vue de liste.</span><span class="sxs-lookup"><span data-stu-id="6963f-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6963f-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6963f-119">Parent Elements</span></span>

|<span data-ttu-id="6963f-120">Élément</span><span class="sxs-lookup"><span data-stu-id="6963f-120">Element</span></span>|<span data-ttu-id="6963f-121">Description</span><span class="sxs-lookup"><span data-stu-id="6963f-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6963f-122">Élément situés (Format)</span><span class="sxs-lookup"><span data-stu-id="6963f-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="6963f-123">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="6963f-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6963f-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="6963f-124">Remarks</span></span>

<span data-ttu-id="6963f-125">Un affichage de liste est un format de liste qui affiche les valeurs de propriété ou de valeurs de script pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="6963f-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="6963f-126">Pour plus d’informations sur les affichages de liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6963f-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6963f-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="6963f-127">Example</span></span>

<span data-ttu-id="6963f-128">Cet exemple montre les éléments XML qui définissent l’affichage de liste pour le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet.</span><span class="sxs-lookup"><span data-stu-id="6963f-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6963f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6963f-129">See Also</span></span>

[<span data-ttu-id="6963f-130">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="6963f-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6963f-131">Élément EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6963f-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="6963f-132">Élément situés (Format)</span><span class="sxs-lookup"><span data-stu-id="6963f-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="6963f-133">Élément ListItems (Format)</span><span class="sxs-lookup"><span data-stu-id="6963f-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="6963f-134">Écriture d’un mise en forme de Windows PowerShell et de Types de fichier</span><span class="sxs-lookup"><span data-stu-id="6963f-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
