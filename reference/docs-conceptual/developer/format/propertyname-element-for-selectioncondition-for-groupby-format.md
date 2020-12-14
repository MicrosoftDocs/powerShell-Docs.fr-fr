---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour SelectionCondition pour GroupBy (Format)
description: PropertyName, élément pour SelectionCondition pour GroupBy (Format)
ms.openlocfilehash: b89fead6185c88ca03956dc265135833696b91d7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665666"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="e0506-103">PropertyName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0506-103">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="e0506-104">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e0506-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e0506-105">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e0506-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="e0506-106">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="e0506-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e0506-107">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour View (format) CustomControl, élément pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) EntrySelectedBy element pour CustomEntry pour GroupBy (format).</span><span class="sxs-lookup"><span data-stu-id="e0506-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0506-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0506-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0506-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e0506-109">Attributes and Elements</span></span>

<span data-ttu-id="e0506-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="e0506-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0506-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e0506-111">Attributes</span></span>

<span data-ttu-id="e0506-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e0506-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0506-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e0506-113">Child Elements</span></span>

<span data-ttu-id="e0506-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e0506-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e0506-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e0506-115">Parent Elements</span></span>

|<span data-ttu-id="e0506-116">Élément</span><span class="sxs-lookup"><span data-stu-id="e0506-116">Element</span></span>|<span data-ttu-id="e0506-117">Description</span><span class="sxs-lookup"><span data-stu-id="e0506-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0506-118">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0506-118">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="e0506-119">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e0506-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e0506-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="e0506-120">Text Value</span></span>

<span data-ttu-id="e0506-121">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="e0506-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0506-122">Notes</span><span class="sxs-lookup"><span data-stu-id="e0506-122">Remarks</span></span>

<span data-ttu-id="e0506-123">La condition de sélection doit spécifier au moins un nom de propriété ou un script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="e0506-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="e0506-124">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e0506-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0506-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0506-125">See Also</span></span>

[<span data-ttu-id="e0506-126">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0506-126">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="e0506-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0506-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
