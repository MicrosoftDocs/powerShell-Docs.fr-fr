---
ms.date: 09/13/2016
ms.topic: reference
title: Control, élément pour Controls pour View (Format)
description: Control, élément pour Controls pour View (Format)
ms.openlocfilehash: c48b8b7ecaebfde5e6ed2123b837d92561551766
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668080"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="cb16b-103">Control, élément pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-103">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="cb16b-104">Définit un contrôle qui peut être utilisé par la vue et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="cb16b-104">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="cb16b-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cb16b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb16b-106">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cb16b-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cb16b-107">Attributes and Elements</span></span>

<span data-ttu-id="cb16b-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Control` élément.</span><span class="sxs-lookup"><span data-stu-id="cb16b-108">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cb16b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="cb16b-109">Attributes</span></span>

<span data-ttu-id="cb16b-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cb16b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cb16b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cb16b-111">Child Elements</span></span>

|<span data-ttu-id="cb16b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="cb16b-112">Element</span></span>|<span data-ttu-id="cb16b-113">Description</span><span class="sxs-lookup"><span data-stu-id="cb16b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb16b-114">Élément Name pour le contrôle pour View (format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-114">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="cb16b-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="cb16b-115">Required element.</span></span><br /><br /> <span data-ttu-id="cb16b-116">Spécifie le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="cb16b-116">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="cb16b-117">CustomControl, élément pour Control pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-117">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="cb16b-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="cb16b-118">Required element.</span></span><br /><br /> <span data-ttu-id="cb16b-119">Définit le contrôle utilisé par cette vue.</span><span class="sxs-lookup"><span data-stu-id="cb16b-119">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cb16b-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cb16b-120">Parent Elements</span></span>

|<span data-ttu-id="cb16b-121">Élément</span><span class="sxs-lookup"><span data-stu-id="cb16b-121">Element</span></span>|<span data-ttu-id="cb16b-122">Description</span><span class="sxs-lookup"><span data-stu-id="cb16b-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb16b-123">Élément Controls (format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-123">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="cb16b-124">Définit les contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="cb16b-124">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cb16b-125">Notes</span><span class="sxs-lookup"><span data-stu-id="cb16b-125">Remarks</span></span>

<span data-ttu-id="cb16b-126">Ce contrôle peut être spécifié par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cb16b-126">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="cb16b-127">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-127">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="cb16b-128">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-128">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="cb16b-129">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-129">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="cb16b-130">CustomControlName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-130">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="cb16b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb16b-131">See Also</span></span>

[<span data-ttu-id="cb16b-132">CustomControl, élément pour Control pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-132">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="cb16b-133">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-133">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="cb16b-134">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-134">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cb16b-135">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="cb16b-136">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-136">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="cb16b-137">Élément Controls (format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-137">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="cb16b-138">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="cb16b-138">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="cb16b-139">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb16b-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
