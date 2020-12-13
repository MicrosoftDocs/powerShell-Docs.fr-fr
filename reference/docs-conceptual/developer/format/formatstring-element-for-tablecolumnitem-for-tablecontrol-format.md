---
ms.date: 09/13/2016
ms.topic: reference
title: FormatString, élément pour TableColumnItem pour TableControl (Format)
description: FormatString, élément pour TableColumnItem pour TableControl (Format)
ms.openlocfilehash: 3d386e61ac321c05e0b298019c2298f76b391b21
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667893"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="7a5f1-103">FormatString, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7a5f1-103">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="7a5f1-104">Spécifie un modèle de format qui définit le mode d’affichage de la valeur de la propriété ou du script de la table.</span><span class="sxs-lookup"><span data-stu-id="7a5f1-104">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="7a5f1-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) TableColumnItems, élément (format) TableColumnItem élément (format) FormatString élément pour TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="7a5f1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a5f1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a5f1-106">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a5f1-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7a5f1-107">Attributes and Elements</span></span>

<span data-ttu-id="7a5f1-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `FormatString` élément.</span><span class="sxs-lookup"><span data-stu-id="7a5f1-108">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a5f1-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="7a5f1-109">Attributes</span></span>

<span data-ttu-id="7a5f1-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7a5f1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a5f1-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7a5f1-111">Child Elements</span></span>

<span data-ttu-id="7a5f1-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7a5f1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7a5f1-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7a5f1-113">Parent Elements</span></span>

|<span data-ttu-id="7a5f1-114">Élément</span><span class="sxs-lookup"><span data-stu-id="7a5f1-114">Element</span></span>|<span data-ttu-id="7a5f1-115">Description</span><span class="sxs-lookup"><span data-stu-id="7a5f1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a5f1-116">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="7a5f1-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="7a5f1-117">Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="7a5f1-117">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7a5f1-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="7a5f1-118">Text Value</span></span>

<span data-ttu-id="7a5f1-119">Spécifiez le modèle qui est utilisé pour mettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="7a5f1-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="7a5f1-120">Par exemple, ce modèle peut être utilisé pour mettre en forme la valeur d’une propriété qui est de type [System. TimeSpan](/dotnet/api/System.TimeSpan): {0 : MMM} {0 : DD} {0 : HH} : {0 : mm}.</span><span class="sxs-lookup"><span data-stu-id="7a5f1-120">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a5f1-121">Notes</span><span class="sxs-lookup"><span data-stu-id="7a5f1-121">Remarks</span></span>

<span data-ttu-id="7a5f1-122">Les chaînes de format peuvent être utilisées lors de la création de vues de table, d’affichages de liste, d’affichages larges ou de vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="7a5f1-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="7a5f1-123">Pour plus d’informations sur la mise en forme d’une valeur affichée dans une vue, consultez [mise en forme des données affichées](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="7a5f1-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="7a5f1-124">Pour plus d’informations sur les composants d’une vue de table, consultez [vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="7a5f1-124">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7a5f1-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a5f1-125">Example</span></span>

<span data-ttu-id="7a5f1-126">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="7a5f1-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="7a5f1-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a5f1-127">See Also</span></span>

[<span data-ttu-id="7a5f1-128">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="7a5f1-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7a5f1-129">Mise en forme des données affichées</span><span class="sxs-lookup"><span data-stu-id="7a5f1-129">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="7a5f1-130">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="7a5f1-130">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="7a5f1-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a5f1-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
