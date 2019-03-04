---
title: Élément CustomControlName pour ExpressionBinding pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855595"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="41c74-102">CustomControlName, élément pour ExpressionBinding pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="41c74-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="41c74-103">Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.</span><span class="sxs-lookup"><span data-stu-id="41c74-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="41c74-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="41c74-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="41c74-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles d’élément de CustomItem vue (Format) pour CustomEntry pour les contrôles d’élément de ExpressionBinding vue (Format) pour CustomItem pour les contrôles pour CustomControlName de vue (Format) Élément pour ExpressionBindine pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="41c74-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="41c74-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41c74-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41c74-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="41c74-107">Attributes and Elements</span></span>

<span data-ttu-id="41c74-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="41c74-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="41c74-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="41c74-109">Attributes</span></span>

<span data-ttu-id="41c74-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="41c74-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="41c74-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="41c74-111">Child Elements</span></span>

<span data-ttu-id="41c74-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="41c74-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="41c74-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="41c74-113">Parent Elements</span></span>

|<span data-ttu-id="41c74-114">Élément</span><span class="sxs-lookup"><span data-stu-id="41c74-114">Element</span></span>|<span data-ttu-id="41c74-115">Description</span><span class="sxs-lookup"><span data-stu-id="41c74-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41c74-116">Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="41c74-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="41c74-117">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="41c74-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="41c74-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="41c74-118">Text Value</span></span>

<span data-ttu-id="41c74-119">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="41c74-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="41c74-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="41c74-120">Remarks</span></span>

<span data-ttu-id="41c74-121">Vous pouvez créer des contrôles communs qui peuvent être utilisées par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisées par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="41c74-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="41c74-122">Les éléments suivants spécifient les noms de ces contrôles :</span><span class="sxs-lookup"><span data-stu-id="41c74-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="41c74-123">Name, élément pour le contrôle pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="41c74-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="41c74-124">Name, élément pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="41c74-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="41c74-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41c74-125">See Also</span></span>

[<span data-ttu-id="41c74-126">Name, élément pour le contrôle pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="41c74-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="41c74-127">Name, élément pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="41c74-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="41c74-128">Élément ExpressionBinding pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="41c74-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="41c74-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="41c74-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
