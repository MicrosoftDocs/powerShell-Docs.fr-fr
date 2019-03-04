---
title: Élément PropertyName pour SelectionCondition pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853525"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="63733-102">PropertyName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="63733-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="63733-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="63733-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="63733-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et l’entrée est utilisée.</span><span class="sxs-lookup"><span data-stu-id="63733-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="63733-105">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="63733-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="63733-106">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles d’élément de CustomEntry vue (Format) pour CustomEntries pour les contrôles d’élément de EntrySelectedBy vue (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition vue (Format) pour EntrySelectedBy pour les contrôles pour afficher ( Élément de PropertyName format) pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="63733-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63733-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63733-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63733-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="63733-108">Attributes and Elements</span></span>

<span data-ttu-id="63733-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="63733-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="63733-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="63733-110">Attributes</span></span>

<span data-ttu-id="63733-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="63733-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63733-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="63733-112">Child Elements</span></span>

<span data-ttu-id="63733-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="63733-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="63733-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="63733-114">Parent Elements</span></span>

|<span data-ttu-id="63733-115">Élément</span><span class="sxs-lookup"><span data-stu-id="63733-115">Element</span></span>|<span data-ttu-id="63733-116">Description</span><span class="sxs-lookup"><span data-stu-id="63733-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63733-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="63733-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="63733-118">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="63733-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="63733-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="63733-119">Text Value</span></span>

<span data-ttu-id="63733-120">Spécifiez le nom de propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="63733-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="63733-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="63733-121">Remarks</span></span>

<span data-ttu-id="63733-122">La condition de sélection doit spécifier un nom d’un propriété minimum ou un script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="63733-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="63733-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="63733-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63733-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63733-124">See Also</span></span>

[<span data-ttu-id="63733-125">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="63733-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="63733-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="63733-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
