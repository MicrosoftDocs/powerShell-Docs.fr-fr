---
title: Control, élément de contrôles pour la configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369008"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="40ed4-102">Control, élément pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="40ed4-103">Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="40ed4-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="40ed4-104">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="40ed4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40ed4-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40ed4-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="40ed4-106">Attributes and Elements</span></span>

<span data-ttu-id="40ed4-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Control`.</span><span class="sxs-lookup"><span data-stu-id="40ed4-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="40ed4-108">Vous devez spécifier un seul élément enfant.</span><span class="sxs-lookup"><span data-stu-id="40ed4-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="40ed4-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="40ed4-109">Attributes</span></span>

<span data-ttu-id="40ed4-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="40ed4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="40ed4-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="40ed4-111">Child Elements</span></span>

|<span data-ttu-id="40ed4-112">Élément</span><span class="sxs-lookup"><span data-stu-id="40ed4-112">Element</span></span>|<span data-ttu-id="40ed4-113">Description</span><span class="sxs-lookup"><span data-stu-id="40ed4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40ed4-114">CustomControl, élément de Control pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="40ed4-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="40ed4-115">Required element.</span></span><br /><br /> <span data-ttu-id="40ed4-116">Définit le contrôle.</span><span class="sxs-lookup"><span data-stu-id="40ed4-116">Defines the control.</span></span>|
|[<span data-ttu-id="40ed4-117">Élément Name pour le contrôle de la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="40ed4-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="40ed4-118">Required element.</span></span><br /><br /> <span data-ttu-id="40ed4-119">Spécifie le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="40ed4-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="40ed4-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="40ed4-120">Parent Elements</span></span>

|<span data-ttu-id="40ed4-121">Élément</span><span class="sxs-lookup"><span data-stu-id="40ed4-121">Element</span></span>|<span data-ttu-id="40ed4-122">Description</span><span class="sxs-lookup"><span data-stu-id="40ed4-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40ed4-123">Élément Controls de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="40ed4-124">Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme ou par d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="40ed4-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="40ed4-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="40ed4-125">Remarks</span></span>

<span data-ttu-id="40ed4-126">Le nom donné à ce contrôle peut être référencé dans les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="40ed4-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="40ed4-127">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="40ed4-128">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="40ed4-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40ed4-129">See Also</span></span>

[<span data-ttu-id="40ed4-130">Élément Controls de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="40ed4-131">CustomControl, élément de Control pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="40ed4-132">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="40ed4-133">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="40ed4-134">Élément Name pour le contrôle des contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="40ed4-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="40ed4-135">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="40ed4-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
