---
title: Élément FirstLineIndent pour frame pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363078"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a><span data-ttu-id="24e0e-102">FirstLineIndent, élément pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="24e0e-102">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="24e0e-103">Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="24e0e-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="24e0e-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="24e0e-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="24e0e-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément CustomItem pour CustomEntry pour l’élément de frame GroupBy (format) pour CustomItem pour l’élément GroupBy (format) FirstLineIndent pour le frame pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="24e0e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="24e0e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24e0e-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="24e0e-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="24e0e-107">Attributes and Elements</span></span>

<span data-ttu-id="24e0e-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `FirstLineIndent`.</span><span class="sxs-lookup"><span data-stu-id="24e0e-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="24e0e-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="24e0e-109">Attributes</span></span>

<span data-ttu-id="24e0e-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="24e0e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="24e0e-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="24e0e-111">Child Elements</span></span>

<span data-ttu-id="24e0e-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="24e0e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="24e0e-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="24e0e-113">Parent Elements</span></span>

|<span data-ttu-id="24e0e-114">Élément</span><span class="sxs-lookup"><span data-stu-id="24e0e-114">Element</span></span>|<span data-ttu-id="24e0e-115">Description</span><span class="sxs-lookup"><span data-stu-id="24e0e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="24e0e-116">Élément Frame pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="24e0e-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="24e0e-117">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="24e0e-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="24e0e-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="24e0e-118">Text Value</span></span>

<span data-ttu-id="24e0e-119">Spécifiez le nombre de caractères dont vous souhaitez déplacer la première ligne des données.</span><span class="sxs-lookup"><span data-stu-id="24e0e-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="24e0e-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="24e0e-120">Remarks</span></span>

<span data-ttu-id="24e0e-121">Si cet élément est spécifié, vous ne pouvez pas spécifier l’élément [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="24e0e-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="24e0e-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24e0e-122">See Also</span></span>

[<span data-ttu-id="24e0e-123">Élément FirstLineHanging pour frame pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="24e0e-123">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="24e0e-124">Élément Frame pour CustomItem pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="24e0e-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="24e0e-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="24e0e-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
