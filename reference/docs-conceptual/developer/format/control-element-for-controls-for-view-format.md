---
title: Control, élément de Controls pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13ea2f09aec7fea8e5460197f133b5f5219cd369
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783804"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="a5978-102">Control, élément pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="a5978-103">Définit un contrôle qui peut être utilisé par la vue et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="a5978-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="a5978-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="a5978-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5978-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5978-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5978-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a5978-106">Attributes and Elements</span></span>

<span data-ttu-id="a5978-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Control` élément.</span><span class="sxs-lookup"><span data-stu-id="a5978-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5978-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="a5978-108">Attributes</span></span>

<span data-ttu-id="a5978-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a5978-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5978-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a5978-110">Child Elements</span></span>

|<span data-ttu-id="a5978-111">Élément</span><span class="sxs-lookup"><span data-stu-id="a5978-111">Element</span></span>|<span data-ttu-id="a5978-112">Description</span><span class="sxs-lookup"><span data-stu-id="a5978-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5978-113">Élément Name pour le contrôle pour View (format)</span><span class="sxs-lookup"><span data-stu-id="a5978-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="a5978-114">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="a5978-114">Required element.</span></span><br /><br /> <span data-ttu-id="a5978-115">Spécifie le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a5978-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="a5978-116">CustomControl, élément pour Control pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="a5978-117">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="a5978-117">Required element.</span></span><br /><br /> <span data-ttu-id="a5978-118">Définit le contrôle utilisé par cette vue.</span><span class="sxs-lookup"><span data-stu-id="a5978-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a5978-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a5978-119">Parent Elements</span></span>

|<span data-ttu-id="a5978-120">Élément</span><span class="sxs-lookup"><span data-stu-id="a5978-120">Element</span></span>|<span data-ttu-id="a5978-121">Description</span><span class="sxs-lookup"><span data-stu-id="a5978-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5978-122">Élément Controls (format)</span><span class="sxs-lookup"><span data-stu-id="a5978-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="a5978-123">Définit les contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="a5978-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a5978-124">Notes</span><span class="sxs-lookup"><span data-stu-id="a5978-124">Remarks</span></span>

<span data-ttu-id="a5978-125">Ce contrôle peut être spécifié par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a5978-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="a5978-126">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="a5978-127">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="a5978-128">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="a5978-129">CustomControlName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="a5978-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5978-130">See Also</span></span>

[<span data-ttu-id="a5978-131">CustomControl, élément pour Control pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a5978-132">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="a5978-133">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a5978-134">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="a5978-135">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="a5978-136">Élément Controls (format)</span><span class="sxs-lookup"><span data-stu-id="a5978-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="a5978-137">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a5978-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a5978-138">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5978-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
