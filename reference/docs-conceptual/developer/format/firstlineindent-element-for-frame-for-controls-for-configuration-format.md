---
title: Élément FirstLineIndent pour frame pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363118"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="99334-102">FirstLineIndent, élément pour Frame pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="99334-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="99334-103">Spécifie le nombre de caractères que la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="99334-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="99334-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="99334-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="99334-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration ( Format) élément CustomEntry pour CustomControl pour les contrôles pour la configuration (format) élément CustomItem pour CustomEntry pour les contrôles de l’élément frame de configuration pour CustomItem pour les contrôles pour la configuration (format) élément FirstLineIndent pour le frame pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="99334-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="99334-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99334-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99334-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="99334-107">Attributes and Elements</span></span>

<span data-ttu-id="99334-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `FirstLineIndent`.</span><span class="sxs-lookup"><span data-stu-id="99334-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="99334-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="99334-109">Attributes</span></span>

<span data-ttu-id="99334-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="99334-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="99334-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="99334-111">Child Elements</span></span>

<span data-ttu-id="99334-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="99334-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="99334-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="99334-113">Parent Elements</span></span>

|<span data-ttu-id="99334-114">Élément</span><span class="sxs-lookup"><span data-stu-id="99334-114">Element</span></span>|<span data-ttu-id="99334-115">Description</span><span class="sxs-lookup"><span data-stu-id="99334-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99334-116">Élément Frame pour CustomItem pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="99334-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="99334-117">Définit le mode d’affichage des données, par exemple en décalant les données à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="99334-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="99334-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="99334-118">Text Value</span></span>

<span data-ttu-id="99334-119">Spécifiez le nombre de caractères dont vous souhaitez déplacer la première ligne des données.</span><span class="sxs-lookup"><span data-stu-id="99334-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="99334-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="99334-120">Remarks</span></span>

<span data-ttu-id="99334-121">Si cet élément est spécifié, vous ne pouvez pas spécifier l’élément [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) .</span><span class="sxs-lookup"><span data-stu-id="99334-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="99334-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99334-122">See Also</span></span>

[<span data-ttu-id="99334-123">Élément FirstLineHanging pour frame pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="99334-123">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="99334-124">Élément Frame pour CustomItem pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="99334-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="99334-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="99334-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
