---
title: Élément CustomControlName pour ExpressionBinding pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854295"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="34218-102">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34218-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="34218-103">Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.</span><span class="sxs-lookup"><span data-stu-id="34218-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="34218-104">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="34218-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="34218-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de ExpressionBinding GroupBy (Format) pour CustomItem d’élément de CustomControlName GroupBy (Format) pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34218-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34218-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34218-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34218-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="34218-107">Attributes and Elements</span></span>

<span data-ttu-id="34218-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="34218-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34218-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="34218-109">Attributes</span></span>

<span data-ttu-id="34218-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="34218-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34218-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="34218-111">Child Elements</span></span>

<span data-ttu-id="34218-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="34218-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34218-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="34218-113">Parent Elements</span></span>

|<span data-ttu-id="34218-114">Élément</span><span class="sxs-lookup"><span data-stu-id="34218-114">Element</span></span>|<span data-ttu-id="34218-115">Description</span><span class="sxs-lookup"><span data-stu-id="34218-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34218-116">Élément ExpressionBinding pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34218-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="34218-117">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="34218-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="34218-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="34218-118">Text Value</span></span>

<span data-ttu-id="34218-119">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="34218-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="34218-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="34218-120">Remarks</span></span>

<span data-ttu-id="34218-121">Vous pouvez créer des contrôles communs qui peuvent être utilisées par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisées par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="34218-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="34218-122">Les éléments suivants spécifient les noms de ces contrôles :</span><span class="sxs-lookup"><span data-stu-id="34218-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="34218-123">Name, élément pour le contrôle pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="34218-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="34218-124">Name, élément pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="34218-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="34218-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34218-125">See Also</span></span>

[<span data-ttu-id="34218-126">Name, élément pour le contrôle pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="34218-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="34218-127">Name, élément pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="34218-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="34218-128">Élément ExpressionBinding pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34218-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="34218-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="34218-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
