---
ms.date: 09/13/2016
ms.topic: reference
title: Name, élément pour Control pour Controls pour Configuration (Format)
description: Name, élément pour Control pour Controls pour Configuration (Format)
ms.openlocfilehash: 0c1c83f827482886ca742f2c0174e8383f87fb52
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666499"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="d6b59-103">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d6b59-103">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d6b59-104">Spécifie le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6b59-104">Specifies the name of the control.</span></span> <span data-ttu-id="d6b59-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d6b59-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d6b59-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément Control pour les contrôles de configuration (format) élément Name pour le contrôle des contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="d6b59-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d6b59-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6b59-107">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d6b59-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d6b59-108">Attributes and Elements</span></span>

<span data-ttu-id="d6b59-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Name` élément.</span><span class="sxs-lookup"><span data-stu-id="d6b59-109">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d6b59-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d6b59-110">Attributes</span></span>

<span data-ttu-id="d6b59-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d6b59-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d6b59-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d6b59-112">Child Elements</span></span>

<span data-ttu-id="d6b59-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d6b59-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d6b59-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d6b59-114">Parent Elements</span></span>

|<span data-ttu-id="d6b59-115">Élément</span><span class="sxs-lookup"><span data-stu-id="d6b59-115">Element</span></span>|<span data-ttu-id="d6b59-116">Description</span><span class="sxs-lookup"><span data-stu-id="d6b59-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6b59-117">Control, élément pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d6b59-117">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="d6b59-118">Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6b59-118">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d6b59-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="d6b59-119">Text Value</span></span>

<span data-ttu-id="d6b59-120">Spécifiez le nom utilisé pour référencer ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6b59-120">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6b59-121">Notes</span><span class="sxs-lookup"><span data-stu-id="d6b59-121">Remarks</span></span>

<span data-ttu-id="d6b59-122">Le nom spécifié ici peut être utilisé dans les éléments suivants pour référencer ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6b59-122">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="d6b59-123">Lorsque vous créez une vue de contrôle de table, de liste, étendue ou personnalisée, le contrôle peut être spécifié par l’élément suivant : [GroupBy, élément de View (format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="d6b59-123">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="d6b59-124">Lors de la création d’un autre contrôle commun, ce contrôle peut être spécifié par l’élément suivant : [ExpressionBinding pour CustomItem pour les contrôles de configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="d6b59-124">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="d6b59-125">Lorsque vous créez un contrôle qui peut être utilisé par une vue, ce contrôle peut être spécifié par l’élément suivant : [ExpressionBinding élément pour CustomItem pour les contrôles pour View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="d6b59-125">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="d6b59-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6b59-126">See Also</span></span>

[<span data-ttu-id="d6b59-127">Control, élément pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d6b59-127">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="d6b59-128">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d6b59-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="d6b59-129">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d6b59-129">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="d6b59-130">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="d6b59-130">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="d6b59-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6b59-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
