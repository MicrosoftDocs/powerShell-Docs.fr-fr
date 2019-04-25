---
title: Control, élément pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066768"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="0a7b0-102">Control, élément pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="0a7b0-103">Définit un contrôle qui peut être utilisé par la vue et le nom qui est utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="0a7b0-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="0a7b0-104">Configuration élément (Format) ViewDefinitions (Format) vue élément (Format) Controls, élément de contrôle d’élément (Format) pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a7b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a7b0-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a7b0-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="0a7b0-106">Attributes and Elements</span></span>

<span data-ttu-id="0a7b0-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Control` élément.</span><span class="sxs-lookup"><span data-stu-id="0a7b0-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a7b0-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="0a7b0-108">Attributes</span></span>

<span data-ttu-id="0a7b0-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0a7b0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a7b0-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0a7b0-110">Child Elements</span></span>

|<span data-ttu-id="0a7b0-111">Élément</span><span class="sxs-lookup"><span data-stu-id="0a7b0-111">Element</span></span>|<span data-ttu-id="0a7b0-112">Description</span><span class="sxs-lookup"><span data-stu-id="0a7b0-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a7b0-113">Name, élément pour le contrôle de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="0a7b0-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="0a7b0-114">Required element.</span></span><br /><br /> <span data-ttu-id="0a7b0-115">Spécifie le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="0a7b0-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="0a7b0-116">Élément CustomControl pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="0a7b0-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="0a7b0-117">Required element.</span></span><br /><br /> <span data-ttu-id="0a7b0-118">Définit le contrôle utilisé par cette vue.</span><span class="sxs-lookup"><span data-stu-id="0a7b0-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0a7b0-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0a7b0-119">Parent Elements</span></span>

|<span data-ttu-id="0a7b0-120">Élément</span><span class="sxs-lookup"><span data-stu-id="0a7b0-120">Element</span></span>|<span data-ttu-id="0a7b0-121">Description</span><span class="sxs-lookup"><span data-stu-id="0a7b0-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a7b0-122">Élément de Controls (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="0a7b0-123">Définit les contrôles d’affichage qui peuvent être utilisées par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="0a7b0-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0a7b0-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="0a7b0-124">Remarks</span></span>

<span data-ttu-id="0a7b0-125">Ce contrôle peut être spécifié par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0a7b0-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="0a7b0-126">Élément CustomControlName pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="0a7b0-127">Élément CustomControlName pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="0a7b0-128">Élément CustomControlName pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="0a7b0-129">Élément CustomControlName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="0a7b0-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a7b0-130">See Also</span></span>

[<span data-ttu-id="0a7b0-131">Élément CustomControl pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="0a7b0-132">Élément CustomControlName pour ExpressionBinding pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="0a7b0-133">Élément CustomControlName pour ExpressionBinding pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0a7b0-134">Élément CustomControlName pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="0a7b0-135">Élément CustomControlName pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="0a7b0-136">Élément de Controls (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="0a7b0-137">Name, élément pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0a7b0-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="0a7b0-138">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a7b0-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
