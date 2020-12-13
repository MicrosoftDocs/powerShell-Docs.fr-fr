---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)
description: CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)
ms.openlocfilehash: bb7dbd449137628da1794628c5a7d7e10158dd46
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655437"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="07dec-103">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="07dec-103">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="07dec-104">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="07dec-104">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="07dec-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="07dec-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="07dec-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour la vue (format) CustomControl, élément de GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="07dec-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07dec-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07dec-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07dec-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="07dec-108">Attributes and Elements</span></span>

<span data-ttu-id="07dec-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="07dec-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="07dec-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="07dec-110">Attributes</span></span>

<span data-ttu-id="07dec-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="07dec-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07dec-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="07dec-112">Child Elements</span></span>

<span data-ttu-id="07dec-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="07dec-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="07dec-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="07dec-114">Parent Elements</span></span>

|<span data-ttu-id="07dec-115">Élément</span><span class="sxs-lookup"><span data-stu-id="07dec-115">Element</span></span>|<span data-ttu-id="07dec-116">Description</span><span class="sxs-lookup"><span data-stu-id="07dec-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07dec-117">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="07dec-117">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="07dec-118">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="07dec-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="07dec-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="07dec-119">Text Value</span></span>

<span data-ttu-id="07dec-120">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="07dec-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="07dec-121">Notes</span><span class="sxs-lookup"><span data-stu-id="07dec-121">Remarks</span></span>

<span data-ttu-id="07dec-122">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="07dec-122">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="07dec-123">Les éléments suivants spécifient les noms de ces contrôles :</span><span class="sxs-lookup"><span data-stu-id="07dec-123">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="07dec-124">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="07dec-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="07dec-125">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="07dec-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="07dec-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07dec-126">See Also</span></span>

[<span data-ttu-id="07dec-127">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="07dec-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="07dec-128">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="07dec-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="07dec-129">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="07dec-129">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="07dec-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="07dec-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
