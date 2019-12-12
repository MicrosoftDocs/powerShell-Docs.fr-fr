---
title: FormatString, élément de WideItem pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363028"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="1c208-102">FormatString, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1c208-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="1c208-103">Spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="1c208-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="1c208-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément pour WideControl (format) élément WideItem pour WideControl (format) FormatString, élément pour WideItem pour WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="1c208-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c208-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c208-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c208-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="1c208-106">Attributes and Elements</span></span>

<span data-ttu-id="1c208-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `FormatString`.</span><span class="sxs-lookup"><span data-stu-id="1c208-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c208-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="1c208-108">Attributes</span></span>

<span data-ttu-id="1c208-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1c208-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c208-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1c208-110">Child Elements</span></span>

<span data-ttu-id="1c208-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1c208-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1c208-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1c208-112">Parent Elements</span></span>

|<span data-ttu-id="1c208-113">Élément</span><span class="sxs-lookup"><span data-stu-id="1c208-113">Element</span></span>|<span data-ttu-id="1c208-114">Description</span><span class="sxs-lookup"><span data-stu-id="1c208-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c208-115">Élément WideItem pour WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="1c208-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="1c208-116">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="1c208-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1c208-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="1c208-117">Text Value</span></span>

<span data-ttu-id="1c208-118">Spécifiez le modèle qui est utilisé pour mettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="1c208-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="1c208-119">Par exemple, vous pouvez utiliser ce modèle pour mettre en forme la valeur d’une propriété de type [System. TimeSpan](/dotnet/api/System.TimeSpan): {0 : MMM} {0 : DD} {0 : HH} : {0 : mm}.</span><span class="sxs-lookup"><span data-stu-id="1c208-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c208-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="1c208-120">Remarks</span></span>

<span data-ttu-id="1c208-121">Les chaînes de format peuvent être utilisées lors de la création de vues de table, d’affichages de liste, d’affichages larges ou de vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1c208-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="1c208-122">Pour plus d’informations sur la mise en forme d’une valeur affichée dans une vue, consultez [mise en forme des données affichées](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="1c208-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="1c208-123">Pour plus d’informations sur l’utilisation des chaînes de format dans les vues larges, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1c208-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1c208-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="1c208-124">Example</span></span>

<span data-ttu-id="1c208-125">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la propriété `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="1c208-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="1c208-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c208-126">See Also</span></span>

[<span data-ttu-id="1c208-127">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="1c208-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1c208-128">Élément WideItem pour WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="1c208-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="1c208-129">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c208-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
