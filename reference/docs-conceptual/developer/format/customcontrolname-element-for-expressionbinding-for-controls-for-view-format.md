---
title: Élément CustomControlName pour ExpressionBinding pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369148"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="f46e2-102">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="f46e2-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="f46e2-103">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="f46e2-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="f46e2-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="f46e2-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f46e2-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour les contrôles pour l’élément CustomItem (format) View pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour CustomItem pour les contrôles pour View (format) CustomControlName , Élément de ExpressionBindine pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f46e2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f46e2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f46e2-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f46e2-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="f46e2-107">Attributes and Elements</span></span>

<span data-ttu-id="f46e2-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="f46e2-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f46e2-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f46e2-109">Attributes</span></span>

<span data-ttu-id="f46e2-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f46e2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f46e2-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f46e2-111">Child Elements</span></span>

<span data-ttu-id="f46e2-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f46e2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f46e2-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f46e2-113">Parent Elements</span></span>

|<span data-ttu-id="f46e2-114">Élément</span><span class="sxs-lookup"><span data-stu-id="f46e2-114">Element</span></span>|<span data-ttu-id="f46e2-115">Description</span><span class="sxs-lookup"><span data-stu-id="f46e2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f46e2-116">Élément ExpressionBinding pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f46e2-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="f46e2-117">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="f46e2-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f46e2-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="f46e2-118">Text Value</span></span>

<span data-ttu-id="f46e2-119">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="f46e2-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="f46e2-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="f46e2-120">Remarks</span></span>

<span data-ttu-id="f46e2-121">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="f46e2-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="f46e2-122">Les éléments suivants spécifient les noms de ces contrôles :</span><span class="sxs-lookup"><span data-stu-id="f46e2-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="f46e2-123">Élément Name pour le contrôle des contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f46e2-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="f46e2-124">Élément Name pour le contrôle des contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f46e2-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="f46e2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f46e2-125">See Also</span></span>

[<span data-ttu-id="f46e2-126">Élément Name pour le contrôle des contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="f46e2-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="f46e2-127">Élément Name pour le contrôle des contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f46e2-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="f46e2-128">Élément ExpressionBinding pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f46e2-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="f46e2-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="f46e2-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
