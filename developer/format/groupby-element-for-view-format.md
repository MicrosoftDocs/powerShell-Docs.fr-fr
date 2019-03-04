---
title: Élément GroupBy de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859525"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="cdcc6-102">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="cdcc6-103">Définit comment un nouveau groupe d’objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="cdcc6-104">Cet élément est utilisé lors de la définition d’une table, la liste, l’affichage de contrôle de larges ou personnalisé.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="cdcc6-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour afficher (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cdcc6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdcc6-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cdcc6-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="cdcc6-107">Attributes and Elements</span></span>

<span data-ttu-id="cdcc6-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cdcc6-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="cdcc6-109">Attributes</span></span>

<span data-ttu-id="cdcc6-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cdcc6-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cdcc6-111">Child Elements</span></span>

|<span data-ttu-id="cdcc6-112">Élément</span><span class="sxs-lookup"><span data-stu-id="cdcc6-112">Element</span></span>|<span data-ttu-id="cdcc6-113">Description</span><span class="sxs-lookup"><span data-stu-id="cdcc6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cdcc6-114">Élément CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="cdcc6-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="cdcc6-116">Définit le contrôle personnalisé qui affichent des groupes.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="cdcc6-117">Élément CustomControlName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="cdcc6-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-118">Optional element.</span></span><br /><br /> <span data-ttu-id="cdcc6-119">Spécifie le nom d’un contrôle qui est utilisé pour afficher le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="cdcc6-120">Élément Label pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="cdcc6-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-121">Optional element.</span></span><br /><br /> <span data-ttu-id="cdcc6-122">Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="cdcc6-123">Élément PropertyName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="cdcc6-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-124">Optional element.</span></span><br /><br /> <span data-ttu-id="cdcc6-125">Spécifie la propriété .NET le démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="cdcc6-126">Élément ScriptBlock pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="cdcc6-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-127">Optional element.</span></span><br /><br /> <span data-ttu-id="cdcc6-128">Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cdcc6-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cdcc6-129">Parent Elements</span></span>

|<span data-ttu-id="cdcc6-130">Élément</span><span class="sxs-lookup"><span data-stu-id="cdcc6-130">Element</span></span>|<span data-ttu-id="cdcc6-131">Description</span><span class="sxs-lookup"><span data-stu-id="cdcc6-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cdcc6-132">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="cdcc6-133">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cdcc6-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="cdcc6-134">Remarks</span></span>

<span data-ttu-id="cdcc6-135">Lorsque vous définissez l’affichage d’un nouveau groupe d’objets, vous devez spécifier la propriété ou un script qui démarre le nouveau groupe ; Toutefois, vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="cdcc6-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdcc6-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdcc6-136">See Also</span></span>

[<span data-ttu-id="cdcc6-137">Élément CustomControlName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="cdcc6-138">Élément Label pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="cdcc6-139">Élément PropertyName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="cdcc6-140">Élément ScriptBlock pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="cdcc6-141">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="cdcc6-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="cdcc6-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cdcc6-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
