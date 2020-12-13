---
ms.date: 09/13/2016
ms.topic: reference
title: Width, élément pour TableColumnHeader pour TableControl (Format)
description: Width, élément pour TableColumnHeader pour TableControl (Format)
ms.openlocfilehash: bde84f1d33b3d6b3b8c4462f870f978611cb434b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658255"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="27d25-103">Width, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="27d25-103">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="27d25-104">Définit la largeur (en caractères) d’une colonne.</span><span class="sxs-lookup"><span data-stu-id="27d25-104">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="27d25-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément table ((format) élément TableHeaders pour table ((format) TableColumnHeader élément TableHeaders pour table ((format) élément Width pour TableColumnHeader (format)</span><span class="sxs-lookup"><span data-stu-id="27d25-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="27d25-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27d25-106">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27d25-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="27d25-107">Attributes and Elements</span></span>

<span data-ttu-id="27d25-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Width` élément utilisé lors de la définition des en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="27d25-108">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="27d25-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="27d25-109">Attributes</span></span>

<span data-ttu-id="27d25-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="27d25-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27d25-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="27d25-111">Child Elements</span></span>

<span data-ttu-id="27d25-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="27d25-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="27d25-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="27d25-113">Parent Elements</span></span>

|<span data-ttu-id="27d25-114">Élément</span><span class="sxs-lookup"><span data-stu-id="27d25-114">Element</span></span>|<span data-ttu-id="27d25-115">Description</span><span class="sxs-lookup"><span data-stu-id="27d25-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27d25-116">Élément TableColumnHeader pour TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="27d25-116">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="27d25-117">Définit une étiquette, une largeur et un alignement des données pour une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="27d25-117">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="27d25-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="27d25-118">Text Value</span></span>

<span data-ttu-id="27d25-119">Dans la mesure du possible, spécifiez une largeur (en caractères) supérieure à la longueur des valeurs de propriété affichées.</span><span class="sxs-lookup"><span data-stu-id="27d25-119">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="27d25-120">Notes</span><span class="sxs-lookup"><span data-stu-id="27d25-120">Remarks</span></span>

<span data-ttu-id="27d25-121">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="27d25-121">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="27d25-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="27d25-122">Example</span></span>

<span data-ttu-id="27d25-123">L’exemple suivant montre un `TableColumnHeader` élément dont la largeur est de 16 caractères.</span><span class="sxs-lookup"><span data-stu-id="27d25-123">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="27d25-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27d25-124">See Also</span></span>

[<span data-ttu-id="27d25-125">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="27d25-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="27d25-126">Élément TableColumnHeader pour TableHeader pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="27d25-126">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="27d25-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="27d25-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
