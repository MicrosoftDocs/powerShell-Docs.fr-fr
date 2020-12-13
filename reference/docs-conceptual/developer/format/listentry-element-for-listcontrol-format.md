---
ms.date: 09/13/2016
ms.topic: reference
title: ListEntry, élément pour ListControl (Format)
description: ListEntry, élément pour ListControl (Format)
ms.openlocfilehash: 96ae5fcdd837d2491d6c7ff6a375fef1d83ae3e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666567"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="edc7c-103">ListEntry, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="edc7c-103">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="edc7c-104">Fournit une définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="edc7c-104">Provides a definition of the list view.</span></span>

<span data-ttu-id="edc7c-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format)</span><span class="sxs-lookup"><span data-stu-id="edc7c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="edc7c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edc7c-106">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="edc7c-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="edc7c-107">Attributes and Elements</span></span>

<span data-ttu-id="edc7c-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="edc7c-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="edc7c-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="edc7c-109">Attributes</span></span>

<span data-ttu-id="edc7c-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="edc7c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="edc7c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="edc7c-111">Child Elements</span></span>

|<span data-ttu-id="edc7c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="edc7c-112">Element</span></span>|<span data-ttu-id="edc7c-113">Description</span><span class="sxs-lookup"><span data-stu-id="edc7c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="edc7c-114">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="edc7c-114">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="edc7c-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="edc7c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="edc7c-116">Définit les objets .NET qui utilisent cette définition de vue de liste ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="edc7c-116">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="edc7c-117">Élément ListItems (format)</span><span class="sxs-lookup"><span data-stu-id="edc7c-117">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="edc7c-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="edc7c-118">Required element.</span></span><br /><br /> <span data-ttu-id="edc7c-119">Définit les propriétés et les scripts dont les valeurs sont affichées par la vue liste.</span><span class="sxs-lookup"><span data-stu-id="edc7c-119">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="edc7c-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="edc7c-120">Parent Elements</span></span>

|<span data-ttu-id="edc7c-121">Élément</span><span class="sxs-lookup"><span data-stu-id="edc7c-121">Element</span></span>|<span data-ttu-id="edc7c-122">Description</span><span class="sxs-lookup"><span data-stu-id="edc7c-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="edc7c-123">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="edc7c-123">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="edc7c-124">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="edc7c-124">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="edc7c-125">Notes</span><span class="sxs-lookup"><span data-stu-id="edc7c-125">Remarks</span></span>

<span data-ttu-id="edc7c-126">Un affichage de liste est un format de liste qui affiche des valeurs de propriété ou des valeurs de script pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="edc7c-126">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="edc7c-127">Pour plus d’informations sur les affichages de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="edc7c-127">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="edc7c-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="edc7c-128">Example</span></span>

<span data-ttu-id="edc7c-129">Cet exemple montre les éléments XML qui définissent le mode liste de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="edc7c-129">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="edc7c-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edc7c-130">See Also</span></span>

[<span data-ttu-id="edc7c-131">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="edc7c-131">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="edc7c-132">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="edc7c-132">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="edc7c-133">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="edc7c-133">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="edc7c-134">Élément ListItems (format)</span><span class="sxs-lookup"><span data-stu-id="edc7c-134">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="edc7c-135">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="edc7c-135">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
