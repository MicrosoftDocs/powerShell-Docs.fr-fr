---
title: Élément FirstLineIndent pour Frame pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854315"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="b7fb1-102">FirstLineIndent, élément pour Frame pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="b7fb1-102">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="b7fb1-103">Spécifie le nombre de caractères la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="b7fb1-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="b7fb1-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="b7fb1-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b7fb1-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour les contrôles d’élément de CustomItem vue (Format) pour CustomEntry pour les contrôles d’élément de Frame de vue (Format) pour CustomItem pour les contrôles d’élément de FirstLineIndent vue (Format) du cadre des contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="b7fb1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineIndent Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7fb1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7fb1-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7fb1-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="b7fb1-107">Attributes and Elements</span></span>

<span data-ttu-id="b7fb1-108">Les sections suivantes décrivent des attributs, éléments enfants et élément parent de la `FirstLineIndent` élément.</span><span class="sxs-lookup"><span data-stu-id="b7fb1-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7fb1-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="b7fb1-109">Attributes</span></span>

<span data-ttu-id="b7fb1-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b7fb1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7fb1-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b7fb1-111">Child Elements</span></span>

<span data-ttu-id="b7fb1-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b7fb1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b7fb1-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b7fb1-113">Parent Elements</span></span>

|<span data-ttu-id="b7fb1-114">Élément</span><span class="sxs-lookup"><span data-stu-id="b7fb1-114">Element</span></span>|<span data-ttu-id="b7fb1-115">Description</span><span class="sxs-lookup"><span data-stu-id="b7fb1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7fb1-116">Élément de frame pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="b7fb1-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b7fb1-117">Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.</span><span class="sxs-lookup"><span data-stu-id="b7fb1-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b7fb1-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="b7fb1-118">Text Value</span></span>

<span data-ttu-id="b7fb1-119">Spécifiez le nombre de caractères que vous souhaitez déplacer la première ligne des données.</span><span class="sxs-lookup"><span data-stu-id="b7fb1-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7fb1-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="b7fb1-120">Remarks</span></span>

<span data-ttu-id="b7fb1-121">Si cet élément est spécifié, vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="b7fb1-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7fb1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7fb1-122">See Also</span></span>

[<span data-ttu-id="b7fb1-123">Élément FirstLineHanging pour Frame pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="b7fb1-123">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="b7fb1-124">Élément de frame pour CustomItem pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="b7fb1-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b7fb1-125">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7fb1-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
