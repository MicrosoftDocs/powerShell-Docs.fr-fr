---
title: Élément Alignment pour TableColumnHeader pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1bf395b84af90d725c14b2f0ef569f72b5fcc613
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783923"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="22684-102">Alignment, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="22684-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="22684-103">Définit le mode d’affichage des données dans un en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="22684-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="22684-104">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément table ((format) élément TableHeaders (format) TableColumnHeader élément (format) élément d’alignement pour TableColumnHeader (format)</span><span class="sxs-lookup"><span data-stu-id="22684-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22684-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22684-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22684-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="22684-106">Attributes and Elements</span></span>

<span data-ttu-id="22684-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Alignment` élément.</span><span class="sxs-lookup"><span data-stu-id="22684-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="22684-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="22684-108">Attributes</span></span>

<span data-ttu-id="22684-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="22684-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22684-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="22684-110">Child Elements</span></span>

<span data-ttu-id="22684-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="22684-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="22684-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="22684-112">Parent Elements</span></span>

|<span data-ttu-id="22684-113">Élément</span><span class="sxs-lookup"><span data-stu-id="22684-113">Element</span></span>|<span data-ttu-id="22684-114">Description</span><span class="sxs-lookup"><span data-stu-id="22684-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22684-115">TableColumnHeader, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="22684-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="22684-116">Définit une étiquette, la largeur et l’alignement des données pour une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="22684-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="22684-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="22684-117">Text Value</span></span>

<span data-ttu-id="22684-118">Spécifiez l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="22684-118">Specify one of the following values.</span></span> <span data-ttu-id="22684-119">Ces valeurs ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="22684-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="22684-120">Aligner à gauche aligne les données affichées dans la colonne de gauche. il s’agit de la valeur par défaut si cet élément n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="22684-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="22684-121">Aligne à droite les données affichées dans la colonne de droite.</span><span class="sxs-lookup"><span data-stu-id="22684-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="22684-122">Centre Centre les données affichées dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="22684-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="22684-123">Notes</span><span class="sxs-lookup"><span data-stu-id="22684-123">Remarks</span></span>

<span data-ttu-id="22684-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="22684-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="22684-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="22684-125">Example</span></span>

<span data-ttu-id="22684-126">Cet exemple montre un `TableColumnHeader` élément dont les données sont alignées à gauche.</span><span class="sxs-lookup"><span data-stu-id="22684-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="22684-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22684-127">See Also</span></span>

[<span data-ttu-id="22684-128">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="22684-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="22684-129">TableColumnHeader, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="22684-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="22684-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="22684-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
