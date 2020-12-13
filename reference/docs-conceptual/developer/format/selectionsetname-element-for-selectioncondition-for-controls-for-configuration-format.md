---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)
description: SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)
ms.openlocfilehash: 4177aace5a6a9374900e7339167c69b531c1e2e7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651653"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="0ad2c-103">SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ad2c-103">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0ad2c-104">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="0ad2c-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="0ad2c-105">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="0ad2c-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="0ad2c-106">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0ad2c-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0ad2c-107">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour les contrôles de configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format), élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format) SelectionSetName élément pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="0ad2c-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ad2c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ad2c-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ad2c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0ad2c-109">Attributes and Elements</span></span>

<span data-ttu-id="0ad2c-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="0ad2c-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ad2c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0ad2c-111">Attributes</span></span>

<span data-ttu-id="0ad2c-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0ad2c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ad2c-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0ad2c-113">Child Elements</span></span>

<span data-ttu-id="0ad2c-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0ad2c-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0ad2c-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0ad2c-115">Parent Elements</span></span>

|<span data-ttu-id="0ad2c-116">Élément</span><span class="sxs-lookup"><span data-stu-id="0ad2c-116">Element</span></span>|<span data-ttu-id="0ad2c-117">Description</span><span class="sxs-lookup"><span data-stu-id="0ad2c-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ad2c-118">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ad2c-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="0ad2c-119">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0ad2c-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0ad2c-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="0ad2c-120">Text Value</span></span>

<span data-ttu-id="0ad2c-121">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="0ad2c-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ad2c-122">Notes</span><span class="sxs-lookup"><span data-stu-id="0ad2c-122">Remarks</span></span>

<span data-ttu-id="0ad2c-123">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0ad2c-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="0ad2c-124">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0ad2c-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="0ad2c-125">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="0ad2c-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="0ad2c-126">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0ad2c-126">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ad2c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ad2c-127">See Also</span></span>

[<span data-ttu-id="0ad2c-128">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ad2c-128">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="0ad2c-129">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="0ad2c-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0ad2c-130">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="0ad2c-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0ad2c-131">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ad2c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
