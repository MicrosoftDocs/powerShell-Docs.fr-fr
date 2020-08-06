---
title: Élément Name pour le contrôle des contrôles pour la configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3d45ba98b909ebee18e01d2b6985a48906ce39d9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783532"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="5a933-102">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a933-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5a933-103">Spécifie le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="5a933-103">Specifies the name of the control.</span></span> <span data-ttu-id="5a933-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="5a933-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5a933-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément Control pour les contrôles de configuration (format) élément Name pour le contrôle des contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="5a933-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5a933-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a933-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a933-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5a933-107">Attributes and Elements</span></span>

<span data-ttu-id="5a933-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Name` élément.</span><span class="sxs-lookup"><span data-stu-id="5a933-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5a933-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="5a933-109">Attributes</span></span>

<span data-ttu-id="5a933-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5a933-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5a933-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5a933-111">Child Elements</span></span>

<span data-ttu-id="5a933-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5a933-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5a933-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5a933-113">Parent Elements</span></span>

|<span data-ttu-id="5a933-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5a933-114">Element</span></span>|<span data-ttu-id="5a933-115">Description</span><span class="sxs-lookup"><span data-stu-id="5a933-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a933-116">Control, élément pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a933-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="5a933-117">Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5a933-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5a933-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="5a933-118">Text Value</span></span>

<span data-ttu-id="5a933-119">Spécifiez le nom utilisé pour référencer ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="5a933-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a933-120">Notes</span><span class="sxs-lookup"><span data-stu-id="5a933-120">Remarks</span></span>

<span data-ttu-id="5a933-121">Le nom spécifié ici peut être utilisé dans les éléments suivants pour référencer ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="5a933-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="5a933-122">Lorsque vous créez une vue de contrôle de table, de liste, étendue ou personnalisée, le contrôle peut être spécifié par l’élément suivant : [GroupBy, élément de View (format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="5a933-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="5a933-123">Lors de la création d’un autre contrôle commun, ce contrôle peut être spécifié par l’élément suivant : [ExpressionBinding pour CustomItem pour les contrôles de configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="5a933-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="5a933-124">Lorsque vous créez un contrôle qui peut être utilisé par une vue, ce contrôle peut être spécifié par l’élément suivant : [ExpressionBinding élément pour CustomItem pour les contrôles pour View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="5a933-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="5a933-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a933-125">See Also</span></span>

[<span data-ttu-id="5a933-126">Control, élément pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a933-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="5a933-127">ExpressionBinding, élément pour CustomItem pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a933-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="5a933-128">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="5a933-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="5a933-129">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="5a933-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="5a933-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a933-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
