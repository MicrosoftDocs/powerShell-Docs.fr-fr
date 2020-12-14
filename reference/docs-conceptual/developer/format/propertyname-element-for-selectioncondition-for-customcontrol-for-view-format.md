---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour SelectionCondition pour CustomControl pour View (Format)
description: PropertyName, élément pour SelectionCondition pour CustomControl pour View (Format)
ms.openlocfilehash: 1dd325a58b29a0f13b1341559c2a7dfe251c6b36
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665853"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="3d8e3-103">PropertyName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3d8e3-103">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="3d8e3-104">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="3d8e3-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="3d8e3-105">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3d8e3-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="3d8e3-106">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3d8e3-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3d8e3-107">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour l’élément View (format) CustomItem pour CustomEntry pour CustomControl pour View (format) EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (format) SelectionCondition element pour EntrySelectedBy pour CustomControl pour l’élément View (format) PropertyName pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3d8e3-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d8e3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d8e3-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d8e3-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3d8e3-109">Attributes and Elements</span></span>

<span data-ttu-id="3d8e3-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="3d8e3-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d8e3-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="3d8e3-111">Attributes</span></span>

<span data-ttu-id="3d8e3-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3d8e3-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d8e3-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3d8e3-113">Child Elements</span></span>

<span data-ttu-id="3d8e3-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3d8e3-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3d8e3-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3d8e3-115">Parent Elements</span></span>

|<span data-ttu-id="3d8e3-116">Élément</span><span class="sxs-lookup"><span data-stu-id="3d8e3-116">Element</span></span>|<span data-ttu-id="3d8e3-117">Description</span><span class="sxs-lookup"><span data-stu-id="3d8e3-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d8e3-118">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3d8e3-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="3d8e3-119">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="3d8e3-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3d8e3-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="3d8e3-120">Text Value</span></span>

<span data-ttu-id="3d8e3-121">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="3d8e3-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d8e3-122">Notes</span><span class="sxs-lookup"><span data-stu-id="3d8e3-122">Remarks</span></span>

<span data-ttu-id="3d8e3-123">La condition de sélection doit spécifier au moins un nom de propriété ou un script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="3d8e3-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="3d8e3-124">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3d8e3-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d8e3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d8e3-125">See Also</span></span>

[<span data-ttu-id="3d8e3-126">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3d8e3-126">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="3d8e3-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d8e3-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
