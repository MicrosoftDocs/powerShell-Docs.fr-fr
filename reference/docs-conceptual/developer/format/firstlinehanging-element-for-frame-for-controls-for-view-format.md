---
title: Élément FirstLineHanging pour frame pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363788"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="f21dd-102">FirstLineHanging, élément pour Frame pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="f21dd-102">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="f21dd-103">Spécifie le nombre de caractères que la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="f21dd-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="f21dd-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="f21dd-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f21dd-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour les contrôles pour l’élément CustomItem (format) View pour CustomEntry pour les contrôles pour l’élément Frame (format) de la vue pour CustomItem pour les contrôles pour l’élément FirstLineHanging de vue (format) de Frame de contrôles de vue (format)</span><span class="sxs-lookup"><span data-stu-id="f21dd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineHanging Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f21dd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f21dd-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f21dd-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="f21dd-107">Attributes and Elements</span></span>

<span data-ttu-id="f21dd-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `FirstLineHanging`.</span><span class="sxs-lookup"><span data-stu-id="f21dd-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f21dd-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="f21dd-109">Attributes</span></span>

<span data-ttu-id="f21dd-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f21dd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f21dd-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f21dd-111">Child Elements</span></span>

<span data-ttu-id="f21dd-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f21dd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f21dd-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f21dd-113">Parent Elements</span></span>

|<span data-ttu-id="f21dd-114">Élément</span><span class="sxs-lookup"><span data-stu-id="f21dd-114">Element</span></span>|<span data-ttu-id="f21dd-115">Description</span><span class="sxs-lookup"><span data-stu-id="f21dd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f21dd-116">Élément Frame pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f21dd-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="f21dd-117">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="f21dd-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f21dd-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="f21dd-118">Text Value</span></span>

<span data-ttu-id="f21dd-119">Spécifiez le nombre de caractères dont vous souhaitez déplacer la première ligne des données.</span><span class="sxs-lookup"><span data-stu-id="f21dd-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="f21dd-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="f21dd-120">Remarks</span></span>

<span data-ttu-id="f21dd-121">Si cet élément est spécifié, vous ne pouvez pas spécifier l’élément [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) .</span><span class="sxs-lookup"><span data-stu-id="f21dd-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f21dd-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f21dd-122">See Also</span></span>

[<span data-ttu-id="f21dd-123">Élément FirstLineIndent pour frame pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f21dd-123">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="f21dd-124">Élément Frame pour CustomItem pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f21dd-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="f21dd-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="f21dd-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
