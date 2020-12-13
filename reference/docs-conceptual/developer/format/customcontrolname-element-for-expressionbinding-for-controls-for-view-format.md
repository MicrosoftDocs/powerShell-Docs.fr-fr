---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)
description: CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)
ms.openlocfilehash: 35e1554a9eed491f37499a7455e9c5cae3cd9e1e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655455"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="8b957-103">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="8b957-103">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="8b957-104">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="8b957-104">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="8b957-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="8b957-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8b957-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément CustomEntries View (format) pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) CustomItem pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour les contrôles de l’élément View (format) CustomItem pour CustomControlName pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8b957-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b957-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b957-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b957-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8b957-108">Attributes and Elements</span></span>

<span data-ttu-id="8b957-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="8b957-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b957-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="8b957-110">Attributes</span></span>

<span data-ttu-id="8b957-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8b957-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b957-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8b957-112">Child Elements</span></span>

<span data-ttu-id="8b957-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8b957-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8b957-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8b957-114">Parent Elements</span></span>

|<span data-ttu-id="8b957-115">Élément</span><span class="sxs-lookup"><span data-stu-id="8b957-115">Element</span></span>|<span data-ttu-id="8b957-116">Description</span><span class="sxs-lookup"><span data-stu-id="8b957-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b957-117">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="8b957-117">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="8b957-118">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="8b957-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8b957-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="8b957-119">Text Value</span></span>

<span data-ttu-id="8b957-120">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="8b957-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b957-121">Notes</span><span class="sxs-lookup"><span data-stu-id="8b957-121">Remarks</span></span>

<span data-ttu-id="8b957-122">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="8b957-122">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="8b957-123">Les éléments suivants spécifient les noms de ces contrôles :</span><span class="sxs-lookup"><span data-stu-id="8b957-123">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="8b957-124">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="8b957-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="8b957-125">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="8b957-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="8b957-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b957-126">See Also</span></span>

[<span data-ttu-id="8b957-127">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="8b957-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="8b957-128">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="8b957-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="8b957-129">ExpressionBinding, élément pour CustomItem pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="8b957-129">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="8b957-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b957-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
