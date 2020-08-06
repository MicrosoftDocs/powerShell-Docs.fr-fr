---
title: Élément label pour ListItem pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ad80cc0478e7567b12d264ab661d843248ba48e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783634"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="4eeed-102">Label, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4eeed-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="4eeed-103">Spécifie l’étiquette affichée à gauche de la valeur de la propriété ou du script dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="4eeed-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="4eeed-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément pour ListControl (format) ListEntry, élément pour ListControl (format) ListItems pour l’élément ListControl pour ListControl (format) ListItem, élément de ListItems pour ListControl (format) élément label pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="4eeed-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4eeed-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4eeed-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4eeed-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4eeed-106">Attributes and Elements</span></span>

<span data-ttu-id="4eeed-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Label` élément.</span><span class="sxs-lookup"><span data-stu-id="4eeed-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4eeed-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="4eeed-108">Attributes</span></span>

<span data-ttu-id="4eeed-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4eeed-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4eeed-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4eeed-110">Child Elements</span></span>

<span data-ttu-id="4eeed-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4eeed-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4eeed-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4eeed-112">Parent Elements</span></span>

|<span data-ttu-id="4eeed-113">Élément</span><span class="sxs-lookup"><span data-stu-id="4eeed-113">Element</span></span>|<span data-ttu-id="4eeed-114">Description</span><span class="sxs-lookup"><span data-stu-id="4eeed-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4eeed-115">ListItem, élément pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4eeed-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="4eeed-116">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="4eeed-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4eeed-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="4eeed-117">Text Value</span></span>

<span data-ttu-id="4eeed-118">Spécifiez l’étiquette à afficher à gauche de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="4eeed-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="4eeed-119">Notes</span><span class="sxs-lookup"><span data-stu-id="4eeed-119">Remarks</span></span>

<span data-ttu-id="4eeed-120">Si aucune étiquette n’est spécifiée, le nom de la propriété ou du script est affiché.</span><span class="sxs-lookup"><span data-stu-id="4eeed-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="4eeed-121">Pour plus d’informations sur l’utilisation des étiquettes dans un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="4eeed-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4eeed-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="4eeed-122">Example</span></span>

<span data-ttu-id="4eeed-123">L’exemple suivant montre comment ajouter une étiquette à une ligne.</span><span class="sxs-lookup"><span data-stu-id="4eeed-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="4eeed-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4eeed-124">See Also</span></span>

[<span data-ttu-id="4eeed-125">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="4eeed-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4eeed-126">ListItem, élément (format)</span><span class="sxs-lookup"><span data-stu-id="4eeed-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="4eeed-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="4eeed-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
