---
title: Élément DefaultSettings (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059063"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="db395-102">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="db395-103">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="db395-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="db395-104">Paramètres courants comprennent l’affichage des erreurs, habillage du texte dans les tables, en définissant la façon dont les collections sont développées et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="db395-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="db395-105">Élément de DefaultSettings (Format) d’élément de configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db395-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db395-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db395-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="db395-107">Attributes and Elements</span></span>

<span data-ttu-id="db395-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `DefaultSettings` élément.</span><span class="sxs-lookup"><span data-stu-id="db395-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db395-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="db395-109">Attributes</span></span>

<span data-ttu-id="db395-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="db395-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db395-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db395-111">Child Elements</span></span>

|<span data-ttu-id="db395-112">Élément</span><span class="sxs-lookup"><span data-stu-id="db395-112">Element</span></span>|<span data-ttu-id="db395-113">Description</span><span class="sxs-lookup"><span data-stu-id="db395-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db395-114">Élément DisplayError (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="db395-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db395-115">Optional element.</span></span><br /><br /> <span data-ttu-id="db395-116">Spécifie que la chaîne #ERR est affichée lorsqu’une erreur se produit lors de l’affichage d’un élément de données.</span><span class="sxs-lookup"><span data-stu-id="db395-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="db395-117">Élément EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="db395-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db395-118">Optional element.</span></span><br /><br /> <span data-ttu-id="db395-119">Définit les différentes façons dont les objets .NET sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="db395-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="db395-120">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="db395-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db395-121">Optional element.</span></span><br /><br /> <span data-ttu-id="db395-122">Spécifie le nombre minimal de propriétés que doit avoir un objet pour afficher l’objet dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="db395-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="db395-123">Élément ShowError (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="db395-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db395-124">Optional element.</span></span><br /><br /> <span data-ttu-id="db395-125">Spécifie que l’enregistrement d’erreur complète est affichée lorsqu’une erreur se produit lors de l’affichage d’un élément de données.</span><span class="sxs-lookup"><span data-stu-id="db395-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="db395-126">Élément WrapTables (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="db395-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db395-127">Optional element.</span></span><br /><br /> <span data-ttu-id="db395-128">Spécifie que les données dans une table sont déplacées vers la ligne suivante si elle ne tient pas dans la largeur de la colonne.</span><span class="sxs-lookup"><span data-stu-id="db395-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="db395-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db395-129">Parent Elements</span></span>

|<span data-ttu-id="db395-130">Élément</span><span class="sxs-lookup"><span data-stu-id="db395-130">Element</span></span>|<span data-ttu-id="db395-131">Description</span><span class="sxs-lookup"><span data-stu-id="db395-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db395-132">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="db395-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="db395-133">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="db395-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="db395-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="db395-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="db395-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db395-135">See Also</span></span>

[<span data-ttu-id="db395-136">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="db395-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="db395-137">Élément DisplayError (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="db395-138">Élément EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="db395-139">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="db395-140">Élément ShowError (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="db395-141">Élément WrapTables (Format)</span><span class="sxs-lookup"><span data-stu-id="db395-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="db395-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="db395-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
