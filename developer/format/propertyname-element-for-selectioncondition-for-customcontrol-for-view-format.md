---
title: Élément PropertyName pour SelectionCondition pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860965"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="0bedb-102">PropertyName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="0bedb-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="0bedb-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0bedb-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="0bedb-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et que la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0bedb-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="0bedb-105">Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0bedb-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0bedb-106">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) CustomControl élément pour élément d’affichage (Format) de CustomEntries pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour CustomControl pour la vue ( Format), élément CustomItem pour CustomEntry pour CustomControl pour l’élément d’affichage (Format) de EntrySelectedBy pour CustomEntry pour CustomControl pour l’élément d’affichage (Format) de SelectionCondition pour EntrySelectedBy pour CustomControl pour PropertyName de vue (Format) Élément pour SelectionCondition pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0bedb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0bedb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bedb-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0bedb-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="0bedb-108">Attributes and Elements</span></span>

<span data-ttu-id="0bedb-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="0bedb-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0bedb-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="0bedb-110">Attributes</span></span>

<span data-ttu-id="0bedb-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0bedb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0bedb-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0bedb-112">Child Elements</span></span>

<span data-ttu-id="0bedb-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0bedb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0bedb-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0bedb-114">Parent Elements</span></span>

|<span data-ttu-id="0bedb-115">Élément</span><span class="sxs-lookup"><span data-stu-id="0bedb-115">Element</span></span>|<span data-ttu-id="0bedb-116">Description</span><span class="sxs-lookup"><span data-stu-id="0bedb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0bedb-117">Élément SelectionCondition pour EntrySelectedBy pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0bedb-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="0bedb-118">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0bedb-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0bedb-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="0bedb-119">Text Value</span></span>

<span data-ttu-id="0bedb-120">Spécifiez le nom de propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="0bedb-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="0bedb-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="0bedb-121">Remarks</span></span>

<span data-ttu-id="0bedb-122">La condition de sélection doit spécifier un nom d’un propriété minimum ou un script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="0bedb-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="0bedb-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0bedb-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bedb-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bedb-124">See Also</span></span>

[<span data-ttu-id="0bedb-125">Élément SelectionCondition pour EntrySelectedBy pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="0bedb-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="0bedb-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0bedb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
