---
title: Élément FormatString de ListItem pour un objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860335"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="a5d1d-102">FormatString, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a5d1d-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="a5d1d-103">Spécifie un modèle de format qui définit comment la valeur de propriété ou un script s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a5d1d-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="a5d1d-104">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément objet ListControl, élément (Format) situés élément d’élément de ListEntry ListControl (Format) d’élément de ListItems ListControl (Format) pour l’objet ListControl (Format) Élément ListItem pour un élément FormatString de ListControl (Format) pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a5d1d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5d1d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5d1d-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5d1d-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="a5d1d-106">Attributes and Elements</span></span>

<span data-ttu-id="a5d1d-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `FormatString` élément.</span><span class="sxs-lookup"><span data-stu-id="a5d1d-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5d1d-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="a5d1d-108">Attributes</span></span>

<span data-ttu-id="a5d1d-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="a5d1d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5d1d-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a5d1d-110">Child Elements</span></span>

<span data-ttu-id="a5d1d-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="a5d1d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a5d1d-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a5d1d-112">Parent Elements</span></span>

|<span data-ttu-id="a5d1d-113">Élément</span><span class="sxs-lookup"><span data-stu-id="a5d1d-113">Element</span></span>|<span data-ttu-id="a5d1d-114">Description</span><span class="sxs-lookup"><span data-stu-id="a5d1d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5d1d-115">Élément ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="a5d1d-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="a5d1d-116">Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="a5d1d-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a5d1d-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="a5d1d-117">Text Value</span></span>

<span data-ttu-id="a5d1d-118">Spécifiez le modèle qui est utilisé pour mettre en forme les données.</span><span class="sxs-lookup"><span data-stu-id="a5d1d-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="a5d1d-119">Par exemple, vous pouvez utiliser ce modèle pour mettre en forme la valeur de n’importe quelle propriété est de type [System.Timespan](/dotnet/api/System.TimeSpan): {0 : MMM} {0:dd} {0:HH} : {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="a5d1d-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5d1d-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="a5d1d-120">Remarks</span></span>

<span data-ttu-id="a5d1d-121">Chaînes de format peuvent être utilisés lors de la création des vues des tables, vues de liste, affichage large ou des vues personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a5d1d-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="a5d1d-122">Pour plus d’informations sur la mise en forme une valeur affichée dans une vue, consultez [mise en forme les données affichées](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="a5d1d-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="a5d1d-123">Pour plus d’informations sur l’utilisation de chaînes de format dans les affichages de liste, consultez [création d’une vue de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a5d1d-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a5d1d-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5d1d-124">Example</span></span>

<span data-ttu-id="a5d1d-125">L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="a5d1d-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="a5d1d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5d1d-126">See Also</span></span>

[<span data-ttu-id="a5d1d-127">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="a5d1d-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a5d1d-128">Élément ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="a5d1d-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="a5d1d-129">Écriture d’un mise en forme de Windows PowerShell et de Types de fichier</span><span class="sxs-lookup"><span data-stu-id="a5d1d-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
