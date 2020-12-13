---
ms.date: 09/13/2016
ms.topic: reference
title: DefaultSettings, élément (Format)
description: DefaultSettings, élément (Format)
ms.openlocfilehash: 1c2055b38a416fe2d75fa20c6c87e92d9eed4285
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666720"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="77edb-103">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="77edb-103">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="77edb-104">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="77edb-104">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="77edb-105">Les paramètres courants incluent l’affichage des erreurs, l’habillage du texte dans les tables, la définition du développement des collections, etc.</span><span class="sxs-lookup"><span data-stu-id="77edb-105">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="77edb-106">Élément de configuration (format) DefaultSettings, élément (format)</span><span class="sxs-lookup"><span data-stu-id="77edb-106">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77edb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77edb-107">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77edb-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="77edb-108">Attributes and Elements</span></span>

<span data-ttu-id="77edb-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `DefaultSettings` élément.</span><span class="sxs-lookup"><span data-stu-id="77edb-109">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77edb-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="77edb-110">Attributes</span></span>

<span data-ttu-id="77edb-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="77edb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77edb-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="77edb-112">Child Elements</span></span>

|<span data-ttu-id="77edb-113">Élément</span><span class="sxs-lookup"><span data-stu-id="77edb-113">Element</span></span>|<span data-ttu-id="77edb-114">Description</span><span class="sxs-lookup"><span data-stu-id="77edb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77edb-115">DisplayError, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="77edb-115">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="77edb-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="77edb-116">Optional element.</span></span><br /><br /> <span data-ttu-id="77edb-117">Spécifie que la chaîne #ERR s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.</span><span class="sxs-lookup"><span data-stu-id="77edb-117">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="77edb-118">EnumerableExpansions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="77edb-118">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="77edb-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="77edb-119">Optional element.</span></span><br /><br /> <span data-ttu-id="77edb-120">Définit les différentes façons dont les objets .NET sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="77edb-120">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="77edb-121">PropertyCountForTable (format)</span><span class="sxs-lookup"><span data-stu-id="77edb-121">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="77edb-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="77edb-122">Optional element.</span></span><br /><br /> <span data-ttu-id="77edb-123">Spécifie le nombre minimal de propriétés qu’un objet doit avoir pour afficher l’objet dans une vue table.</span><span class="sxs-lookup"><span data-stu-id="77edb-123">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="77edb-124">ShowError, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="77edb-124">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="77edb-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="77edb-125">Optional element.</span></span><br /><br /> <span data-ttu-id="77edb-126">Spécifie que l’enregistrement complet de l’erreur s’affiche lorsqu’une erreur se produit lors de l’affichage d’un élément de données.</span><span class="sxs-lookup"><span data-stu-id="77edb-126">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="77edb-127">WrapTables, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="77edb-127">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="77edb-128">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="77edb-128">Optional element.</span></span><br /><br /> <span data-ttu-id="77edb-129">Spécifie que les données d’une table sont déplacées vers la ligne suivante si elles ne correspondent pas à la largeur de la colonne.</span><span class="sxs-lookup"><span data-stu-id="77edb-129">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="77edb-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="77edb-130">Parent Elements</span></span>

|<span data-ttu-id="77edb-131">Élément</span><span class="sxs-lookup"><span data-stu-id="77edb-131">Element</span></span>|<span data-ttu-id="77edb-132">Description</span><span class="sxs-lookup"><span data-stu-id="77edb-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77edb-133">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="77edb-133">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="77edb-134">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="77edb-134">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="77edb-135">Notes</span><span class="sxs-lookup"><span data-stu-id="77edb-135">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="77edb-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77edb-136">See Also</span></span>

[<span data-ttu-id="77edb-137">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="77edb-137">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="77edb-138">DisplayError, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="77edb-138">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="77edb-139">EnumerableExpansions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="77edb-139">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="77edb-140">PropertyCountForTable (format)</span><span class="sxs-lookup"><span data-stu-id="77edb-140">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="77edb-141">ShowError, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="77edb-141">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="77edb-142">WrapTables, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="77edb-142">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="77edb-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="77edb-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
