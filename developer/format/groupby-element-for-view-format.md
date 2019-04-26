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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065533"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="57cdc-102">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="57cdc-103">Définit comment un nouveau groupe d’objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="57cdc-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="57cdc-104">Cet élément est utilisé lors de la définition d’une table, la liste, l’affichage de contrôle de larges ou personnalisé.</span><span class="sxs-lookup"><span data-stu-id="57cdc-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="57cdc-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour afficher (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57cdc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57cdc-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57cdc-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="57cdc-107">Attributes and Elements</span></span>

<span data-ttu-id="57cdc-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="57cdc-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="57cdc-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="57cdc-109">Attributes</span></span>

<span data-ttu-id="57cdc-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="57cdc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57cdc-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="57cdc-111">Child Elements</span></span>

|<span data-ttu-id="57cdc-112">Élément</span><span class="sxs-lookup"><span data-stu-id="57cdc-112">Element</span></span>|<span data-ttu-id="57cdc-113">Description</span><span class="sxs-lookup"><span data-stu-id="57cdc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57cdc-114">Élément CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="57cdc-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="57cdc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="57cdc-116">Définit le contrôle personnalisé qui affichent des groupes.</span><span class="sxs-lookup"><span data-stu-id="57cdc-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="57cdc-117">Élément CustomControlName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="57cdc-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="57cdc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="57cdc-119">Spécifie le nom d’un contrôle qui est utilisé pour afficher le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="57cdc-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="57cdc-120">Élément Label pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="57cdc-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="57cdc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="57cdc-122">Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.</span><span class="sxs-lookup"><span data-stu-id="57cdc-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="57cdc-123">Élément PropertyName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="57cdc-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="57cdc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="57cdc-125">Spécifie la propriété .NET le démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="57cdc-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="57cdc-126">Élément ScriptBlock pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="57cdc-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="57cdc-127">Optional element.</span></span><br /><br /> <span data-ttu-id="57cdc-128">Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="57cdc-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="57cdc-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="57cdc-129">Parent Elements</span></span>

|<span data-ttu-id="57cdc-130">Élément</span><span class="sxs-lookup"><span data-stu-id="57cdc-130">Element</span></span>|<span data-ttu-id="57cdc-131">Description</span><span class="sxs-lookup"><span data-stu-id="57cdc-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57cdc-132">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="57cdc-133">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="57cdc-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="57cdc-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="57cdc-134">Remarks</span></span>

<span data-ttu-id="57cdc-135">Lorsque vous définissez l’affichage d’un nouveau groupe d’objets, vous devez spécifier la propriété ou un script qui démarre le nouveau groupe ; Toutefois, vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="57cdc-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="57cdc-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57cdc-136">See Also</span></span>

[<span data-ttu-id="57cdc-137">Élément CustomControlName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="57cdc-138">Élément Label pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="57cdc-139">Élément PropertyName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="57cdc-140">Élément ScriptBlock pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="57cdc-141">Élément d’affichage (Format)</span><span class="sxs-lookup"><span data-stu-id="57cdc-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="57cdc-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="57cdc-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
