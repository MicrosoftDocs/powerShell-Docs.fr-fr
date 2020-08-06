---
title: Élément Name pour le contrôle des contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 109f3a40606dbe82322decf0c69d2367c75175f6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781084"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="9f9ea-102">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="9f9ea-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="9f9ea-103">Spécifie le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9f9ea-103">Specifies the name of the control.</span></span>

<span data-ttu-id="9f9ea-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour l’élément View (format) Name pour le contrôle pour View (format)</span><span class="sxs-lookup"><span data-stu-id="9f9ea-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f9ea-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f9ea-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f9ea-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9f9ea-106">Attributes and Elements</span></span>

<span data-ttu-id="9f9ea-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Name` élément.</span><span class="sxs-lookup"><span data-stu-id="9f9ea-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f9ea-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="9f9ea-108">Attributes</span></span>

<span data-ttu-id="9f9ea-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9f9ea-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f9ea-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9f9ea-110">Child Elements</span></span>

<span data-ttu-id="9f9ea-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9f9ea-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9f9ea-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9f9ea-112">Parent Elements</span></span>

|<span data-ttu-id="9f9ea-113">Élément</span><span class="sxs-lookup"><span data-stu-id="9f9ea-113">Element</span></span>|<span data-ttu-id="9f9ea-114">Description</span><span class="sxs-lookup"><span data-stu-id="9f9ea-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f9ea-115">Control, élément de Controls pour View (format)</span><span class="sxs-lookup"><span data-stu-id="9f9ea-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="9f9ea-116">Définit un contrôle qui peut être utilisé par la vue et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="9f9ea-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9f9ea-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="9f9ea-117">Text Value</span></span>

<span data-ttu-id="9f9ea-118">Spécifiez le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="9f9ea-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f9ea-119">Notes</span><span class="sxs-lookup"><span data-stu-id="9f9ea-119">Remarks</span></span>

<span data-ttu-id="9f9ea-120">Le nom spécifié ici peut être utilisé dans les éléments suivants pour référencer ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="9f9ea-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="9f9ea-121">Lorsque vous créez une vue de contrôle de table, de liste, étendue ou personnalisée, le contrôle peut être spécifié par l’élément suivant : [GroupBy, élément de View (format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="9f9ea-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="9f9ea-122">Lorsque vous créez un autre contrôle qui peut être utilisé par une vue, ce contrôle peut être spécifié par l’élément suivant : [ExpressionBinding élément pour CustomItem pour les contrôles pour View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="9f9ea-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="9f9ea-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f9ea-123">See Also</span></span>

[<span data-ttu-id="9f9ea-124">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="9f9ea-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="9f9ea-125">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="9f9ea-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="9f9ea-126">Control, élément de Controls pour View (format)</span><span class="sxs-lookup"><span data-stu-id="9f9ea-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="9f9ea-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f9ea-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
