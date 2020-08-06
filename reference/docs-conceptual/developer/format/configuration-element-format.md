---
title: Élément configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 90be02f8e27c0bd391e01da1a08ecd8eeb29b84c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783838"
---
# <a name="configuration-element-format"></a><span data-ttu-id="b89d3-102">Configuration, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b89d3-102">Configuration Element (Format)</span></span>

<span data-ttu-id="b89d3-103">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b89d3-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="b89d3-104">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="b89d3-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="b89d3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b89d3-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b89d3-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b89d3-106">Attributes and Elements</span></span>

<span data-ttu-id="b89d3-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Configuration` élément.</span><span class="sxs-lookup"><span data-stu-id="b89d3-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="b89d3-108">Cet élément doit être l’élément racine de chaque fichier de mise en forme, et cet élément doit contenir au moins un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="b89d3-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b89d3-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="b89d3-109">Attributes</span></span>

<span data-ttu-id="b89d3-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b89d3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b89d3-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b89d3-111">Child Elements</span></span>

|<span data-ttu-id="b89d3-112">Élément</span><span class="sxs-lookup"><span data-stu-id="b89d3-112">Element</span></span>|<span data-ttu-id="b89d3-113">Description</span><span class="sxs-lookup"><span data-stu-id="b89d3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b89d3-114">Controls, élément pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="b89d3-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="b89d3-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b89d3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b89d3-116">Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b89d3-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="b89d3-117">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b89d3-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="b89d3-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b89d3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b89d3-119">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b89d3-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="b89d3-120">Format de l’élément SelectionSets</span><span class="sxs-lookup"><span data-stu-id="b89d3-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="b89d3-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b89d3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b89d3-122">Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b89d3-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="b89d3-123">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b89d3-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="b89d3-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="b89d3-124">Optional element.</span></span><br /><br /> <span data-ttu-id="b89d3-125">Définit les vues utilisées pour afficher des objets.</span><span class="sxs-lookup"><span data-stu-id="b89d3-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b89d3-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b89d3-126">Parent Elements</span></span>

<span data-ttu-id="b89d3-127">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b89d3-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="b89d3-128">Notes</span><span class="sxs-lookup"><span data-stu-id="b89d3-128">Remarks</span></span>

<span data-ttu-id="b89d3-129">Les fichiers de mise en forme définissent la façon dont les objets sont affichés.</span><span class="sxs-lookup"><span data-stu-id="b89d3-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="b89d3-130">Dans la plupart des cas, cet élément racine contient un élément [ViewDefinitions](./viewdefinitions-element-format.md) qui définit la table, la liste et les vues larges du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b89d3-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="b89d3-131">Outre les définitions de vue, le fichier de mise en forme peut définir des jeux de sélection, des paramètres et des contrôles communs que ces vues peuvent utiliser.</span><span class="sxs-lookup"><span data-stu-id="b89d3-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="b89d3-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b89d3-132">See Also</span></span>

[<span data-ttu-id="b89d3-133">Controls, élément pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="b89d3-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="b89d3-134">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b89d3-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="b89d3-135">SelectionSets, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b89d3-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="b89d3-136">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="b89d3-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="b89d3-137">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b89d3-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
