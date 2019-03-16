---
title: Élément de la largeur pour TableColumnHeader pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055187"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="bbc49-102">Width, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc49-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="bbc49-103">Définit la largeur (en caractères) d’une colonne.</span><span class="sxs-lookup"><span data-stu-id="bbc49-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="bbc49-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableHeaders élément de configuration pour TableHeaders TableColumnHeader élément de table (Format) pour l’élément de la largeur de la table (Format) pour TableColumnHeader pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc49-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bbc49-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbc49-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbc49-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="bbc49-106">Attributes and Elements</span></span>

<span data-ttu-id="bbc49-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `Width` élément utilisé lors de la définition des en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="bbc49-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbc49-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="bbc49-108">Attributes</span></span>

<span data-ttu-id="bbc49-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="bbc49-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bbc49-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bbc49-110">Child Elements</span></span>

<span data-ttu-id="bbc49-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="bbc49-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bbc49-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bbc49-112">Parent Elements</span></span>

|<span data-ttu-id="bbc49-113">Élément</span><span class="sxs-lookup"><span data-stu-id="bbc49-113">Element</span></span>|<span data-ttu-id="bbc49-114">Description</span><span class="sxs-lookup"><span data-stu-id="bbc49-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbc49-115">Élément TableColumnHeader pour TableHeaders pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc49-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="bbc49-116">Définit une étiquette, la largeur et l’alignement des données pour une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="bbc49-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bbc49-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="bbc49-117">Text Value</span></span>

<span data-ttu-id="bbc49-118">Lorsqu’à cela est possible, spécifiez une largeur (en caractères) qui est supérieure à la longueur des valeurs de propriété affiché.</span><span class="sxs-lookup"><span data-stu-id="bbc49-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbc49-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="bbc49-119">Remarks</span></span>

<span data-ttu-id="bbc49-120">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="bbc49-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bbc49-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="bbc49-121">Example</span></span>

<span data-ttu-id="bbc49-122">L’exemple suivant montre un `TableColumnHeader` élément dont la largeur est de 16 caractères.</span><span class="sxs-lookup"><span data-stu-id="bbc49-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="bbc49-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbc49-123">See Also</span></span>

[<span data-ttu-id="bbc49-124">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="bbc49-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bbc49-125">Élément TableColumnHeader pour TableHeader pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="bbc49-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="bbc49-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbc49-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
