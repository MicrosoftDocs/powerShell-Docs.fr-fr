---
ms.date: 09/13/2016
ms.topic: reference
title: Label, élément pour ListItem pour ListControl (Format)
description: Label, élément pour ListItem pour ListControl (Format)
ms.openlocfilehash: 01ff34c4129abe2c76a0a21794e756b77bff12bf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666652"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="be6a5-103">Label, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="be6a5-103">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="be6a5-104">Spécifie l’étiquette affichée à gauche de la valeur de la propriété ou du script dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="be6a5-104">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="be6a5-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément pour ListControl (format) ListEntry, élément pour ListControl (format) ListItems pour l’élément ListControl pour ListControl (format) ListItem, élément de ListItems pour ListControl (format) élément label pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="be6a5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="be6a5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be6a5-106">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="be6a5-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="be6a5-107">Attributes and Elements</span></span>

<span data-ttu-id="be6a5-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Label` élément.</span><span class="sxs-lookup"><span data-stu-id="be6a5-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="be6a5-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="be6a5-109">Attributes</span></span>

<span data-ttu-id="be6a5-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="be6a5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="be6a5-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="be6a5-111">Child Elements</span></span>

<span data-ttu-id="be6a5-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="be6a5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="be6a5-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="be6a5-113">Parent Elements</span></span>

|<span data-ttu-id="be6a5-114">Élément</span><span class="sxs-lookup"><span data-stu-id="be6a5-114">Element</span></span>|<span data-ttu-id="be6a5-115">Description</span><span class="sxs-lookup"><span data-stu-id="be6a5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be6a5-116">ListItem, élément pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="be6a5-116">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="be6a5-117">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="be6a5-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="be6a5-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="be6a5-118">Text Value</span></span>

<span data-ttu-id="be6a5-119">Spécifiez l’étiquette à afficher à gauche de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="be6a5-119">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="be6a5-120">Notes</span><span class="sxs-lookup"><span data-stu-id="be6a5-120">Remarks</span></span>

<span data-ttu-id="be6a5-121">Si aucune étiquette n’est spécifiée, le nom de la propriété ou du script est affiché.</span><span class="sxs-lookup"><span data-stu-id="be6a5-121">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="be6a5-122">Pour plus d’informations sur l’utilisation des étiquettes dans un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="be6a5-122">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="be6a5-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="be6a5-123">Example</span></span>

<span data-ttu-id="be6a5-124">L’exemple suivant montre comment ajouter une étiquette à une ligne.</span><span class="sxs-lookup"><span data-stu-id="be6a5-124">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="be6a5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be6a5-125">See Also</span></span>

[<span data-ttu-id="be6a5-126">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="be6a5-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="be6a5-127">ListItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="be6a5-127">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="be6a5-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="be6a5-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
