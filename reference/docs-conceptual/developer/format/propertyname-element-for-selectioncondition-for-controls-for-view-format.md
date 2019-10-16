---
title: Élément PropertyName pour SelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362358"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="ba179-102">PropertyName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ba179-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="ba179-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ba179-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ba179-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et l’entrée est utilisée.</span><span class="sxs-lookup"><span data-stu-id="ba179-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="ba179-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="ba179-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ba179-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément d’affichage (format) CustomEntry pour CustomEntries pour les contrôles pour l’élément EntrySelectedBy (format) de vue pour CustomEntry pour les contrôles pour l’élément d’affichage (format) SelectionCondition pour les contrôles pour la vue ( Format) PropertyName, élément de SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="ba179-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ba179-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba179-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ba179-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ba179-108">Attributes and Elements</span></span>

<span data-ttu-id="ba179-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="ba179-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ba179-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="ba179-110">Attributes</span></span>

<span data-ttu-id="ba179-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ba179-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ba179-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ba179-112">Child Elements</span></span>

<span data-ttu-id="ba179-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ba179-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ba179-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ba179-114">Parent Elements</span></span>

|<span data-ttu-id="ba179-115">Élément</span><span class="sxs-lookup"><span data-stu-id="ba179-115">Element</span></span>|<span data-ttu-id="ba179-116">Description</span><span class="sxs-lookup"><span data-stu-id="ba179-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ba179-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="ba179-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="ba179-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="ba179-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ba179-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="ba179-119">Text Value</span></span>

<span data-ttu-id="ba179-120">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="ba179-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba179-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="ba179-121">Remarks</span></span>

<span data-ttu-id="ba179-122">La condition de sélection doit spécifier au moins un nom de propriété ou un script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="ba179-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="ba179-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ba179-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba179-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba179-124">See Also</span></span>

[<span data-ttu-id="ba179-125">Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="ba179-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="ba179-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba179-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
