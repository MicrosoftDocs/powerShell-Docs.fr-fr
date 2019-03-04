---
title: Élément FormatString pour TableColumnItem pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854325"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="2e27b-102">FormatString, élément pour TableColumnItem pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2e27b-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="2e27b-103">Spécifie un modèle de format qui définit comment la valeur de propriété ou un script de la table est affichée.</span><span class="sxs-lookup"><span data-stu-id="2e27b-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="2e27b-104">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément de table (Format) élément TableRowEntries (Format) TableRowEntry, élément (Format) TableColumnItems, élément (Format) TableColumnItem élément (Format) Élément FormatString pour TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2e27b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e27b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e27b-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e27b-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="2e27b-106">Attributes and Elements</span></span>

<span data-ttu-id="2e27b-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `FormatString` élément.</span><span class="sxs-lookup"><span data-stu-id="2e27b-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e27b-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="2e27b-108">Attributes</span></span>

<span data-ttu-id="2e27b-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="2e27b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e27b-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2e27b-110">Child Elements</span></span>

<span data-ttu-id="2e27b-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="2e27b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2e27b-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2e27b-112">Parent Elements</span></span>

|<span data-ttu-id="2e27b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="2e27b-113">Element</span></span>|<span data-ttu-id="2e27b-114">Description</span><span class="sxs-lookup"><span data-stu-id="2e27b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e27b-115">Élément TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2e27b-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="2e27b-116">Définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="2e27b-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2e27b-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="2e27b-117">Text Value</span></span>

<span data-ttu-id="2e27b-118">Spécifiez le modèle qui est utilisé pour mettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="2e27b-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="2e27b-119">Par exemple, ce modèle peut être utilisé pour mettre en forme la valeur de n’importe quelle propriété est de type [System.Timespan](/dotnet/api/System.TimeSpan): {0 : MMM} {0:dd} {0:HH} : {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="2e27b-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e27b-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="2e27b-120">Remarks</span></span>

<span data-ttu-id="2e27b-121">Chaînes de format peuvent être utilisés lors de la création des vues des tables, vues de liste, affichage large ou des vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="2e27b-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="2e27b-122">Pour plus d’informations sur la mise en forme une valeur affichée dans une vue, consultez [mise en forme les données affichées](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="2e27b-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="2e27b-123">Pour plus d’informations sur les composants d’une vue de table, consultez [Table vue](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="2e27b-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2e27b-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e27b-124">Example</span></span>

<span data-ttu-id="2e27b-125">L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="2e27b-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="2e27b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e27b-126">See Also</span></span>

[<span data-ttu-id="2e27b-127">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="2e27b-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2e27b-128">Mise en forme des données affichées</span><span class="sxs-lookup"><span data-stu-id="2e27b-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="2e27b-129">Élément TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="2e27b-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="2e27b-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e27b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
