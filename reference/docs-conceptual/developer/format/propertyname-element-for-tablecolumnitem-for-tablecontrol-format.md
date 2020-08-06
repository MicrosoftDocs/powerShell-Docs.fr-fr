---
title: PropertyName, élément de TableColumnItem pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bf267eeb83aef59abea2d945af12e849252309c8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772975"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="2b64c-102">PropertyName, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2b64c-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="2b64c-103">Spécifie la propriété dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2b64c-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="2b64c-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) TableColumnItems élément (format) TableColumnItem élément (format) PropertyName élément pour TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="2b64c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b64c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b64c-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b64c-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2b64c-106">Attributes and Elements</span></span>

<span data-ttu-id="2b64c-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="2b64c-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b64c-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="2b64c-108">Attributes</span></span>

<span data-ttu-id="2b64c-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2b64c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b64c-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2b64c-110">Child Elements</span></span>

<span data-ttu-id="2b64c-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2b64c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b64c-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2b64c-112">Parent Elements</span></span>

|<span data-ttu-id="2b64c-113">Élément</span><span class="sxs-lookup"><span data-stu-id="2b64c-113">Element</span></span>|<span data-ttu-id="2b64c-114">Description</span><span class="sxs-lookup"><span data-stu-id="2b64c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b64c-115">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="2b64c-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="2b64c-116">Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2b64c-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2b64c-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="2b64c-117">Text Value</span></span>

<span data-ttu-id="2b64c-118">Spécifiez le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="2b64c-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b64c-119">Notes</span><span class="sxs-lookup"><span data-stu-id="2b64c-119">Remarks</span></span>

<span data-ttu-id="2b64c-120">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="2b64c-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2b64c-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="2b64c-121">Example</span></span>

<span data-ttu-id="2b64c-122">Cet exemple montre un `TableColumnItem` élément qui spécifie la `Status` propriété de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="2b64c-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="2b64c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b64c-123">See Also</span></span>

[<span data-ttu-id="2b64c-124">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="2b64c-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2b64c-125">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="2b64c-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="2b64c-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b64c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
