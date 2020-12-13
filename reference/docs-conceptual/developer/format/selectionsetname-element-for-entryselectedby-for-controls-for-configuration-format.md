---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)
description: SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)
ms.openlocfilehash: b775aa8a3184aa3ebcbda17a8e3191c69d67a700
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645722"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="38c8e-103">SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="38c8e-103">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="38c8e-104">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="38c8e-104">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="38c8e-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="38c8e-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="38c8e-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) EntrySelectedBy, élément pour CustomEntry pour les contrôles de configuration (format) SelectionSetName pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="38c8e-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38c8e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38c8e-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="38c8e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="38c8e-108">Attributes and Elements</span></span>

<span data-ttu-id="38c8e-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="38c8e-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="38c8e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="38c8e-110">Attributes</span></span>

<span data-ttu-id="38c8e-111">None</span><span class="sxs-lookup"><span data-stu-id="38c8e-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="38c8e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38c8e-112">Child Elements</span></span>

<span data-ttu-id="38c8e-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="38c8e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="38c8e-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38c8e-114">Parent Elements</span></span>

|<span data-ttu-id="38c8e-115">Élément</span><span class="sxs-lookup"><span data-stu-id="38c8e-115">Element</span></span>|<span data-ttu-id="38c8e-116">Description</span><span class="sxs-lookup"><span data-stu-id="38c8e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38c8e-117">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="38c8e-117">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="38c8e-118">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="38c8e-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="38c8e-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="38c8e-119">Text Value</span></span>

<span data-ttu-id="38c8e-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="38c8e-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="38c8e-121">Notes</span><span class="sxs-lookup"><span data-stu-id="38c8e-121">Remarks</span></span>

<span data-ttu-id="38c8e-122">Chaque définition de contrôle doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="38c8e-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="38c8e-123">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="38c8e-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="38c8e-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="38c8e-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38c8e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38c8e-125">See Also</span></span>

[<span data-ttu-id="38c8e-126">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="38c8e-126">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="38c8e-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="38c8e-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
