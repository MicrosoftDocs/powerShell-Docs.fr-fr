---
title: Élément CustomControlName pour ExpressionBinding pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364108"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="e0356-102">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e0356-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="e0356-103">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="e0356-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="e0356-104">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e0356-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e0356-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl pour View (format) CustomEntries element pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour View (format) CustomItem Élément pour CustomEntry pour l’élément ExpressionBinding View (format) pour CustomItem (format) CustomControlName élément pour la liaison d’expression pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="e0356-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0356-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0356-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0356-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e0356-107">Attributes and Elements</span></span>

<span data-ttu-id="e0356-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="e0356-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0356-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="e0356-109">Attributes</span></span>

<span data-ttu-id="e0356-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e0356-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0356-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e0356-111">Child Elements</span></span>

<span data-ttu-id="e0356-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e0356-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e0356-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e0356-113">Parent Elements</span></span>

|<span data-ttu-id="e0356-114">Élément</span><span class="sxs-lookup"><span data-stu-id="e0356-114">Element</span></span>|<span data-ttu-id="e0356-115">Description</span><span class="sxs-lookup"><span data-stu-id="e0356-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0356-116">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="e0356-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="e0356-117">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e0356-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e0356-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="e0356-118">Text Value</span></span>

<span data-ttu-id="e0356-119">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e0356-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0356-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="e0356-120">Remarks</span></span>

<span data-ttu-id="e0356-121">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="e0356-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="e0356-122">Les noms de ces contrôles sont spécifiés par les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="e0356-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="e0356-123">Élément Name pour le contrôle des contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e0356-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="e0356-124">Élément Name pour le contrôle des contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e0356-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="e0356-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0356-125">See Also</span></span>

[<span data-ttu-id="e0356-126">Élément Name pour le contrôle des contrôles pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e0356-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="e0356-127">Élément Name pour le contrôle des contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="e0356-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="e0356-128">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="e0356-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e0356-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0356-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
