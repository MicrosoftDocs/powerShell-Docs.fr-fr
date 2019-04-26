---
title: Élément d’alignement pour TableColumnHeader pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067006"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="72200-102">Alignment, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="72200-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="72200-103">Définit comment les données dans un en-tête de colonne s’affiche.</span><span class="sxs-lookup"><span data-stu-id="72200-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="72200-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) élément TableHeaders (Format) TableColumnHeader, élément (Format) alignement élément de configuration pour TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="72200-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="72200-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72200-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="72200-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="72200-106">Attributes and Elements</span></span>

<span data-ttu-id="72200-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `Alignment` élément.</span><span class="sxs-lookup"><span data-stu-id="72200-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="72200-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="72200-108">Attributes</span></span>

<span data-ttu-id="72200-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="72200-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="72200-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="72200-110">Child Elements</span></span>

<span data-ttu-id="72200-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="72200-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="72200-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="72200-112">Parent Elements</span></span>

|<span data-ttu-id="72200-113">Élément</span><span class="sxs-lookup"><span data-stu-id="72200-113">Element</span></span>|<span data-ttu-id="72200-114">Description</span><span class="sxs-lookup"><span data-stu-id="72200-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72200-115">Élément TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="72200-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="72200-116">Définit une étiquette, la largeur et l’alignement des données pour une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="72200-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="72200-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="72200-117">Text Value</span></span>

<span data-ttu-id="72200-118">Spécifiez l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="72200-118">Specify one of the following values.</span></span> <span data-ttu-id="72200-119">Ces valeurs ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="72200-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="72200-120">Aligne à gauche les données affichées dans la colonne gauche Ceci est la valeur par défaut si cet élément n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="72200-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="72200-121">Aligne à droite les données affichées dans la colonne de droite.</span><span class="sxs-lookup"><span data-stu-id="72200-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="72200-122">Centres de centre de données affichées dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="72200-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="72200-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="72200-123">Remarks</span></span>

<span data-ttu-id="72200-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="72200-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="72200-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="72200-125">Example</span></span>

<span data-ttu-id="72200-126">Cet exemple montre un `TableColumnHeader` élément dont les données sont alignées à gauche.</span><span class="sxs-lookup"><span data-stu-id="72200-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="72200-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72200-127">See Also</span></span>

[<span data-ttu-id="72200-128">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="72200-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="72200-129">Élément TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="72200-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="72200-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="72200-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
