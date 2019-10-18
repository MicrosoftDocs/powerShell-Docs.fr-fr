---
title: Élément DefaultSettings (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363868"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="1f8a8-102">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="1f8a8-103">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="1f8a8-104">Les paramètres courants incluent l’affichage des erreurs, l’habillage du texte dans les tables, la définition du développement des collections, etc.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="1f8a8-105">Élément de configuration (format) DefaultSettings, élément (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f8a8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f8a8-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f8a8-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="1f8a8-107">Attributes and Elements</span></span>

<span data-ttu-id="1f8a8-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `DefaultSettings`.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f8a8-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="1f8a8-109">Attributes</span></span>

<span data-ttu-id="1f8a8-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f8a8-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1f8a8-111">Child Elements</span></span>

|<span data-ttu-id="1f8a8-112">Élément</span><span class="sxs-lookup"><span data-stu-id="1f8a8-112">Element</span></span>|<span data-ttu-id="1f8a8-113">Description</span><span class="sxs-lookup"><span data-stu-id="1f8a8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f8a8-114">Élément DisplayError (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="1f8a8-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1f8a8-116">Spécifie que la chaîne #ERR s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="1f8a8-117">Élément EnumerableExpansions (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="1f8a8-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="1f8a8-119">Définit les différentes façons dont les objets .NET sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="1f8a8-120">PropertyCountForTable (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="1f8a8-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="1f8a8-122">Spécifie le nombre minimal de propriétés qu’un objet doit avoir pour afficher l’objet dans une vue table.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="1f8a8-123">Élément ShowError (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="1f8a8-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="1f8a8-125">Spécifie que l’enregistrement complet de l’erreur s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="1f8a8-126">Élément WrapTables (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="1f8a8-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-127">Optional element.</span></span><br /><br /> <span data-ttu-id="1f8a8-128">Spécifie que les données d’une table sont déplacées vers la ligne suivante si elles ne correspondent pas à la largeur de la colonne.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1f8a8-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1f8a8-129">Parent Elements</span></span>

|<span data-ttu-id="1f8a8-130">Élément</span><span class="sxs-lookup"><span data-stu-id="1f8a8-130">Element</span></span>|<span data-ttu-id="1f8a8-131">Description</span><span class="sxs-lookup"><span data-stu-id="1f8a8-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f8a8-132">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="1f8a8-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="1f8a8-133">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="1f8a8-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f8a8-134">Remarks</span><span class="sxs-lookup"><span data-stu-id="1f8a8-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="1f8a8-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f8a8-135">See Also</span></span>

[<span data-ttu-id="1f8a8-136">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="1f8a8-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="1f8a8-137">Élément DisplayError (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="1f8a8-138">Élément EnumerableExpansions (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="1f8a8-139">PropertyCountForTable (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="1f8a8-140">Élément ShowError (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="1f8a8-141">Élément WrapTables (format)</span><span class="sxs-lookup"><span data-stu-id="1f8a8-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="1f8a8-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f8a8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)