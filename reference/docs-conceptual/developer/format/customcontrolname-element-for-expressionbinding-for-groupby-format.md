---
title: Élément CustomControlName pour ExpressionBinding pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368908"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="36245-102">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="36245-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="36245-103">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="36245-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="36245-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="36245-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="36245-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément CustomItem pour CustomEntry pour GroupBy (format) élément ExpressionBinding pour CustomItem pour l’élément GroupBy (format) CustomControlName pour l’élément ExpressionBinding pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="36245-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36245-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36245-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36245-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="36245-107">Attributes and Elements</span></span>

<span data-ttu-id="36245-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="36245-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="36245-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="36245-109">Attributes</span></span>

<span data-ttu-id="36245-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="36245-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36245-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="36245-111">Child Elements</span></span>

<span data-ttu-id="36245-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="36245-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="36245-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="36245-113">Parent Elements</span></span>

|<span data-ttu-id="36245-114">Élément</span><span class="sxs-lookup"><span data-stu-id="36245-114">Element</span></span>|<span data-ttu-id="36245-115">Description</span><span class="sxs-lookup"><span data-stu-id="36245-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36245-116">Élément ExpressionBinding pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="36245-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="36245-117">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="36245-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="36245-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="36245-118">Text Value</span></span>

<span data-ttu-id="36245-119">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="36245-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="36245-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="36245-120">Remarks</span></span>

<span data-ttu-id="36245-121">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="36245-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="36245-122">Les éléments suivants spécifient les noms de ces contrôles :</span><span class="sxs-lookup"><span data-stu-id="36245-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="36245-123">Élément Name pour le contrôle des contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="36245-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="36245-124">Élément Name pour le contrôle des contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="36245-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="36245-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36245-125">See Also</span></span>

[<span data-ttu-id="36245-126">Élément Name pour le contrôle des contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="36245-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="36245-127">Élément Name pour le contrôle des contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="36245-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="36245-128">Élément ExpressionBinding pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="36245-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="36245-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="36245-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
