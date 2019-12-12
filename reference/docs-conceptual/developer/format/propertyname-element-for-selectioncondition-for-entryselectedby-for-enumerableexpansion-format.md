---
title: PropertyName, élément de SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362318"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="3ad3a-102">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="3ad3a-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="3ad3a-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="3ad3a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="3ad3a-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3ad3a-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="3ad3a-105">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) PropertyName, élément de SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="3ad3a-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ad3a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ad3a-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ad3a-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="3ad3a-107">Attributes and Elements</span></span>

<span data-ttu-id="3ad3a-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="3ad3a-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ad3a-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="3ad3a-109">Attributes</span></span>

<span data-ttu-id="3ad3a-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3ad3a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ad3a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3ad3a-111">Child Elements</span></span>

<span data-ttu-id="3ad3a-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3ad3a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3ad3a-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3ad3a-113">Parent Elements</span></span>

|<span data-ttu-id="3ad3a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="3ad3a-114">Element</span></span>|<span data-ttu-id="3ad3a-115">Description</span><span class="sxs-lookup"><span data-stu-id="3ad3a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ad3a-116">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="3ad3a-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="3ad3a-117">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="3ad3a-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3ad3a-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="3ad3a-118">Text Value</span></span>

<span data-ttu-id="3ad3a-119">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="3ad3a-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ad3a-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="3ad3a-120">Remarks</span></span>

<span data-ttu-id="3ad3a-121">La condition de sélection doit spécifier au moins un nom de propriété ou un script à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="3ad3a-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="3ad3a-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3ad3a-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ad3a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ad3a-123">See Also</span></span>

[<span data-ttu-id="3ad3a-124">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="3ad3a-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3ad3a-125">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="3ad3a-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="3ad3a-126">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="3ad3a-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="3ad3a-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ad3a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
