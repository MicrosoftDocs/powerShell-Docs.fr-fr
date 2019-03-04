---
title: Élément PropertyName pour ListItem pour un objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855735"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="dc9bf-102">PropertyName, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dc9bf-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="dc9bf-103">Spécifie la propriété .NET dont la valeur est affichée dans la liste.</span><span class="sxs-lookup"><span data-stu-id="dc9bf-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="dc9bf-104">Configuration élément (Format) ViewDefinitions, élément (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) ListItems, élément (Format) élément ListItem (Format) PropertyName élément pour ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="dc9bf-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc9bf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc9bf-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc9bf-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="dc9bf-106">Attributes and Elements</span></span>

<span data-ttu-id="dc9bf-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="dc9bf-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc9bf-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="dc9bf-108">Attributes</span></span>

<span data-ttu-id="dc9bf-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="dc9bf-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc9bf-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dc9bf-110">Child Elements</span></span>

<span data-ttu-id="dc9bf-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="dc9bf-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dc9bf-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dc9bf-112">Parent Elements</span></span>

|<span data-ttu-id="dc9bf-113">Élément</span><span class="sxs-lookup"><span data-stu-id="dc9bf-113">Element</span></span>|<span data-ttu-id="dc9bf-114">Description</span><span class="sxs-lookup"><span data-stu-id="dc9bf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc9bf-115">Élément ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="dc9bf-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="dc9bf-116">Définit la propriété ou un script dont la valeur est affichée dans la ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="dc9bf-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dc9bf-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="dc9bf-117">Text Value</span></span>

<span data-ttu-id="dc9bf-118">Spécifiez le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="dc9bf-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc9bf-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="dc9bf-119">Remarks</span></span>

<span data-ttu-id="dc9bf-120">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="dc9bf-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="dc9bf-121">Outre l’affichage de la valeur de propriété, vous pouvez également spécifier une étiquette pour la valeur ou une chaîne de format qui peut être utilisée pour modifier l’affichage de la valeur.</span><span class="sxs-lookup"><span data-stu-id="dc9bf-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="dc9bf-122">Pour plus d’informations sur la spécification des données dans un affichage de liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="dc9bf-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dc9bf-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc9bf-123">Example</span></span>

<span data-ttu-id="dc9bf-124">L’exemple suivant montre comment spécifier l’étiquette et la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="dc9bf-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="dc9bf-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc9bf-125">See Also</span></span>

[<span data-ttu-id="dc9bf-126">Élément ScriptBlock pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dc9bf-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="dc9bf-127">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="dc9bf-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="dc9bf-128">Élément ListItem pour ListControl(Format)</span><span class="sxs-lookup"><span data-stu-id="dc9bf-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="dc9bf-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="dc9bf-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
