---
title: Élément CustomControlName pour ExpressionBinding pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860435"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="93df3-102">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="93df3-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="93df3-103">Spécifie le nom d’un contrôle commun ou un contrôle d’affichage.</span><span class="sxs-lookup"><span data-stu-id="93df3-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="93df3-104">Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="93df3-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="93df3-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) CustomControl élément d’affichage (Format) CustomEntries élément pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour CustomItem de vue (Format) Élément pour CustomEntry pour élément de ExpressionBinding d’affichage (Format) pour l’élément de CustomControlName CustomItem (Format) pour la liaison d’Expression pour CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="93df3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="93df3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93df3-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="93df3-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="93df3-107">Attributes and Elements</span></span>

<span data-ttu-id="93df3-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="93df3-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="93df3-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="93df3-109">Attributes</span></span>

<span data-ttu-id="93df3-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="93df3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="93df3-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="93df3-111">Child Elements</span></span>

<span data-ttu-id="93df3-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="93df3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="93df3-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="93df3-113">Parent Elements</span></span>

|<span data-ttu-id="93df3-114">Élément</span><span class="sxs-lookup"><span data-stu-id="93df3-114">Element</span></span>|<span data-ttu-id="93df3-115">Description</span><span class="sxs-lookup"><span data-stu-id="93df3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93df3-116">Élément ExpressionBinding pour CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="93df3-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="93df3-117">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="93df3-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="93df3-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="93df3-118">Text Value</span></span>

<span data-ttu-id="93df3-119">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="93df3-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="93df3-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="93df3-120">Remarks</span></span>

<span data-ttu-id="93df3-121">Vous pouvez créer des contrôles communs qui peuvent être utilisées par toutes les vues d’un fichier de mise en forme et vous pouvez créer des contrôles d’affichage qui peuvent être utilisées par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="93df3-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="93df3-122">Les noms de ces contrôles sont spécifiés par les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="93df3-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="93df3-123">Name, élément pour le contrôle pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="93df3-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="93df3-124">Name, élément pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="93df3-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="93df3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93df3-125">See Also</span></span>

[<span data-ttu-id="93df3-126">Name, élément pour le contrôle pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="93df3-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="93df3-127">Name, élément pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="93df3-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="93df3-128">Élément ExpressionBinding pour CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="93df3-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="93df3-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="93df3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
