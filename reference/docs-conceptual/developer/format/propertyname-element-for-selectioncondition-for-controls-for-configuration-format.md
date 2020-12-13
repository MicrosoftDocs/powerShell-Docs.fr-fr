---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)
description: PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)
ms.openlocfilehash: 5e4368a9546307c5ff223ae42ecaa1d2872bc587
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665955"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="0eb83-103">PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0eb83-103">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0eb83-104">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0eb83-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="0eb83-105">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et l’entrée est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0eb83-105">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="0eb83-106">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0eb83-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0eb83-107">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) CustomEntry, élément de CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) élément SelectionCondition pour EntrySelectedBy pour CustomEntry pour l’élément configuration (format) PropertyName pour SelectionCondition pour pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0eb83-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0eb83-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0eb83-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0eb83-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0eb83-109">Attributes and Elements</span></span>

<span data-ttu-id="0eb83-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="0eb83-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0eb83-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0eb83-111">Attributes</span></span>

<span data-ttu-id="0eb83-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0eb83-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0eb83-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0eb83-113">Child Elements</span></span>

<span data-ttu-id="0eb83-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0eb83-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0eb83-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0eb83-115">Parent Elements</span></span>

|<span data-ttu-id="0eb83-116">Élément</span><span class="sxs-lookup"><span data-stu-id="0eb83-116">Element</span></span>|<span data-ttu-id="0eb83-117">Description</span><span class="sxs-lookup"><span data-stu-id="0eb83-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0eb83-118">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0eb83-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="0eb83-119">Définit une condition qui doit exister pour qu’une définition de contrôle commun soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0eb83-119">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0eb83-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="0eb83-120">Text Value</span></span>

<span data-ttu-id="0eb83-121">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="0eb83-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="0eb83-122">Notes</span><span class="sxs-lookup"><span data-stu-id="0eb83-122">Remarks</span></span>

<span data-ttu-id="0eb83-123">La condition de sélection doit spécifier au moins un nom de propriété ou un script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="0eb83-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="0eb83-124">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0eb83-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0eb83-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0eb83-125">See Also</span></span>

[<span data-ttu-id="0eb83-126">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0eb83-126">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="0eb83-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0eb83-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
