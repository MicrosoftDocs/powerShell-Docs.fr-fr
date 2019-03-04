---
title: Élément ListItem pour ListItems pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855155"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="bb400-102">ListItem, élément pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="bb400-103">Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="bb400-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="bb400-104">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément objet ListControl, élément (Format) situés élément d’élément de ListEntry ListControl (Format) d’élément de ListItems ListControl (Format) pour l’objet ListControl (Format) ListItem pour l’élément objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bb400-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb400-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bb400-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="bb400-106">Attributes and Elements</span></span>

<span data-ttu-id="bb400-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `ListItem` élément.</span><span class="sxs-lookup"><span data-stu-id="bb400-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="bb400-108">Peut être spécifié qu’une seule propriété ou script.</span><span class="sxs-lookup"><span data-stu-id="bb400-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="bb400-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="bb400-109">Attributes</span></span>

<span data-ttu-id="bb400-110">Aucune</span><span class="sxs-lookup"><span data-stu-id="bb400-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="bb400-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bb400-111">Child Elements</span></span>

|<span data-ttu-id="bb400-112">Élément</span><span class="sxs-lookup"><span data-stu-id="bb400-112">Element</span></span>|<span data-ttu-id="bb400-113">Description</span><span class="sxs-lookup"><span data-stu-id="bb400-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bb400-114">Élément FormatString de ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bb400-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb400-115">Optional element.</span></span><br /><br /> <span data-ttu-id="bb400-116">Spécifie une chaîne de format qui définit comment la valeur de propriété ou un script s’affiche.</span><span class="sxs-lookup"><span data-stu-id="bb400-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="bb400-117">Élément ItemSelectionCondition pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bb400-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb400-118">Optional element.</span></span><br /><br /> <span data-ttu-id="bb400-119">Définit la condition qui doit exister pour cet élément de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="bb400-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="bb400-120">Élément Label pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bb400-121">Élément facultatif</span><span class="sxs-lookup"><span data-stu-id="bb400-121">Optional element</span></span><br /><br /> <span data-ttu-id="bb400-122">Spécifie l’étiquette qui s’affiche à gauche de la valeur de propriété ou un script dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="bb400-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="bb400-123">Élément PropertyName pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bb400-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb400-124">Optional element.</span></span><br /><br /> <span data-ttu-id="bb400-125">Spécifie la propriété .NET dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="bb400-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="bb400-126">Élément ScriptBlock pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="bb400-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="bb400-127">Optional element.</span></span><br /><br /> <span data-ttu-id="bb400-128">Spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="bb400-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bb400-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bb400-129">Parent Elements</span></span>

|<span data-ttu-id="bb400-130">Élément</span><span class="sxs-lookup"><span data-stu-id="bb400-130">Element</span></span>|<span data-ttu-id="bb400-131">Description</span><span class="sxs-lookup"><span data-stu-id="bb400-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bb400-132">Élément ListItems pour le contrôle de liste (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="bb400-133">Définit les propriétés et les scripts dont les valeurs sont affichées dans la vue liste.</span><span class="sxs-lookup"><span data-stu-id="bb400-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bb400-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="bb400-134">Remarks</span></span>

<span data-ttu-id="bb400-135">Pour plus d’informations sur les composants d’une vue liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="bb400-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bb400-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb400-136">Example</span></span>

<span data-ttu-id="bb400-137">Cet exemple montre les éléments XML qui définissent les trois lignes de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="bb400-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="bb400-138">Les deux premières lignes affichent la valeur d’une propriété .NET, et la dernière ligne affiche une valeur générée par un script.</span><span class="sxs-lookup"><span data-stu-id="bb400-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="bb400-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb400-139">See Also</span></span>

[<span data-ttu-id="bb400-140">Élément ListItems (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="bb400-141">Élément FormatString de ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="bb400-142">Élément Label pour ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="bb400-143">Élément PropertyName pour ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="bb400-144">Élément ScriptBlock pour ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="bb400-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="bb400-145">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="bb400-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="bb400-146">Écriture d’un mise en forme de Windows PowerShell et de Types de fichier</span><span class="sxs-lookup"><span data-stu-id="bb400-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
