---
title: Élément situés pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856785"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="079f2-102">ListEntries, élément pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="079f2-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="079f2-103">Fournit les définitions de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="079f2-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="079f2-104">L’affichage de liste doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="079f2-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="079f2-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément objet ListControl, élément (Format) situés élément (Format)</span><span class="sxs-lookup"><span data-stu-id="079f2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="079f2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="079f2-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="079f2-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="079f2-107">Attributes and Elements</span></span>

<span data-ttu-id="079f2-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ListEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="079f2-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="079f2-109">Au moins un élément enfant doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="079f2-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="079f2-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="079f2-110">Attributes</span></span>

<span data-ttu-id="079f2-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="079f2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="079f2-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="079f2-112">Child Elements</span></span>

|<span data-ttu-id="079f2-113">Élément</span><span class="sxs-lookup"><span data-stu-id="079f2-113">Element</span></span>|<span data-ttu-id="079f2-114">Description</span><span class="sxs-lookup"><span data-stu-id="079f2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="079f2-115">Élément ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="079f2-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="079f2-116">Fournit une définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="079f2-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="079f2-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="079f2-117">Parent Elements</span></span>

|<span data-ttu-id="079f2-118">Élément</span><span class="sxs-lookup"><span data-stu-id="079f2-118">Element</span></span>|<span data-ttu-id="079f2-119">Description</span><span class="sxs-lookup"><span data-stu-id="079f2-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="079f2-120">Élément objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="079f2-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="079f2-121">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="079f2-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="079f2-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="079f2-122">Remarks</span></span>

<span data-ttu-id="079f2-123">Pour plus d’informations sur les affichages de liste, consultez [mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="079f2-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="079f2-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="079f2-124">Example</span></span>

<span data-ttu-id="079f2-125">Cet exemple montre les éléments XML qui définissent l’affichage de liste pour le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet.</span><span class="sxs-lookup"><span data-stu-id="079f2-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="079f2-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="079f2-126">See Also</span></span>

[<span data-ttu-id="079f2-127">Élément objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="079f2-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="079f2-128">Élément ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="079f2-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="079f2-129">Affichage de liste</span><span class="sxs-lookup"><span data-stu-id="079f2-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="079f2-130">Écriture d’un mise en forme de Windows PowerShell et de Types de fichier</span><span class="sxs-lookup"><span data-stu-id="079f2-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
