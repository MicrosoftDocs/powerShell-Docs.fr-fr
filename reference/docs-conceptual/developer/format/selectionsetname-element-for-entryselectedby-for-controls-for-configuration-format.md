---
title: Élément SelectionSetName pour EntrySelectedBy pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364788"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="9d76a-102">SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d76a-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9d76a-103">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9d76a-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="9d76a-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9d76a-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9d76a-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration ( Format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) SelectionSetName, élément pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="9d76a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d76a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d76a-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d76a-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="9d76a-107">Attributes and Elements</span></span>

<span data-ttu-id="9d76a-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="9d76a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d76a-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="9d76a-109">Attributes</span></span>

<span data-ttu-id="9d76a-110">aucune.</span><span class="sxs-lookup"><span data-stu-id="9d76a-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d76a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9d76a-111">Child Elements</span></span>

<span data-ttu-id="9d76a-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9d76a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9d76a-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9d76a-113">Parent Elements</span></span>

|<span data-ttu-id="9d76a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="9d76a-114">Element</span></span>|<span data-ttu-id="9d76a-115">Description</span><span class="sxs-lookup"><span data-stu-id="9d76a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d76a-116">Élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="9d76a-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="9d76a-117">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="9d76a-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9d76a-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="9d76a-118">Text Value</span></span>

<span data-ttu-id="9d76a-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="9d76a-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d76a-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="9d76a-120">Remarks</span></span>

<span data-ttu-id="9d76a-121">Chaque définition de contrôle doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="9d76a-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9d76a-122">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="9d76a-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="9d76a-123">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9d76a-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d76a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d76a-124">See Also</span></span>

[<span data-ttu-id="9d76a-125">Élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="9d76a-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="9d76a-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d76a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
