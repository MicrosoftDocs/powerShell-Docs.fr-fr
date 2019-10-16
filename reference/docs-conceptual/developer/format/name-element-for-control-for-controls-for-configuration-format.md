---
title: Élément Name pour le contrôle des contrôles pour la configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362708"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="f9cc5-102">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="f9cc5-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f9cc5-103">Spécifie le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="f9cc5-103">Specifies the name of the control.</span></span> <span data-ttu-id="f9cc5-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="f9cc5-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f9cc5-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément Control pour les contrôles de configuration (format) élément Name pour le contrôle des contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f9cc5-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f9cc5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9cc5-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9cc5-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="f9cc5-107">Attributes and Elements</span></span>

<span data-ttu-id="f9cc5-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Name`.</span><span class="sxs-lookup"><span data-stu-id="f9cc5-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9cc5-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f9cc5-109">Attributes</span></span>

<span data-ttu-id="f9cc5-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f9cc5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9cc5-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f9cc5-111">Child Elements</span></span>

<span data-ttu-id="f9cc5-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f9cc5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f9cc5-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f9cc5-113">Parent Elements</span></span>

|<span data-ttu-id="f9cc5-114">Élément</span><span class="sxs-lookup"><span data-stu-id="f9cc5-114">Element</span></span>|<span data-ttu-id="f9cc5-115">Description</span><span class="sxs-lookup"><span data-stu-id="f9cc5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9cc5-116">Élément Control pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f9cc5-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="f9cc5-117">Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="f9cc5-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f9cc5-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="f9cc5-118">Text Value</span></span>

<span data-ttu-id="f9cc5-119">Spécifiez le nom utilisé pour référencer ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="f9cc5-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9cc5-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="f9cc5-120">Remarks</span></span>

<span data-ttu-id="f9cc5-121">Le nom spécifié ici peut être utilisé dans les éléments suivants pour référencer ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="f9cc5-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="f9cc5-122">Lorsque vous créez une vue de contrôle de table, de liste, étendue ou personnalisée, le contrôle peut être spécifié par l’élément suivant : [GroupBy, élément de View (format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="f9cc5-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="f9cc5-123">Lors de la création d’un autre contrôle commun, ce contrôle peut être spécifié par l’élément suivant : [ExpressionBinding pour CustomItem pour les contrôles de configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="f9cc5-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="f9cc5-124">Lorsque vous créez un contrôle qui peut être utilisé par une vue, ce contrôle peut être spécifié par l’élément suivant : [ExpressionBinding élément pour CustomItem pour les contrôles pour View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="f9cc5-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="f9cc5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9cc5-125">See Also</span></span>

[<span data-ttu-id="f9cc5-126">Élément Control pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f9cc5-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="f9cc5-127">Élément ExpressionBinding pour CustomItem pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f9cc5-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f9cc5-128">Élément ExpressionBinding pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f9cc5-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="f9cc5-129">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="f9cc5-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="f9cc5-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="f9cc5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
