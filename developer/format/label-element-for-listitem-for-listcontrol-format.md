---
title: L’étiquette d’élément pour ListItem pour un objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065425"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="9b64c-102">Label, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9b64c-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="9b64c-103">Spécifie l’étiquette qui s’affiche à gauche de la valeur de propriété ou un script dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="9b64c-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="9b64c-104">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément d’élément de ListEntry ListControl (Format) pour ListItems ListControl (Format) pour ListEntry pour l’élément de l’objet ListControl ( Format), élément ListItem pour ListItems pour l’élément Label ListControl (Format) ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9b64c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9b64c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b64c-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b64c-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="9b64c-106">Attributes and Elements</span></span>

<span data-ttu-id="9b64c-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Label` élément.</span><span class="sxs-lookup"><span data-stu-id="9b64c-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9b64c-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="9b64c-108">Attributes</span></span>

<span data-ttu-id="9b64c-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9b64c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9b64c-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9b64c-110">Child Elements</span></span>

<span data-ttu-id="9b64c-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9b64c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9b64c-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9b64c-112">Parent Elements</span></span>

|<span data-ttu-id="9b64c-113">Élément</span><span class="sxs-lookup"><span data-stu-id="9b64c-113">Element</span></span>|<span data-ttu-id="9b64c-114">Description</span><span class="sxs-lookup"><span data-stu-id="9b64c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b64c-115">Élément ListItem pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9b64c-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="9b64c-116">Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="9b64c-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9b64c-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="9b64c-117">Text Value</span></span>

<span data-ttu-id="9b64c-118">Spécifiez l’étiquette pour être affichée à gauche de la valeur de propriété ou un script.</span><span class="sxs-lookup"><span data-stu-id="9b64c-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b64c-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="9b64c-119">Remarks</span></span>

<span data-ttu-id="9b64c-120">Si une étiquette n’est pas spécifiée, le nom de la propriété ou le script s’affiche.</span><span class="sxs-lookup"><span data-stu-id="9b64c-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="9b64c-121">Pour plus d’informations sur l’utilisation des étiquettes dans un affichage de liste, consultez [création d’une vue liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="9b64c-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9b64c-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b64c-122">Example</span></span>

<span data-ttu-id="9b64c-123">L’exemple suivant montre comment ajouter une étiquette à une ligne.</span><span class="sxs-lookup"><span data-stu-id="9b64c-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="9b64c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b64c-124">See Also</span></span>

[<span data-ttu-id="9b64c-125">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="9b64c-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9b64c-126">Élément ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="9b64c-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="9b64c-127">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b64c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
