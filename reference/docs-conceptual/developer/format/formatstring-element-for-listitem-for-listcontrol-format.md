---
title: FormatString, élément de ListItem pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363018"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="1bd0b-102">FormatString, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1bd0b-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="1bd0b-103">Spécifie un modèle de format qui définit l’affichage de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="1bd0b-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="1bd0b-104">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément pour ListControl (format) ListEntry, élément de ListControl (format) élément ListItems pour ListControl (format) Élément ListItem pour ListControl (format) FormatString, élément pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="1bd0b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1bd0b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bd0b-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1bd0b-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="1bd0b-106">Attributes and Elements</span></span>

<span data-ttu-id="1bd0b-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `FormatString`.</span><span class="sxs-lookup"><span data-stu-id="1bd0b-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1bd0b-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="1bd0b-108">Attributes</span></span>

<span data-ttu-id="1bd0b-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1bd0b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1bd0b-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1bd0b-110">Child Elements</span></span>

<span data-ttu-id="1bd0b-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1bd0b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1bd0b-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1bd0b-112">Parent Elements</span></span>

|<span data-ttu-id="1bd0b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="1bd0b-113">Element</span></span>|<span data-ttu-id="1bd0b-114">Description</span><span class="sxs-lookup"><span data-stu-id="1bd0b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1bd0b-115">ListItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="1bd0b-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="1bd0b-116">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="1bd0b-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1bd0b-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="1bd0b-117">Text Value</span></span>

<span data-ttu-id="1bd0b-118">Spécifiez le modèle qui est utilisé pour mettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="1bd0b-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="1bd0b-119">Par exemple, vous pouvez utiliser ce modèle pour mettre en forme la valeur d’une propriété de type [System. TimeSpan](/dotnet/api/System.TimeSpan): {0 : MMM} {0 : DD} {0 : HH} : {0 : mm}.</span><span class="sxs-lookup"><span data-stu-id="1bd0b-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="1bd0b-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="1bd0b-120">Remarks</span></span>

<span data-ttu-id="1bd0b-121">Les chaînes de format peuvent être utilisées lors de la création de vues de table, d’affichages de liste, d’affichages larges ou de vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1bd0b-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="1bd0b-122">Pour plus d’informations sur la mise en forme d’une valeur affichée dans une vue, consultez [mise en forme des données affichées](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="1bd0b-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="1bd0b-123">Pour plus d’informations sur l’utilisation des chaînes de format dans les affichages de liste, consultez Création d’une [vue Liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1bd0b-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1bd0b-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="1bd0b-124">Example</span></span>

<span data-ttu-id="1bd0b-125">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la propriété `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="1bd0b-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="1bd0b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bd0b-126">See Also</span></span>

[<span data-ttu-id="1bd0b-127">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="1bd0b-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1bd0b-128">ListItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="1bd0b-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="1bd0b-129">Écriture d’un fichier de mise en forme et de types Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bd0b-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
