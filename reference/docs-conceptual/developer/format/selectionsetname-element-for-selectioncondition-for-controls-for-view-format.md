---
title: Élément SelectionSetName pour SelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361968"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="38c3b-102">SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="38c3b-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="38c3b-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="38c3b-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="38c3b-104">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="38c3b-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="38c3b-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="38c3b-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="38c3b-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément d’affichage (format) CustomEntry pour CustomEntries pour les contrôles pour l’élément EntrySelectedBy (format) de vue pour CustomEntry pour les contrôles pour l’élément d’affichage (format) SelectionCondition pour les contrôles pour la vue ( Format) élément SelectionSetName pour SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="38c3b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38c3b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38c3b-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38c3b-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="38c3b-108">Attributes and Elements</span></span>

<span data-ttu-id="38c3b-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="38c3b-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="38c3b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="38c3b-110">Attributes</span></span>

<span data-ttu-id="38c3b-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="38c3b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38c3b-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38c3b-112">Child Elements</span></span>

<span data-ttu-id="38c3b-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="38c3b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="38c3b-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38c3b-114">Parent Elements</span></span>

|<span data-ttu-id="38c3b-115">Élément</span><span class="sxs-lookup"><span data-stu-id="38c3b-115">Element</span></span>|<span data-ttu-id="38c3b-116">Description</span><span class="sxs-lookup"><span data-stu-id="38c3b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38c3b-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="38c3b-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="38c3b-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="38c3b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="38c3b-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="38c3b-119">Text Value</span></span>

<span data-ttu-id="38c3b-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="38c3b-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="38c3b-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="38c3b-121">Remarks</span></span>

<span data-ttu-id="38c3b-122">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="38c3b-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="38c3b-123">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="38c3b-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="38c3b-124">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="38c3b-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="38c3b-125">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="38c3b-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38c3b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38c3b-126">See Also</span></span>

[<span data-ttu-id="38c3b-127">Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="38c3b-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="38c3b-128">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="38c3b-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="38c3b-129">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="38c3b-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="38c3b-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="38c3b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
