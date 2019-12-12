---
title: Élément ListItems pour ListEntry pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362738"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="494c1-102">ListItems, élément pour ListEntry pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="494c1-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="494c1-103">Définit les propriétés et les scripts dont les valeurs sont affichées dans les lignes de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="494c1-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="494c1-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) ListControl, élément (format) ListEntries, élément pour le contrôle de liste (format) ListEntry, élément de ListControl (format) élément ListItems pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="494c1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="494c1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="494c1-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="494c1-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="494c1-106">Attributes and Elements</span></span>

<span data-ttu-id="494c1-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ListItems`.</span><span class="sxs-lookup"><span data-stu-id="494c1-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="494c1-108">Il n’existe aucune limite quant au nombre d’éléments enfants qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="494c1-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="494c1-109">L’ordre des éléments enfants définit l’ordre dans lequel les valeurs sont affichées en mode liste.</span><span class="sxs-lookup"><span data-stu-id="494c1-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="494c1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="494c1-110">Attributes</span></span>

<span data-ttu-id="494c1-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="494c1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="494c1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="494c1-112">Child Elements</span></span>

|<span data-ttu-id="494c1-113">Élément</span><span class="sxs-lookup"><span data-stu-id="494c1-113">Element</span></span>|<span data-ttu-id="494c1-114">Description</span><span class="sxs-lookup"><span data-stu-id="494c1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="494c1-115">Élément ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="494c1-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="494c1-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="494c1-116">Required element.</span></span><br /><br /> <span data-ttu-id="494c1-117">Définit la propriété ou le script dont la valeur est affichée par le mode liste.</span><span class="sxs-lookup"><span data-stu-id="494c1-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="494c1-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="494c1-118">Parent Elements</span></span>

|<span data-ttu-id="494c1-119">Élément</span><span class="sxs-lookup"><span data-stu-id="494c1-119">Element</span></span>|<span data-ttu-id="494c1-120">Description</span><span class="sxs-lookup"><span data-stu-id="494c1-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="494c1-121">Élément ListEntry pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="494c1-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="494c1-122">Fournit une définition de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="494c1-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="494c1-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="494c1-123">Remarks</span></span>

<span data-ttu-id="494c1-124">Pour plus d’informations sur ce type d’affichage, consultez [création d’un affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="494c1-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="494c1-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="494c1-125">Example</span></span>

<span data-ttu-id="494c1-126">Cet exemple montre les éléments XML qui définissent trois lignes de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="494c1-126">This example shows the XML elements that define three rows of the list view.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="494c1-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="494c1-127">See Also</span></span>

[<span data-ttu-id="494c1-128">Élément ListEntry pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="494c1-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="494c1-129">Élément ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="494c1-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="494c1-130">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="494c1-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="494c1-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="494c1-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
