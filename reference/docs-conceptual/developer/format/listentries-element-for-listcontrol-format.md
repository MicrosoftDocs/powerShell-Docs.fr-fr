---
title: Élément ListEntries pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0fe07e739c2d2fec153599ec6c0c0b3ecc14df18
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785708"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="4dc3f-102">ListEntries, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4dc3f-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="4dc3f-103">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="4dc3f-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="4dc3f-104">Le mode liste doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="4dc3f-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="4dc3f-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="4dc3f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4dc3f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dc3f-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4dc3f-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4dc3f-107">Attributes and Elements</span></span>

<span data-ttu-id="4dc3f-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="4dc3f-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="4dc3f-109">Au moins un élément enfant doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="4dc3f-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="4dc3f-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4dc3f-110">Attributes</span></span>

<span data-ttu-id="4dc3f-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4dc3f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4dc3f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4dc3f-112">Child Elements</span></span>

|<span data-ttu-id="4dc3f-113">Élément</span><span class="sxs-lookup"><span data-stu-id="4dc3f-113">Element</span></span>|<span data-ttu-id="4dc3f-114">Description</span><span class="sxs-lookup"><span data-stu-id="4dc3f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4dc3f-115">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="4dc3f-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="4dc3f-116">Fournit une définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="4dc3f-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4dc3f-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4dc3f-117">Parent Elements</span></span>

|<span data-ttu-id="4dc3f-118">Élément</span><span class="sxs-lookup"><span data-stu-id="4dc3f-118">Element</span></span>|<span data-ttu-id="4dc3f-119">Description</span><span class="sxs-lookup"><span data-stu-id="4dc3f-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4dc3f-120">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="4dc3f-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="4dc3f-121">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="4dc3f-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4dc3f-122">Notes</span><span class="sxs-lookup"><span data-stu-id="4dc3f-122">Remarks</span></span>

<span data-ttu-id="4dc3f-123">Pour plus d’informations sur les affichages de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="4dc3f-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4dc3f-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="4dc3f-124">Example</span></span>

<span data-ttu-id="4dc3f-125">Cet exemple montre les éléments XML qui définissent le mode liste de l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="4dc3f-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4dc3f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dc3f-126">See Also</span></span>

[<span data-ttu-id="4dc3f-127">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="4dc3f-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="4dc3f-128">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="4dc3f-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="4dc3f-129">Mode liste</span><span class="sxs-lookup"><span data-stu-id="4dc3f-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4dc3f-130">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4dc3f-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
