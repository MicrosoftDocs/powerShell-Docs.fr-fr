---
title: Control, élément de contrôles pour la configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9447efac84cff3cc33468aeebc97a8bdd6137518
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783821"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="b3fad-102">Control, élément pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b3fad-103">Définit un contrôle commun qui peut être utilisé par toutes les vues du fichier de mise en forme et le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b3fad-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="b3fad-104">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b3fad-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3fad-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b3fad-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b3fad-106">Attributes and Elements</span></span>

<span data-ttu-id="b3fad-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Control` élément.</span><span class="sxs-lookup"><span data-stu-id="b3fad-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="b3fad-108">Vous devez spécifier un seul élément enfant.</span><span class="sxs-lookup"><span data-stu-id="b3fad-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b3fad-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="b3fad-109">Attributes</span></span>

<span data-ttu-id="b3fad-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b3fad-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b3fad-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b3fad-111">Child Elements</span></span>

|<span data-ttu-id="b3fad-112">Élément</span><span class="sxs-lookup"><span data-stu-id="b3fad-112">Element</span></span>|<span data-ttu-id="b3fad-113">Description</span><span class="sxs-lookup"><span data-stu-id="b3fad-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3fad-114">CustomControl, élément pour Control pour Controls (Format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="b3fad-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="b3fad-115">Required element.</span></span><br /><br /> <span data-ttu-id="b3fad-116">Définit le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b3fad-116">Defines the control.</span></span>|
|[<span data-ttu-id="b3fad-117">Élément Name pour le contrôle de la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="b3fad-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="b3fad-118">Required element.</span></span><br /><br /> <span data-ttu-id="b3fad-119">Spécifie le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b3fad-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b3fad-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b3fad-120">Parent Elements</span></span>

|<span data-ttu-id="b3fad-121">Élément</span><span class="sxs-lookup"><span data-stu-id="b3fad-121">Element</span></span>|<span data-ttu-id="b3fad-122">Description</span><span class="sxs-lookup"><span data-stu-id="b3fad-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3fad-123">Élément Controls de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="b3fad-124">Définit les contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme ou par d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="b3fad-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b3fad-125">Notes</span><span class="sxs-lookup"><span data-stu-id="b3fad-125">Remarks</span></span>

<span data-ttu-id="b3fad-126">Le nom donné à ce contrôle peut être référencé dans les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b3fad-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="b3fad-127">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="b3fad-128">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="b3fad-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3fad-129">See Also</span></span>

[<span data-ttu-id="b3fad-130">Élément Controls de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="b3fad-131">CustomControl, élément de Control pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="b3fad-132">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b3fad-133">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="b3fad-134">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="b3fad-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="b3fad-135">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3fad-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
