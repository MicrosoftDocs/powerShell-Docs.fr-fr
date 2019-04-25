---
title: Élément SelectionSetName pour EntrySelectedBy pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075645"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="c7cae-102">SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c7cae-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="c7cae-103">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="c7cae-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="c7cae-104">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="c7cae-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c7cae-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles d’élément de CustomEntry vue (Format) pour CustomEntries pour les contrôles d’élément de EntrySelectedBy vue (Format) pour CustomEntry pour les contrôles d’élément de SelectionSetName vue (Format) pour EntrySelectedBy pour les contrôles pour afficher ( Format)</span><span class="sxs-lookup"><span data-stu-id="c7cae-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7cae-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7cae-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7cae-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="c7cae-107">Attributes and Elements</span></span>

<span data-ttu-id="c7cae-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="c7cae-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7cae-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c7cae-109">Attributes</span></span>

<span data-ttu-id="c7cae-110">Aucune</span><span class="sxs-lookup"><span data-stu-id="c7cae-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7cae-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c7cae-111">Child Elements</span></span>

<span data-ttu-id="c7cae-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c7cae-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c7cae-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c7cae-113">Parent Elements</span></span>

|<span data-ttu-id="c7cae-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c7cae-114">Element</span></span>|<span data-ttu-id="c7cae-115">Description</span><span class="sxs-lookup"><span data-stu-id="c7cae-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7cae-116">Élément EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="c7cae-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="c7cae-117">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c7cae-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c7cae-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="c7cae-118">Text Value</span></span>

<span data-ttu-id="c7cae-119">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="c7cae-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7cae-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="c7cae-120">Remarks</span></span>

<span data-ttu-id="c7cae-121">Chaque définition de contrôle doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="c7cae-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c7cae-122">Sélection jeux sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="c7cae-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="c7cae-123">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition sélection définit](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c7cae-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7cae-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7cae-124">See Also</span></span>

[<span data-ttu-id="c7cae-125">Élément EntrySelectedBy pour CustomEntry pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="c7cae-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="c7cae-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7cae-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
