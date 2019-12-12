---
title: FormatString, élément de TableColumnItem pour table ((format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363708"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="f48be-102">FormatString, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f48be-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="f48be-103">Spécifie un modèle de format qui définit le mode d’affichage de la valeur de la propriété ou du script de la table.</span><span class="sxs-lookup"><span data-stu-id="f48be-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="f48be-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry, élément (format) TableColumnItems élément (format) TableColumnItem, élément (format) FormatString, élément de TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="f48be-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f48be-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f48be-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f48be-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="f48be-106">Attributes and Elements</span></span>

<span data-ttu-id="f48be-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `FormatString`.</span><span class="sxs-lookup"><span data-stu-id="f48be-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f48be-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="f48be-108">Attributes</span></span>

<span data-ttu-id="f48be-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f48be-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f48be-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f48be-110">Child Elements</span></span>

<span data-ttu-id="f48be-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f48be-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f48be-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f48be-112">Parent Elements</span></span>

|<span data-ttu-id="f48be-113">Élément</span><span class="sxs-lookup"><span data-stu-id="f48be-113">Element</span></span>|<span data-ttu-id="f48be-114">Description</span><span class="sxs-lookup"><span data-stu-id="f48be-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f48be-115">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="f48be-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="f48be-116">Définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="f48be-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f48be-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="f48be-117">Text Value</span></span>

<span data-ttu-id="f48be-118">Spécifiez le modèle qui est utilisé pour mettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="f48be-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="f48be-119">Par exemple, ce modèle peut être utilisé pour mettre en forme la valeur d’une propriété qui est de type [System. TimeSpan](/dotnet/api/System.TimeSpan): {0 : MMM} {0 : DD} {0 : HH} : {0 : mm}.</span><span class="sxs-lookup"><span data-stu-id="f48be-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="f48be-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="f48be-120">Remarks</span></span>

<span data-ttu-id="f48be-121">Les chaînes de format peuvent être utilisées lors de la création de vues de table, d’affichages de liste, d’affichages larges ou de vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f48be-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="f48be-122">Pour plus d’informations sur la mise en forme d’une valeur affichée dans une vue, consultez [mise en forme des données affichées](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="f48be-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="f48be-123">Pour plus d’informations sur les composants d’une vue de table, consultez [vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f48be-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f48be-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="f48be-124">Example</span></span>

<span data-ttu-id="f48be-125">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la propriété `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="f48be-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="f48be-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f48be-126">See Also</span></span>

[<span data-ttu-id="f48be-127">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="f48be-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f48be-128">Mise en forme des données affichées</span><span class="sxs-lookup"><span data-stu-id="f48be-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="f48be-129">Élément TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="f48be-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="f48be-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="f48be-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
