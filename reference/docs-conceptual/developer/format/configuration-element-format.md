---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration, élément (Format)
description: Configuration, élément (Format)
ms.openlocfilehash: 0524736d40dd7a7acb0b6fb61d1438b75672c240
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655682"
---
# <a name="configuration-element-format"></a><span data-ttu-id="b5388-103">Configuration, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b5388-103">Configuration Element (Format)</span></span>

<span data-ttu-id="b5388-104">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b5388-104">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="b5388-105">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="b5388-105">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="b5388-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5388-106">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5388-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b5388-107">Attributes and Elements</span></span>

<span data-ttu-id="b5388-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Configuration` élément.</span><span class="sxs-lookup"><span data-stu-id="b5388-108">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="b5388-109">Cet élément doit être l’élément racine de chaque fichier de mise en forme, et cet élément doit contenir au moins un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="b5388-109">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5388-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b5388-110">Attributes</span></span>

<span data-ttu-id="b5388-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b5388-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5388-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b5388-112">Child Elements</span></span>

|<span data-ttu-id="b5388-113">Élément</span><span class="sxs-lookup"><span data-stu-id="b5388-113">Element</span></span>|<span data-ttu-id="b5388-114">Description</span><span class="sxs-lookup"><span data-stu-id="b5388-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5388-115">Controls, élément pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="b5388-115">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="b5388-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5388-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b5388-117">Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b5388-117">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="b5388-118">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b5388-118">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="b5388-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5388-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b5388-120">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b5388-120">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="b5388-121">Format de l’élément SelectionSets</span><span class="sxs-lookup"><span data-stu-id="b5388-121">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="b5388-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5388-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b5388-123">Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b5388-123">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="b5388-124">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b5388-124">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="b5388-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5388-125">Optional element.</span></span><br /><br /> <span data-ttu-id="b5388-126">Définit les vues utilisées pour afficher des objets.</span><span class="sxs-lookup"><span data-stu-id="b5388-126">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b5388-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b5388-127">Parent Elements</span></span>

<span data-ttu-id="b5388-128">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b5388-128">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5388-129">Notes</span><span class="sxs-lookup"><span data-stu-id="b5388-129">Remarks</span></span>

<span data-ttu-id="b5388-130">Les fichiers de mise en forme définissent la façon dont les objets sont affichés.</span><span class="sxs-lookup"><span data-stu-id="b5388-130">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="b5388-131">Dans la plupart des cas, cet élément racine contient un élément [ViewDefinitions](./viewdefinitions-element-format.md) qui définit la table, la liste et les vues larges du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b5388-131">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="b5388-132">Outre les définitions de vue, le fichier de mise en forme peut définir des jeux de sélection, des paramètres et des contrôles communs que ces vues peuvent utiliser.</span><span class="sxs-lookup"><span data-stu-id="b5388-132">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5388-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5388-133">See Also</span></span>

[<span data-ttu-id="b5388-134">Controls, élément pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="b5388-134">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="b5388-135">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b5388-135">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="b5388-136">SelectionSets, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b5388-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="b5388-137">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b5388-137">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="b5388-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5388-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
