---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour ListItem pour ListControl (Format)
description: PropertyName, élément pour ListItem pour ListControl (Format)
ms.openlocfilehash: 30cd48f9549e1a091776cd5f8395e1a71314ea1b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665972"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="dce63-103">PropertyName, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dce63-103">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="dce63-104">Spécifie la propriété .NET dont la valeur est affichée dans la liste.</span><span class="sxs-lookup"><span data-stu-id="dce63-104">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="dce63-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) ListItems élément (format) élément ListItem (format) NomPropriété, élément pour ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="dce63-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dce63-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dce63-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dce63-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dce63-107">Attributes and Elements</span></span>

<span data-ttu-id="dce63-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="dce63-108">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dce63-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="dce63-109">Attributes</span></span>

<span data-ttu-id="dce63-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dce63-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dce63-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dce63-111">Child Elements</span></span>

<span data-ttu-id="dce63-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dce63-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dce63-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dce63-113">Parent Elements</span></span>

|<span data-ttu-id="dce63-114">Élément</span><span class="sxs-lookup"><span data-stu-id="dce63-114">Element</span></span>|<span data-ttu-id="dce63-115">Description</span><span class="sxs-lookup"><span data-stu-id="dce63-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dce63-116">ListItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="dce63-116">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="dce63-117">Définit la propriété ou le script dont la valeur est affichée dans la ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="dce63-117">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dce63-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="dce63-118">Text Value</span></span>

<span data-ttu-id="dce63-119">Spécifiez le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="dce63-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="dce63-120">Notes</span><span class="sxs-lookup"><span data-stu-id="dce63-120">Remarks</span></span>

<span data-ttu-id="dce63-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="dce63-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="dce63-122">Outre l’affichage de la valeur de propriété, vous pouvez également spécifier une étiquette pour la valeur ou une chaîne de format qui peut être utilisée pour modifier l’affichage de la valeur.</span><span class="sxs-lookup"><span data-stu-id="dce63-122">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="dce63-123">Pour plus d’informations sur la spécification des données dans un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="dce63-123">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dce63-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="dce63-124">Example</span></span>

<span data-ttu-id="dce63-125">L’exemple suivant montre comment spécifier l’étiquette et la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="dce63-125">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="dce63-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dce63-126">See Also</span></span>

[<span data-ttu-id="dce63-127">ScriptBlock, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dce63-127">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="dce63-128">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="dce63-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="dce63-129">Élément ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="dce63-129">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="dce63-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="dce63-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
