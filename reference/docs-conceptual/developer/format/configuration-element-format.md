---
title: Élément configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363498"
---
# <a name="configuration-element-format"></a><span data-ttu-id="9afd3-102">Configuration, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="9afd3-102">Configuration Element (Format)</span></span>

<span data-ttu-id="9afd3-103">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9afd3-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="9afd3-104">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="9afd3-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="9afd3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9afd3-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9afd3-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="9afd3-106">Attributes and Elements</span></span>

<span data-ttu-id="9afd3-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="9afd3-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="9afd3-108">Cet élément doit être l’élément racine de chaque fichier de mise en forme, et cet élément doit contenir au moins un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="9afd3-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9afd3-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="9afd3-109">Attributes</span></span>

<span data-ttu-id="9afd3-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9afd3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9afd3-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9afd3-111">Child Elements</span></span>

|<span data-ttu-id="9afd3-112">Élément</span><span class="sxs-lookup"><span data-stu-id="9afd3-112">Element</span></span>|<span data-ttu-id="9afd3-113">Description</span><span class="sxs-lookup"><span data-stu-id="9afd3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9afd3-114">Controls, élément de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="9afd3-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="9afd3-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="9afd3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9afd3-116">Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9afd3-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="9afd3-117">Élément DefaultSettings (format)</span><span class="sxs-lookup"><span data-stu-id="9afd3-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="9afd3-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="9afd3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9afd3-119">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9afd3-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="9afd3-120">Format de l’élément SelectionSets</span><span class="sxs-lookup"><span data-stu-id="9afd3-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="9afd3-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="9afd3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9afd3-122">Définit les ensembles courants d’objets .NET qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9afd3-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="9afd3-123">Élément ViewDefinitions (format)</span><span class="sxs-lookup"><span data-stu-id="9afd3-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="9afd3-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="9afd3-124">Optional element.</span></span><br /><br /> <span data-ttu-id="9afd3-125">Définit les vues utilisées pour afficher des objets.</span><span class="sxs-lookup"><span data-stu-id="9afd3-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9afd3-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9afd3-126">Parent Elements</span></span>

<span data-ttu-id="9afd3-127">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9afd3-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="9afd3-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="9afd3-128">Remarks</span></span>

<span data-ttu-id="9afd3-129">Les fichiers de mise en forme définissent la façon dont les objets sont affichés.</span><span class="sxs-lookup"><span data-stu-id="9afd3-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="9afd3-130">Dans la plupart des cas, cet élément racine contient un élément [ViewDefinitions](./viewdefinitions-element-format.md) qui définit la table, la liste et les vues larges du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9afd3-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="9afd3-131">Outre les définitions de vue, le fichier de mise en forme peut définir des jeux de sélection, des paramètres et des contrôles communs que ces vues peuvent utiliser.</span><span class="sxs-lookup"><span data-stu-id="9afd3-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="9afd3-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9afd3-132">See Also</span></span>

[<span data-ttu-id="9afd3-133">Controls, élément de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="9afd3-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="9afd3-134">Élément DefaultSettings (format)</span><span class="sxs-lookup"><span data-stu-id="9afd3-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="9afd3-135">Élément SelectionSets (format)</span><span class="sxs-lookup"><span data-stu-id="9afd3-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="9afd3-136">Élément ViewDefinitions (format)</span><span class="sxs-lookup"><span data-stu-id="9afd3-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="9afd3-137">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9afd3-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
