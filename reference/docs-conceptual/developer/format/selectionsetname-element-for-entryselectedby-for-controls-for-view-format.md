---
title: Élément SelectionSetName pour EntrySelectedBy pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368348"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="8f596-102">SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="8f596-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="8f596-103">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="8f596-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="8f596-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="8f596-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8f596-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément d’affichage (format) CustomEntry pour CustomEntries pour les contrôles pour l’élément EntrySelectedBy (format) de vue pour CustomEntry pour les contrôles pour l’élément d’affichage (format) SelectionSetName pour les contrôles pour la vue ( Format</span><span class="sxs-lookup"><span data-stu-id="8f596-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f596-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f596-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f596-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="8f596-107">Attributes and Elements</span></span>

<span data-ttu-id="8f596-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="8f596-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f596-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="8f596-109">Attributes</span></span>

<span data-ttu-id="8f596-110">aucune.</span><span class="sxs-lookup"><span data-stu-id="8f596-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f596-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8f596-111">Child Elements</span></span>

<span data-ttu-id="8f596-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="8f596-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8f596-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8f596-113">Parent Elements</span></span>

|<span data-ttu-id="8f596-114">Élément</span><span class="sxs-lookup"><span data-stu-id="8f596-114">Element</span></span>|<span data-ttu-id="8f596-115">Description</span><span class="sxs-lookup"><span data-stu-id="8f596-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f596-116">Élément EntrySelectedBy pour CustomEntry pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8f596-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="8f596-117">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="8f596-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8f596-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="8f596-118">Text Value</span></span>

<span data-ttu-id="8f596-119">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="8f596-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f596-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="8f596-120">Remarks</span></span>

<span data-ttu-id="8f596-121">Chaque définition de contrôle doit avoir au moins un nom de type, un jeu de sélection ou une condition de sélection définis.</span><span class="sxs-lookup"><span data-stu-id="8f596-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8f596-122">Les jeux de sélection sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="8f596-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="8f596-123">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition de jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8f596-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f596-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f596-124">See Also</span></span>

[<span data-ttu-id="8f596-125">Élément EntrySelectedBy pour CustomEntry pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8f596-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="8f596-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f596-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
