---
title: GroupBy, élément de View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2f9071a3ebbc7cc2ccb7721dd518e82723e9cc4e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781424"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="4cf47-102">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="4cf47-103">Définit le mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="4cf47-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="4cf47-104">Cet élément est utilisé lors de la définition d’une vue de contrôle de table, de liste, étendue ou personnalisée.</span><span class="sxs-lookup"><span data-stu-id="4cf47-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="4cf47-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour View (format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4cf47-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cf47-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4cf47-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4cf47-107">Attributes and Elements</span></span>

<span data-ttu-id="4cf47-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4cf47-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4cf47-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="4cf47-109">Attributes</span></span>

<span data-ttu-id="4cf47-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4cf47-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4cf47-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4cf47-111">Child Elements</span></span>

|<span data-ttu-id="4cf47-112">Élément</span><span class="sxs-lookup"><span data-stu-id="4cf47-112">Element</span></span>|<span data-ttu-id="4cf47-113">Description</span><span class="sxs-lookup"><span data-stu-id="4cf47-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4cf47-114">CustomControl, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="4cf47-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4cf47-115">Optional element.</span></span><br /><br /> <span data-ttu-id="4cf47-116">Définit le contrôle personnalisé qui affiche les nouveaux groupes.</span><span class="sxs-lookup"><span data-stu-id="4cf47-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="4cf47-117">CustomControlName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="4cf47-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4cf47-118">Optional element.</span></span><br /><br /> <span data-ttu-id="4cf47-119">Spécifie le nom d’un contrôle qui est utilisé pour afficher le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="4cf47-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="4cf47-120">Label, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="4cf47-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4cf47-121">Optional element.</span></span><br /><br /> <span data-ttu-id="4cf47-122">Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.</span><span class="sxs-lookup"><span data-stu-id="4cf47-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="4cf47-123">PropertyName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="4cf47-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4cf47-124">Optional element.</span></span><br /><br /> <span data-ttu-id="4cf47-125">Spécifie la propriété .NET qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="4cf47-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="4cf47-126">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="4cf47-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4cf47-127">Optional element.</span></span><br /><br /> <span data-ttu-id="4cf47-128">Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="4cf47-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4cf47-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4cf47-129">Parent Elements</span></span>

|<span data-ttu-id="4cf47-130">Élément</span><span class="sxs-lookup"><span data-stu-id="4cf47-130">Element</span></span>|<span data-ttu-id="4cf47-131">Description</span><span class="sxs-lookup"><span data-stu-id="4cf47-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4cf47-132">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="4cf47-133">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="4cf47-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4cf47-134">Notes</span><span class="sxs-lookup"><span data-stu-id="4cf47-134">Remarks</span></span>

<span data-ttu-id="4cf47-135">Lorsque vous définissez le mode d’affichage d’un nouveau groupe d’objets, vous devez spécifier la propriété ou le script qui va démarrer le nouveau groupe. Toutefois, vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="4cf47-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="4cf47-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cf47-136">See Also</span></span>

[<span data-ttu-id="4cf47-137">CustomControlName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="4cf47-138">Label, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="4cf47-139">PropertyName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="4cf47-140">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="4cf47-141">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="4cf47-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="4cf47-142">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="4cf47-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
