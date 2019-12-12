---
title: Width, élément de TableColumnHeader pour table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367868"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="f4cdc-102">Width, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f4cdc-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="f4cdc-103">Définit la largeur (en caractères) d’une colonne.</span><span class="sxs-lookup"><span data-stu-id="f4cdc-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="f4cdc-104">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément table ((format) élément TableHeaders pour table ((format) TableColumnHeader élément TableHeaders pour table ((format) Width, élément de TableColumnHeader pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="f4cdc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4cdc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4cdc-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4cdc-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="f4cdc-106">Attributes and Elements</span></span>

<span data-ttu-id="f4cdc-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Width` utilisé lors de la définition des en-têtes de colonnes.</span><span class="sxs-lookup"><span data-stu-id="f4cdc-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4cdc-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="f4cdc-108">Attributes</span></span>

<span data-ttu-id="f4cdc-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f4cdc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4cdc-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f4cdc-110">Child Elements</span></span>

<span data-ttu-id="f4cdc-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f4cdc-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f4cdc-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f4cdc-112">Parent Elements</span></span>

|<span data-ttu-id="f4cdc-113">Élément</span><span class="sxs-lookup"><span data-stu-id="f4cdc-113">Element</span></span>|<span data-ttu-id="f4cdc-114">Description</span><span class="sxs-lookup"><span data-stu-id="f4cdc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4cdc-115">Élément TableColumnHeader pour TableHeaders pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="f4cdc-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="f4cdc-116">Définit une étiquette, une largeur et un alignement des données pour une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="f4cdc-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f4cdc-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="f4cdc-117">Text Value</span></span>

<span data-ttu-id="f4cdc-118">Dans la mesure du possible, spécifiez une largeur (en caractères) supérieure à la longueur des valeurs de propriété affichées.</span><span class="sxs-lookup"><span data-stu-id="f4cdc-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4cdc-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="f4cdc-119">Remarks</span></span>

<span data-ttu-id="f4cdc-120">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f4cdc-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f4cdc-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="f4cdc-121">Example</span></span>

<span data-ttu-id="f4cdc-122">L’exemple suivant montre un élément `TableColumnHeader` dont la largeur est de 16 caractères.</span><span class="sxs-lookup"><span data-stu-id="f4cdc-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="f4cdc-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4cdc-123">See Also</span></span>

[<span data-ttu-id="f4cdc-124">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="f4cdc-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f4cdc-125">Élément TableColumnHeader pour TableHeader pour table ((format)</span><span class="sxs-lookup"><span data-stu-id="f4cdc-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="f4cdc-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4cdc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
