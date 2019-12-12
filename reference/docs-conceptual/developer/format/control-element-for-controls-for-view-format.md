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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363468"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="1f6e7-102">Control, élément pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="1f6e7-103">Définit un contrôle qui peut être utilisé par la vue et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="1f6e7-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="1f6e7-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f6e7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f6e7-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f6e7-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="1f6e7-106">Attributes and Elements</span></span>

<span data-ttu-id="1f6e7-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Control`.</span><span class="sxs-lookup"><span data-stu-id="1f6e7-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f6e7-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="1f6e7-108">Attributes</span></span>

<span data-ttu-id="1f6e7-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1f6e7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f6e7-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1f6e7-110">Child Elements</span></span>

|<span data-ttu-id="1f6e7-111">Élément</span><span class="sxs-lookup"><span data-stu-id="1f6e7-111">Element</span></span>|<span data-ttu-id="1f6e7-112">Description</span><span class="sxs-lookup"><span data-stu-id="1f6e7-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f6e7-113">Élément Name pour le contrôle pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="1f6e7-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="1f6e7-114">Required element.</span></span><br /><br /> <span data-ttu-id="1f6e7-115">Spécifie le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="1f6e7-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="1f6e7-116">CustomControl, élément de Control pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="1f6e7-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="1f6e7-117">Required element.</span></span><br /><br /> <span data-ttu-id="1f6e7-118">Définit le contrôle utilisé par cette vue.</span><span class="sxs-lookup"><span data-stu-id="1f6e7-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1f6e7-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1f6e7-119">Parent Elements</span></span>

|<span data-ttu-id="1f6e7-120">Élément</span><span class="sxs-lookup"><span data-stu-id="1f6e7-120">Element</span></span>|<span data-ttu-id="1f6e7-121">Description</span><span class="sxs-lookup"><span data-stu-id="1f6e7-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f6e7-122">Élément Controls (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="1f6e7-123">Définit les contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="1f6e7-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f6e7-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="1f6e7-124">Remarks</span></span>

<span data-ttu-id="1f6e7-125">Ce contrôle peut être spécifié par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1f6e7-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="1f6e7-126">Élément CustomControlName pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="1f6e7-127">Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="1f6e7-128">Élément CustomControlName pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="1f6e7-129">Élément CustomControlName pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="1f6e7-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f6e7-130">See Also</span></span>

[<span data-ttu-id="1f6e7-131">CustomControl, élément de Control pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1f6e7-132">Élément CustomControlName pour ExpressionBinding pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="1f6e7-133">Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1f6e7-134">Élément CustomControlName pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="1f6e7-135">Élément CustomControlName pour ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="1f6e7-136">Élément Controls (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="1f6e7-137">Élément Name pour le contrôle des contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="1f6e7-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1f6e7-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f6e7-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
