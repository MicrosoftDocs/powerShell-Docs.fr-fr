---
title: Élément FirstLineHanging pour Frame pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861335"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="8e0e9-102">FirstLineHanging, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="8e0e9-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8e0e9-103">Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="8e0e9-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="8e0e9-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="8e0e9-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8e0e9-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de CustomItem Configuration (Format) pour CustomEntry pour les contrôles d’élément de Frame de Configuration pour CustomItem pour les contrôles d’élément de FirstLineHanging Configuration (Format) pour le Frame pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="8e0e9-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e0e9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e0e9-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e0e9-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="8e0e9-107">Attributes and Elements</span></span>

<span data-ttu-id="8e0e9-108">Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `FirstLineHanging` élément.</span><span class="sxs-lookup"><span data-stu-id="8e0e9-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e0e9-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="8e0e9-109">Attributes</span></span>

<span data-ttu-id="8e0e9-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="8e0e9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e0e9-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8e0e9-111">Child Elements</span></span>

<span data-ttu-id="8e0e9-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="8e0e9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8e0e9-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8e0e9-113">Parent Elements</span></span>

|<span data-ttu-id="8e0e9-114">Élément</span><span class="sxs-lookup"><span data-stu-id="8e0e9-114">Element</span></span>|<span data-ttu-id="8e0e9-115">Description</span><span class="sxs-lookup"><span data-stu-id="8e0e9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e0e9-116">Élément de frame pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="8e0e9-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="8e0e9-117">Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.</span><span class="sxs-lookup"><span data-stu-id="8e0e9-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8e0e9-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="8e0e9-118">Text Value</span></span>

<span data-ttu-id="8e0e9-119">Spécifiez le nombre de caractères que vous souhaitez déplacer la première ligne des données.</span><span class="sxs-lookup"><span data-stu-id="8e0e9-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e0e9-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="8e0e9-120">Remarks</span></span>

<span data-ttu-id="8e0e9-121">Si cet élément est spécifié, vous ne pouvez pas spécifier le `FirstLineIndent` élément.</span><span class="sxs-lookup"><span data-stu-id="8e0e9-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e0e9-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e0e9-122">See Also</span></span>

[<span data-ttu-id="8e0e9-123">Élément de frame pour CustomItem pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="8e0e9-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="8e0e9-124">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e0e9-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
