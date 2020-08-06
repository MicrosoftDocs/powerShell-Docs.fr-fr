---
title: FormatString, élément de WideItem pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4f1f0826a1cebb1526858875df640baac9d4ce48
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781526"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="6cea8-102">FormatString, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cea8-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="6cea8-103">Spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="6cea8-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="6cea8-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément WideControl (format) élément WideEntries (format) WideEntry élément pour WideControl (format) élément WideItem pour WideControl (format) FormatString, élément pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="6cea8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6cea8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cea8-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6cea8-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6cea8-106">Attributes and Elements</span></span>

<span data-ttu-id="6cea8-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `FormatString` élément.</span><span class="sxs-lookup"><span data-stu-id="6cea8-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6cea8-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="6cea8-108">Attributes</span></span>

<span data-ttu-id="6cea8-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6cea8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6cea8-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6cea8-110">Child Elements</span></span>

<span data-ttu-id="6cea8-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6cea8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6cea8-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6cea8-112">Parent Elements</span></span>

|<span data-ttu-id="6cea8-113">Élément</span><span class="sxs-lookup"><span data-stu-id="6cea8-113">Element</span></span>|<span data-ttu-id="6cea8-114">Description</span><span class="sxs-lookup"><span data-stu-id="6cea8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6cea8-115">WideItem, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cea8-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="6cea8-116">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="6cea8-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6cea8-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="6cea8-117">Text Value</span></span>

<span data-ttu-id="6cea8-118">Spécifiez le modèle qui est utilisé pour mettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="6cea8-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="6cea8-119">Par exemple, vous pouvez utiliser ce modèle pour mettre en forme la valeur d’une propriété de type [System. TimeSpan](/dotnet/api/System.TimeSpan): {0 : MMM} {0 : DD} {0 : HH} : {0 : mm}.</span><span class="sxs-lookup"><span data-stu-id="6cea8-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="6cea8-120">Notes</span><span class="sxs-lookup"><span data-stu-id="6cea8-120">Remarks</span></span>

<span data-ttu-id="6cea8-121">Les chaînes de format peuvent être utilisées lors de la création de vues de table, d’affichages de liste, d’affichages larges ou de vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="6cea8-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="6cea8-122">Pour plus d’informations sur la mise en forme d’une valeur affichée dans une vue, consultez [mise en forme des données affichées](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="6cea8-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="6cea8-123">Pour plus d’informations sur l’utilisation des chaînes de format dans les vues larges, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="6cea8-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6cea8-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="6cea8-124">Example</span></span>

<span data-ttu-id="6cea8-125">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="6cea8-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="6cea8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cea8-126">See Also</span></span>

[<span data-ttu-id="6cea8-127">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="6cea8-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6cea8-128">WideItem, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6cea8-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="6cea8-129">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6cea8-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
