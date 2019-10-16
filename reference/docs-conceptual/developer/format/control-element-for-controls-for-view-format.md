---
title: Control, élément de Controls pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363468"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="034c5-102">Control, élément pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="034c5-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="034c5-103">Définit un contrôle qui peut être utilisé par la vue et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="034c5-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="034c5-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="034c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="034c5-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="034c5-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="034c5-106">Attributes and Elements</span></span>

<span data-ttu-id="034c5-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Control`.</span><span class="sxs-lookup"><span data-stu-id="034c5-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="034c5-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="034c5-108">Attributes</span></span>

<span data-ttu-id="034c5-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="034c5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="034c5-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="034c5-110">Child Elements</span></span>

|<span data-ttu-id="034c5-111">Élément</span><span class="sxs-lookup"><span data-stu-id="034c5-111">Element</span></span>|<span data-ttu-id="034c5-112">Description</span><span class="sxs-lookup"><span data-stu-id="034c5-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="034c5-113">Élément Name pour le contrôle pour View (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="034c5-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="034c5-114">Required element.</span></span><br /><br /> <span data-ttu-id="034c5-115">Spécifie le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="034c5-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="034c5-116">CustomControl, élément de Control pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="034c5-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="034c5-117">Required element.</span></span><br /><br /> <span data-ttu-id="034c5-118">Définit le contrôle utilisé par cette vue.</span><span class="sxs-lookup"><span data-stu-id="034c5-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="034c5-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="034c5-119">Parent Elements</span></span>

|<span data-ttu-id="034c5-120">Élément</span><span class="sxs-lookup"><span data-stu-id="034c5-120">Element</span></span>|<span data-ttu-id="034c5-121">Description</span><span class="sxs-lookup"><span data-stu-id="034c5-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="034c5-122">Élément Controls (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="034c5-123">Définit les contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="034c5-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="034c5-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="034c5-124">Remarks</span></span>

<span data-ttu-id="034c5-125">Ce contrôle peut être spécifié par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="034c5-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="034c5-126">Élément CustomControlName pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="034c5-127">Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="034c5-128">Élément CustomControlName pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="034c5-129">Élément CustomControlName pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="034c5-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="034c5-130">See Also</span></span>

[<span data-ttu-id="034c5-131">CustomControl, élément de Control pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="034c5-132">Élément CustomControlName pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="034c5-133">Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="034c5-134">Élément CustomControlName pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="034c5-135">Élément CustomControlName pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="034c5-136">Élément Controls (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="034c5-137">Élément Name pour le contrôle des contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="034c5-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="034c5-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="034c5-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
