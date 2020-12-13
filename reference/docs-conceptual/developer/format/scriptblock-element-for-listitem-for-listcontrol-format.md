---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour ListItem pour ListControl (Format)
description: ScriptBlock, élément pour ListItem pour ListControl (Format)
ms.openlocfilehash: 0635ac2622cc203a2dc895873621901d956f87da
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664972"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="dbfe3-103">ScriptBlock, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dbfe3-103">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="dbfe3-104">Spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="dbfe3-104">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="dbfe3-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) élément ListItems pour l’élément ListEntry pour ListControl (format) ListItem pour l’élément ListItems pour ListControl (format) ScriptBlock pour ListControl pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="dbfe3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dbfe3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbfe3-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dbfe3-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dbfe3-107">Attributes and Elements</span></span>

<span data-ttu-id="dbfe3-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="dbfe3-108">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dbfe3-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="dbfe3-109">Attributes</span></span>

<span data-ttu-id="dbfe3-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dbfe3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dbfe3-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dbfe3-111">Child Elements</span></span>

<span data-ttu-id="dbfe3-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dbfe3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dbfe3-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dbfe3-113">Parent Elements</span></span>

|<span data-ttu-id="dbfe3-114">Élément</span><span class="sxs-lookup"><span data-stu-id="dbfe3-114">Element</span></span>|<span data-ttu-id="dbfe3-115">Description</span><span class="sxs-lookup"><span data-stu-id="dbfe3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dbfe3-116">ListItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="dbfe3-116">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="dbfe3-117">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="dbfe3-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dbfe3-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="dbfe3-118">Text Value</span></span>

<span data-ttu-id="dbfe3-119">Spécifiez le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="dbfe3-119">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="dbfe3-120">Notes</span><span class="sxs-lookup"><span data-stu-id="dbfe3-120">Remarks</span></span>

<span data-ttu-id="dbfe3-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="dbfe3-121">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="dbfe3-122">Pour plus d’informations sur la spécification de scripts dans un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="dbfe3-122">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dbfe3-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="dbfe3-123">Example</span></span>

<span data-ttu-id="dbfe3-124">L’exemple suivant montre comment spécifier la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="dbfe3-124">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="dbfe3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbfe3-125">See Also</span></span>

[<span data-ttu-id="dbfe3-126">PropertyName, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dbfe3-126">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="dbfe3-127">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="dbfe3-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="dbfe3-128">ListItem, élément pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dbfe3-128">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="dbfe3-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbfe3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
