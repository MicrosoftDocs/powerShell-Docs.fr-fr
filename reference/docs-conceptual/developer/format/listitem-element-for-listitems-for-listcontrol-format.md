---
title: Élément ListItem pour ListItems pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365128"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="672e4-102">ListItem, élément pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="672e4-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="672e4-103">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="672e4-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="672e4-104">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément pour ListControl (format) ListEntry, élément de ListControl (format) élément ListItems pour ListControl (format) ListItem pour l’élément ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="672e4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="672e4-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="672e4-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="672e4-106">Attributes and Elements</span></span>

<span data-ttu-id="672e4-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ListItem`.</span><span class="sxs-lookup"><span data-stu-id="672e4-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="672e4-108">Une seule propriété ou un seul script peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="672e4-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="672e4-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="672e4-109">Attributes</span></span>

<span data-ttu-id="672e4-110">aucune.</span><span class="sxs-lookup"><span data-stu-id="672e4-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="672e4-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="672e4-111">Child Elements</span></span>

|<span data-ttu-id="672e4-112">Élément</span><span class="sxs-lookup"><span data-stu-id="672e4-112">Element</span></span>|<span data-ttu-id="672e4-113">Description</span><span class="sxs-lookup"><span data-stu-id="672e4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="672e4-114">FormatString, élément de ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="672e4-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="672e4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="672e4-116">Spécifie une chaîne de format qui définit le mode d’affichage de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="672e4-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="672e4-117">Élément ItemSelectionCondition pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="672e4-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="672e4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="672e4-119">Définit la condition qui doit exister pour l’élément de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="672e4-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="672e4-120">Élément label pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="672e4-121">Élément facultatif</span><span class="sxs-lookup"><span data-stu-id="672e4-121">Optional element</span></span><br /><br /> <span data-ttu-id="672e4-122">Spécifie l’étiquette affichée à gauche de la valeur de la propriété ou du script dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="672e4-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="672e4-123">PropertyName, élément de ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="672e4-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="672e4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="672e4-125">Spécifie la propriété .NET dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="672e4-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="672e4-126">Élément ScriptBlock pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="672e4-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="672e4-127">Optional element.</span></span><br /><br /> <span data-ttu-id="672e4-128">Spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="672e4-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="672e4-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="672e4-129">Parent Elements</span></span>

|<span data-ttu-id="672e4-130">Élément</span><span class="sxs-lookup"><span data-stu-id="672e4-130">Element</span></span>|<span data-ttu-id="672e4-131">Description</span><span class="sxs-lookup"><span data-stu-id="672e4-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="672e4-132">Élément ListItems pour le contrôle List (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="672e4-133">Définit les propriétés et les scripts dont les valeurs sont affichées en mode liste.</span><span class="sxs-lookup"><span data-stu-id="672e4-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="672e4-134">Remarks</span><span class="sxs-lookup"><span data-stu-id="672e4-134">Remarks</span></span>

<span data-ttu-id="672e4-135">Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="672e4-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="672e4-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="672e4-136">Example</span></span>

<span data-ttu-id="672e4-137">Cet exemple montre les éléments XML qui définissent trois lignes de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="672e4-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="672e4-138">Les deux premières lignes affichent la valeur d’une propriété .NET et la dernière ligne affiche une valeur générée par un script.</span><span class="sxs-lookup"><span data-stu-id="672e4-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="672e4-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="672e4-139">See Also</span></span>

[<span data-ttu-id="672e4-140">Élément ListItems (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="672e4-141">Élément FormatString pour ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="672e4-142">Élément label pour ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="672e4-143">PropertyName, élément de ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="672e4-144">Élément ScriptBlock pour ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="672e4-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="672e4-145">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="672e4-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="672e4-146">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="672e4-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
