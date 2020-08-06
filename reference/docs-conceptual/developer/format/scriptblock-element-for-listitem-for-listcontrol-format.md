---
title: Élément ScriptBlock pour ListItem pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 249d3e36b4246b7baa410815122f8e30340f1862
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785453"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="6bc98-102">ScriptBlock, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6bc98-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="6bc98-103">Spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="6bc98-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="6bc98-104">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) élément ListItems pour l’élément ListEntry pour ListControl (format) ListItem pour l’élément ListItems pour ListControl (format) ScriptBlock pour ListControl pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="6bc98-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6bc98-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bc98-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6bc98-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6bc98-106">Attributes and Elements</span></span>

<span data-ttu-id="6bc98-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="6bc98-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6bc98-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="6bc98-108">Attributes</span></span>

<span data-ttu-id="6bc98-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6bc98-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6bc98-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6bc98-110">Child Elements</span></span>

<span data-ttu-id="6bc98-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6bc98-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6bc98-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6bc98-112">Parent Elements</span></span>

|<span data-ttu-id="6bc98-113">Élément</span><span class="sxs-lookup"><span data-stu-id="6bc98-113">Element</span></span>|<span data-ttu-id="6bc98-114">Description</span><span class="sxs-lookup"><span data-stu-id="6bc98-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6bc98-115">ListItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="6bc98-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="6bc98-116">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="6bc98-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6bc98-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="6bc98-117">Text Value</span></span>

<span data-ttu-id="6bc98-118">Spécifiez le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="6bc98-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="6bc98-119">Notes</span><span class="sxs-lookup"><span data-stu-id="6bc98-119">Remarks</span></span>

<span data-ttu-id="6bc98-120">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="6bc98-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="6bc98-121">Pour plus d’informations sur la spécification de scripts dans un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6bc98-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6bc98-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="6bc98-122">Example</span></span>

<span data-ttu-id="6bc98-123">L’exemple suivant montre comment spécifier la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="6bc98-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="6bc98-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bc98-124">See Also</span></span>

[<span data-ttu-id="6bc98-125">PropertyName, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6bc98-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="6bc98-126">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="6bc98-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6bc98-127">ListItem, élément pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6bc98-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="6bc98-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="6bc98-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
