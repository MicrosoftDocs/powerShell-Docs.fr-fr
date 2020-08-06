---
title: Élément ListEntry pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d98f0b5215eea7668f866d2733214ade79d748f1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785691"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="ebee3-102">ListEntry, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ebee3-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="ebee3-103">Fournit une définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="ebee3-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="ebee3-104">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format)</span><span class="sxs-lookup"><span data-stu-id="ebee3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ebee3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebee3-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ebee3-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ebee3-106">Attributes and Elements</span></span>

<span data-ttu-id="ebee3-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="ebee3-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ebee3-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="ebee3-108">Attributes</span></span>

<span data-ttu-id="ebee3-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ebee3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ebee3-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ebee3-110">Child Elements</span></span>

|<span data-ttu-id="ebee3-111">Élément</span><span class="sxs-lookup"><span data-stu-id="ebee3-111">Element</span></span>|<span data-ttu-id="ebee3-112">Description</span><span class="sxs-lookup"><span data-stu-id="ebee3-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ebee3-113">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ebee3-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="ebee3-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ebee3-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ebee3-115">Définit les objets .NET qui utilisent cette définition de vue de liste ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="ebee3-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="ebee3-116">Élément ListItems (format)</span><span class="sxs-lookup"><span data-stu-id="ebee3-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="ebee3-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="ebee3-117">Required element.</span></span><br /><br /> <span data-ttu-id="ebee3-118">Définit les propriétés et les scripts dont les valeurs sont affichées par la vue liste.</span><span class="sxs-lookup"><span data-stu-id="ebee3-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ebee3-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ebee3-119">Parent Elements</span></span>

|<span data-ttu-id="ebee3-120">Élément</span><span class="sxs-lookup"><span data-stu-id="ebee3-120">Element</span></span>|<span data-ttu-id="ebee3-121">Description</span><span class="sxs-lookup"><span data-stu-id="ebee3-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ebee3-122">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="ebee3-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="ebee3-123">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="ebee3-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ebee3-124">Notes</span><span class="sxs-lookup"><span data-stu-id="ebee3-124">Remarks</span></span>

<span data-ttu-id="ebee3-125">Un affichage de liste est un format de liste qui affiche des valeurs de propriété ou des valeurs de script pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="ebee3-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="ebee3-126">Pour plus d’informations sur les affichages de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="ebee3-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ebee3-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="ebee3-127">Example</span></span>

<span data-ttu-id="ebee3-128">Cet exemple montre les éléments XML qui définissent le mode liste de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="ebee3-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ebee3-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebee3-129">See Also</span></span>

[<span data-ttu-id="ebee3-130">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="ebee3-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ebee3-131">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ebee3-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="ebee3-132">ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="ebee3-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="ebee3-133">Élément ListItems (format)</span><span class="sxs-lookup"><span data-stu-id="ebee3-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="ebee3-134">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ebee3-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
