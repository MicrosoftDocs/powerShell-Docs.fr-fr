---
ms.date: 09/13/2016
ms.topic: reference
title: FormatString, élément pour ListItem pour ListControl (Format)
description: FormatString, élément pour ListItem pour ListControl (Format)
ms.openlocfilehash: 1c16da92928ea632241942f4f2c63390c4fea706
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667910"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="5bfb6-103">FormatString, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5bfb6-103">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="5bfb6-104">Spécifie un modèle de format qui définit l’affichage de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="5bfb6-104">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="5bfb6-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément pour ListControl (format) élément ListEntry pour ListControl (format) élément ListItems pour ListControl (format) ListItem, élément pour ListControl (format) FormatString, élément pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="5bfb6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5bfb6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bfb6-106">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5bfb6-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5bfb6-107">Attributes and Elements</span></span>

<span data-ttu-id="5bfb6-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `FormatString` élément.</span><span class="sxs-lookup"><span data-stu-id="5bfb6-108">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5bfb6-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="5bfb6-109">Attributes</span></span>

<span data-ttu-id="5bfb6-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5bfb6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5bfb6-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5bfb6-111">Child Elements</span></span>

<span data-ttu-id="5bfb6-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5bfb6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5bfb6-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5bfb6-113">Parent Elements</span></span>

|<span data-ttu-id="5bfb6-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5bfb6-114">Element</span></span>|<span data-ttu-id="5bfb6-115">Description</span><span class="sxs-lookup"><span data-stu-id="5bfb6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5bfb6-116">ListItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="5bfb6-116">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="5bfb6-117">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="5bfb6-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5bfb6-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="5bfb6-118">Text Value</span></span>

<span data-ttu-id="5bfb6-119">Spécifiez le modèle qui est utilisé pour mettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="5bfb6-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="5bfb6-120">Par exemple, vous pouvez utiliser ce modèle pour mettre en forme la valeur d’une propriété de type [System. TimeSpan](/dotnet/api/System.TimeSpan): {0 : MMM} {0 : DD} {0 : HH} : {0 : mm}.</span><span class="sxs-lookup"><span data-stu-id="5bfb6-120">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="5bfb6-121">Notes</span><span class="sxs-lookup"><span data-stu-id="5bfb6-121">Remarks</span></span>

<span data-ttu-id="5bfb6-122">Les chaînes de format peuvent être utilisées lors de la création de vues de table, d’affichages de liste, d’affichages larges ou de vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="5bfb6-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="5bfb6-123">Pour plus d’informations sur la mise en forme d’une valeur affichée dans une vue, consultez [mise en forme des données affichées](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb6-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="5bfb6-124">Pour plus d’informations sur l’utilisation des chaînes de format dans les affichages de liste, consultez Création d’une [vue Liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb6-124">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5bfb6-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="5bfb6-125">Example</span></span>

<span data-ttu-id="5bfb6-126">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="5bfb6-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="5bfb6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bfb6-127">See Also</span></span>

[<span data-ttu-id="5bfb6-128">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="5bfb6-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5bfb6-129">ListItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="5bfb6-129">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="5bfb6-130">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5bfb6-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
