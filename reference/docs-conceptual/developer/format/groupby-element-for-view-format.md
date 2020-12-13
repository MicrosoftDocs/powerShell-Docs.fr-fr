---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy, élément pour View (Format)
description: GroupBy, élément pour View (Format)
ms.openlocfilehash: d8ca93a3b2c1490928885579919c07f5eb274cd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652096"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="db0c5-103">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-103">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="db0c5-104">Définit le mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="db0c5-104">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="db0c5-105">Cet élément est utilisé lors de la définition d’une vue de contrôle de table, de liste, étendue ou personnalisée.</span><span class="sxs-lookup"><span data-stu-id="db0c5-105">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="db0c5-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour View (format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db0c5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db0c5-107">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db0c5-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="db0c5-108">Attributes and Elements</span></span>

<span data-ttu-id="db0c5-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="db0c5-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="db0c5-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="db0c5-110">Attributes</span></span>

<span data-ttu-id="db0c5-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="db0c5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db0c5-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db0c5-112">Child Elements</span></span>

|<span data-ttu-id="db0c5-113">Élément</span><span class="sxs-lookup"><span data-stu-id="db0c5-113">Element</span></span>|<span data-ttu-id="db0c5-114">Description</span><span class="sxs-lookup"><span data-stu-id="db0c5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db0c5-115">CustomControl, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-115">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="db0c5-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db0c5-116">Optional element.</span></span><br /><br /> <span data-ttu-id="db0c5-117">Définit le contrôle personnalisé qui affiche les nouveaux groupes.</span><span class="sxs-lookup"><span data-stu-id="db0c5-117">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="db0c5-118">CustomControlName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-118">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="db0c5-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db0c5-119">Optional element.</span></span><br /><br /> <span data-ttu-id="db0c5-120">Spécifie le nom d’un contrôle qui est utilisé pour afficher le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="db0c5-120">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="db0c5-121">Label, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-121">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="db0c5-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db0c5-122">Optional element.</span></span><br /><br /> <span data-ttu-id="db0c5-123">Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.</span><span class="sxs-lookup"><span data-stu-id="db0c5-123">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="db0c5-124">PropertyName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-124">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="db0c5-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db0c5-125">Optional element.</span></span><br /><br /> <span data-ttu-id="db0c5-126">Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="db0c5-126">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="db0c5-127">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="db0c5-128">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="db0c5-128">Optional element.</span></span><br /><br /> <span data-ttu-id="db0c5-129">Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="db0c5-129">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="db0c5-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db0c5-130">Parent Elements</span></span>

|<span data-ttu-id="db0c5-131">Élément</span><span class="sxs-lookup"><span data-stu-id="db0c5-131">Element</span></span>|<span data-ttu-id="db0c5-132">Description</span><span class="sxs-lookup"><span data-stu-id="db0c5-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db0c5-133">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-133">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="db0c5-134">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="db0c5-134">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="db0c5-135">Notes</span><span class="sxs-lookup"><span data-stu-id="db0c5-135">Remarks</span></span>

<span data-ttu-id="db0c5-136">Lorsque vous définissez le mode d’affichage d’un nouveau groupe d’objets, vous devez spécifier la propriété ou le script qui va démarrer le nouveau groupe. Toutefois, vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="db0c5-136">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="db0c5-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db0c5-137">See Also</span></span>

[<span data-ttu-id="db0c5-138">CustomControlName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-138">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="db0c5-139">Label, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-139">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="db0c5-140">PropertyName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-140">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="db0c5-141">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-141">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="db0c5-142">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="db0c5-142">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="db0c5-143">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="db0c5-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
