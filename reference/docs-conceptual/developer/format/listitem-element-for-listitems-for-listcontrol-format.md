---
ms.date: 09/13/2016
ms.topic: reference
title: ListItem, élément pour ListItems pour ListControl (Format)
description: ListItem, élément pour ListItems pour ListControl (Format)
ms.openlocfilehash: 999491b7851aa4fa21667ad376d7e9853500ca08
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666550"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="84917-103">ListItem, élément pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84917-103">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="84917-104">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="84917-104">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="84917-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément pour ListControl (format) ListEntry, élément de ListControl (format) élément ListItems pour ListControl (format) ListItem pour l’élément ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="84917-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84917-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84917-106">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="84917-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="84917-107">Attributes and Elements</span></span>

<span data-ttu-id="84917-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ListItem` élément.</span><span class="sxs-lookup"><span data-stu-id="84917-108">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="84917-109">Une seule propriété ou un seul script peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="84917-109">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="84917-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="84917-110">Attributes</span></span>

<span data-ttu-id="84917-111">None</span><span class="sxs-lookup"><span data-stu-id="84917-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="84917-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="84917-112">Child Elements</span></span>

|<span data-ttu-id="84917-113">Élément</span><span class="sxs-lookup"><span data-stu-id="84917-113">Element</span></span>|<span data-ttu-id="84917-114">Description</span><span class="sxs-lookup"><span data-stu-id="84917-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84917-115">FormatString, élément de ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="84917-115">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="84917-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="84917-116">Optional element.</span></span><br /><br /> <span data-ttu-id="84917-117">Spécifie une chaîne de format qui définit le mode d’affichage de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="84917-117">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="84917-118">ItemSelectionCondition, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84917-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="84917-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="84917-119">Optional element.</span></span><br /><br /> <span data-ttu-id="84917-120">Définit la condition qui doit exister pour l’élément de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="84917-120">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="84917-121">Label, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84917-121">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="84917-122">Élément facultatif</span><span class="sxs-lookup"><span data-stu-id="84917-122">Optional element</span></span><br /><br /> <span data-ttu-id="84917-123">Spécifie l’étiquette affichée à gauche de la valeur de la propriété ou du script dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="84917-123">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="84917-124">PropertyName, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84917-124">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="84917-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="84917-125">Optional element.</span></span><br /><br /> <span data-ttu-id="84917-126">Spécifie la propriété .NET dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="84917-126">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="84917-127">ScriptBlock, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84917-127">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="84917-128">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="84917-128">Optional element.</span></span><br /><br /> <span data-ttu-id="84917-129">Spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="84917-129">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="84917-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="84917-130">Parent Elements</span></span>

|<span data-ttu-id="84917-131">Élément</span><span class="sxs-lookup"><span data-stu-id="84917-131">Element</span></span>|<span data-ttu-id="84917-132">Description</span><span class="sxs-lookup"><span data-stu-id="84917-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84917-133">Élément ListItems pour le contrôle List (format)</span><span class="sxs-lookup"><span data-stu-id="84917-133">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="84917-134">Définit les propriétés et les scripts dont les valeurs sont affichées en mode liste.</span><span class="sxs-lookup"><span data-stu-id="84917-134">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="84917-135">Notes</span><span class="sxs-lookup"><span data-stu-id="84917-135">Remarks</span></span>

<span data-ttu-id="84917-136">Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="84917-136">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="84917-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="84917-137">Example</span></span>

<span data-ttu-id="84917-138">Cet exemple montre les éléments XML qui définissent trois lignes de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="84917-138">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="84917-139">Les deux premières lignes affichent la valeur d’une propriété .NET et la dernière ligne affiche une valeur générée par un script.</span><span class="sxs-lookup"><span data-stu-id="84917-139">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="84917-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84917-140">See Also</span></span>

[<span data-ttu-id="84917-141">Élément ListItems (format)</span><span class="sxs-lookup"><span data-stu-id="84917-141">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="84917-142">Élément FormatString pour ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="84917-142">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="84917-143">Élément label pour ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="84917-143">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="84917-144">PropertyName, élément de ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="84917-144">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="84917-145">Élément ScriptBlock pour ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="84917-145">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="84917-146">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="84917-146">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="84917-147">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="84917-147">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
