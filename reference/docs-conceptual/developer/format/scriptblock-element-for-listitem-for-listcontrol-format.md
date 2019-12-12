---
title: Élément ScriptBlock pour ListItem pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364808"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="7d03b-102">ScriptBlock, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7d03b-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="7d03b-103">Spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="7d03b-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="7d03b-104">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) ListItems, élément de ListEntry pour l’élément ListControl (format) ListItem pour ListItems pour ListControl (format) ScriptBlock, élément pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7d03b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d03b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d03b-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d03b-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="7d03b-106">Attributes and Elements</span></span>

<span data-ttu-id="7d03b-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="7d03b-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d03b-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="7d03b-108">Attributes</span></span>

<span data-ttu-id="7d03b-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="7d03b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d03b-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7d03b-110">Child Elements</span></span>

<span data-ttu-id="7d03b-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="7d03b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7d03b-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7d03b-112">Parent Elements</span></span>

|<span data-ttu-id="7d03b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="7d03b-113">Element</span></span>|<span data-ttu-id="7d03b-114">Description</span><span class="sxs-lookup"><span data-stu-id="7d03b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d03b-115">ListItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="7d03b-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="7d03b-116">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="7d03b-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7d03b-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="7d03b-117">Text Value</span></span>

<span data-ttu-id="7d03b-118">Spécifiez le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="7d03b-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="7d03b-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="7d03b-119">Remarks</span></span>

<span data-ttu-id="7d03b-120">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="7d03b-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="7d03b-121">Pour plus d’informations sur la spécification de scripts dans un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7d03b-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7d03b-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="7d03b-122">Example</span></span>

<span data-ttu-id="7d03b-123">L’exemple suivant montre comment spécifier la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="7d03b-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="7d03b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d03b-124">See Also</span></span>

[<span data-ttu-id="7d03b-125">PropertyName, élément de ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7d03b-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="7d03b-126">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="7d03b-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7d03b-127">Élément ListItem pour ListItems pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7d03b-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="7d03b-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d03b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
