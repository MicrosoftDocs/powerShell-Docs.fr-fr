---
title: Élément SelectionSetName pour EntrySelectedBy pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 72072d8d13e6ca22afdb9bca2e0237d29ba0594f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787561"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="77591-102">SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="77591-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="77591-103">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="77591-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="77591-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="77591-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="77591-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) EntrySelectedBy, élément pour CustomEntry pour les contrôles de configuration (format) SelectionSetName pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="77591-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77591-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77591-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="77591-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="77591-107">Attributes and Elements</span></span>

<span data-ttu-id="77591-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="77591-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77591-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="77591-109">Attributes</span></span>

<span data-ttu-id="77591-110">Aucun</span><span class="sxs-lookup"><span data-stu-id="77591-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="77591-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="77591-111">Child Elements</span></span>

<span data-ttu-id="77591-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="77591-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="77591-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="77591-113">Parent Elements</span></span>

|<span data-ttu-id="77591-114">Élément</span><span class="sxs-lookup"><span data-stu-id="77591-114">Element</span></span>|<span data-ttu-id="77591-115">Description</span><span class="sxs-lookup"><span data-stu-id="77591-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77591-116">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="77591-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="77591-117">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="77591-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="77591-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="77591-118">Text Value</span></span>

<span data-ttu-id="77591-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="77591-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="77591-120">Notes</span><span class="sxs-lookup"><span data-stu-id="77591-120">Remarks</span></span>

<span data-ttu-id="77591-121">Chaque définition de contrôle doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="77591-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="77591-122">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="77591-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="77591-123">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="77591-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77591-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77591-124">See Also</span></span>

[<span data-ttu-id="77591-125">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="77591-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="77591-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="77591-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
