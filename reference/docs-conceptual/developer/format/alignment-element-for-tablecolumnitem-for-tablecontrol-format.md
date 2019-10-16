---
title: Élément Alignment pour TableColumnItem pour table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369078"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="214eb-102">Alignment, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="214eb-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="214eb-103">Définit le mode d’affichage des données dans une colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="214eb-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="214eb-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) TableColumnItems élément (format) TableColumnItem, élément (format) Élément Alignment pour TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="214eb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="214eb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="214eb-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="214eb-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="214eb-106">Attributes and Elements</span></span>

<span data-ttu-id="214eb-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Alignment`.</span><span class="sxs-lookup"><span data-stu-id="214eb-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="214eb-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="214eb-108">Attributes</span></span>

<span data-ttu-id="214eb-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="214eb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="214eb-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="214eb-110">Child Elements</span></span>

<span data-ttu-id="214eb-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="214eb-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="214eb-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="214eb-112">Parent Elements</span></span>

|<span data-ttu-id="214eb-113">Élément</span><span class="sxs-lookup"><span data-stu-id="214eb-113">Element</span></span>|<span data-ttu-id="214eb-114">Description</span><span class="sxs-lookup"><span data-stu-id="214eb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="214eb-115">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="214eb-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="214eb-116">Définit une étiquette, la largeur et l’alignement des données pour une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="214eb-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="214eb-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="214eb-117">Text Value</span></span>

<span data-ttu-id="214eb-118">Spécifiez l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="214eb-118">Specify one of the following values.</span></span> <span data-ttu-id="214eb-119">(Ces valeurs ne respectent pas la casse.)</span><span class="sxs-lookup"><span data-stu-id="214eb-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="214eb-120">Gauche déplace les données affichées dans la colonne vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="214eb-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="214eb-121">(Il s’agit de la valeur par défaut si cet élément n’est pas spécifié.)</span><span class="sxs-lookup"><span data-stu-id="214eb-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="214eb-122">Décale vers la droite les données affichées dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="214eb-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="214eb-123">Centre Centre les données affichées dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="214eb-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="214eb-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="214eb-124">Remarks</span></span>

<span data-ttu-id="214eb-125">Pour plus d’informations sur les composants d’une vue de table, consultez [vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="214eb-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="214eb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="214eb-126">See Also</span></span>

[<span data-ttu-id="214eb-127">Vue table</span><span class="sxs-lookup"><span data-stu-id="214eb-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="214eb-128">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="214eb-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
