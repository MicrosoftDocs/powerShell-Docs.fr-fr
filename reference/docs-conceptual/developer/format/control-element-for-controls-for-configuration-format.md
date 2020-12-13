---
ms.date: 09/13/2016
ms.topic: reference
title: Control, élément pour Controls pour Configuration (Format)
description: Control, élément pour Controls pour Configuration (Format)
ms.openlocfilehash: 43424de025cb89d81533e973abd7c39c09533747
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655656"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="7c5b4-103">Control, élément pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-103">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7c5b4-104">Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-104">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="7c5b4-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c5b4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c5b4-106">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c5b4-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7c5b4-107">Attributes and Elements</span></span>

<span data-ttu-id="7c5b4-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Control` élément.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-108">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="7c5b4-109">Vous devez spécifier un seul élément enfant.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-109">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c5b4-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="7c5b4-110">Attributes</span></span>

<span data-ttu-id="7c5b4-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c5b4-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7c5b4-112">Child Elements</span></span>

|<span data-ttu-id="7c5b4-113">Élément</span><span class="sxs-lookup"><span data-stu-id="7c5b4-113">Element</span></span>|<span data-ttu-id="7c5b4-114">Description</span><span class="sxs-lookup"><span data-stu-id="7c5b4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c5b4-115">CustomControl, élément pour Control pour Controls (Format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-115">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="7c5b4-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-116">Required element.</span></span><br /><br /> <span data-ttu-id="7c5b4-117">Définit le contrôle.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-117">Defines the control.</span></span>|
|[<span data-ttu-id="7c5b4-118">Élément Name pour le contrôle de la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-118">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="7c5b4-119">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-119">Required element.</span></span><br /><br /> <span data-ttu-id="7c5b4-120">Spécifie le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-120">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7c5b4-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7c5b4-121">Parent Elements</span></span>

|<span data-ttu-id="7c5b4-122">Élément</span><span class="sxs-lookup"><span data-stu-id="7c5b4-122">Element</span></span>|<span data-ttu-id="7c5b4-123">Description</span><span class="sxs-lookup"><span data-stu-id="7c5b4-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c5b4-124">Élément Controls de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-124">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="7c5b4-125">Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme ou par d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="7c5b4-125">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7c5b4-126">Notes</span><span class="sxs-lookup"><span data-stu-id="7c5b4-126">Remarks</span></span>

<span data-ttu-id="7c5b4-127">Le nom donné à ce contrôle peut être référencé dans les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="7c5b4-127">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="7c5b4-128">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="7c5b4-129">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-129">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="7c5b4-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c5b4-130">See Also</span></span>

[<span data-ttu-id="7c5b4-131">Élément Controls de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-131">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="7c5b4-132">CustomControl, élément de Control pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-132">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="7c5b4-133">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-133">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="7c5b4-134">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-134">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="7c5b4-135">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="7c5b4-135">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="7c5b4-136">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c5b4-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
