---
title: PropertyName, élément de TableColumnItem pour table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362248"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="c597d-102">PropertyName, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c597d-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="c597d-103">Spécifie la propriété dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="c597d-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="c597d-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) TableColumnItems élément (format) TableColumnItem, élément (format) PropertyName, élément de TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="c597d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c597d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c597d-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c597d-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="c597d-106">Attributes and Elements</span></span>

<span data-ttu-id="c597d-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="c597d-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c597d-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="c597d-108">Attributes</span></span>

<span data-ttu-id="c597d-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c597d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c597d-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c597d-110">Child Elements</span></span>

<span data-ttu-id="c597d-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c597d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c597d-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c597d-112">Parent Elements</span></span>

|<span data-ttu-id="c597d-113">Élément</span><span class="sxs-lookup"><span data-stu-id="c597d-113">Element</span></span>|<span data-ttu-id="c597d-114">Description</span><span class="sxs-lookup"><span data-stu-id="c597d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c597d-115">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="c597d-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="c597d-116">Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="c597d-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c597d-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="c597d-117">Text Value</span></span>

<span data-ttu-id="c597d-118">Spécifiez le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="c597d-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="c597d-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="c597d-119">Remarks</span></span>

<span data-ttu-id="c597d-120">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c597d-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c597d-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="c597d-121">Example</span></span>

<span data-ttu-id="c597d-122">Cet exemple montre un élément `TableColumnItem` qui spécifie la propriété `Status` de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="c597d-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="c597d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c597d-123">See Also</span></span>

[<span data-ttu-id="c597d-124">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="c597d-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c597d-125">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="c597d-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="c597d-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c597d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
