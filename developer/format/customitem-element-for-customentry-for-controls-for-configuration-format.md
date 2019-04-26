---
title: Élément CustomItem pour CustomEntry pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066428"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="205d2-102">CustomItem, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="205d2-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="205d2-103">Définit les données affichées par le contrôle et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="205d2-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="205d2-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="205d2-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="205d2-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles de Configuration</span><span class="sxs-lookup"><span data-stu-id="205d2-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="205d2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="205d2-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="205d2-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="205d2-107">Attributes and Elements</span></span>

<span data-ttu-id="205d2-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `CustomItem` élément.</span><span class="sxs-lookup"><span data-stu-id="205d2-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="205d2-109">Pour plus d’informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="205d2-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="205d2-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="205d2-110">Attributes</span></span>

<span data-ttu-id="205d2-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="205d2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="205d2-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="205d2-112">Child Elements</span></span>

|<span data-ttu-id="205d2-113">Élément</span><span class="sxs-lookup"><span data-stu-id="205d2-113">Element</span></span>|<span data-ttu-id="205d2-114">Description</span><span class="sxs-lookup"><span data-stu-id="205d2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="205d2-115">Élément ExpressionBinding pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="205d2-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="205d2-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="205d2-116">Optional element.</span></span><br /><br /> <span data-ttu-id="205d2-117">Définit les données qui sont affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="205d2-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="205d2-118">Élément de frame pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="205d2-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="205d2-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="205d2-119">Optional element.</span></span><br /><br /> <span data-ttu-id="205d2-120">Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.</span><span class="sxs-lookup"><span data-stu-id="205d2-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="205d2-121">Élément de saut de ligne pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="205d2-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="205d2-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="205d2-122">Optional element.</span></span><br /><br /> <span data-ttu-id="205d2-123">Ajoute une ligne vide à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="205d2-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="205d2-124">Élément de texte pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="205d2-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="205d2-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="205d2-125">Optional element.</span></span><br /><br /> <span data-ttu-id="205d2-126">Ajoute du texte, tels que des parenthèses ou des crochets, à l’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="205d2-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="205d2-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="205d2-127">Parent Elements</span></span>

|<span data-ttu-id="205d2-128">Élément</span><span class="sxs-lookup"><span data-stu-id="205d2-128">Element</span></span>|<span data-ttu-id="205d2-129">Description</span><span class="sxs-lookup"><span data-stu-id="205d2-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="205d2-130">Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="205d2-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="205d2-131">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="205d2-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="205d2-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="205d2-132">Remarks</span></span>

<span data-ttu-id="205d2-133">Lorsque vous spécifiez les éléments enfants de le `CustomItem` élément, gardez les points suivants à l’esprit :</span><span class="sxs-lookup"><span data-stu-id="205d2-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="205d2-134">Les éléments enfants doivent être ajoutés dans l’ordre suivant : `ExpressionBinding`, `NewLine`, `Text`, et `Frame`.</span><span class="sxs-lookup"><span data-stu-id="205d2-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="205d2-135">Il n’existe aucune limite maximale pour le nombre de séquences que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="205d2-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="205d2-136">Dans chaque séquence, il n’existe aucune limite maximale pour le nombre de `ExpressionBinding` éléments que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="205d2-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="205d2-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="205d2-137">See Also</span></span>

[<span data-ttu-id="205d2-138">Élément ExpressionBinding pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="205d2-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="205d2-139">Élément de frame pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="205d2-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="205d2-140">Élément de saut de ligne pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="205d2-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="205d2-141">Élément de texte pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="205d2-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="205d2-142">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="205d2-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
