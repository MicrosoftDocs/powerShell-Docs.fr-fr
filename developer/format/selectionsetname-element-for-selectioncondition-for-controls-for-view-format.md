---
title: Élément SelectionSetName pour SelectionCondition pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855115"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="10fc4-102">SelectionSetName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="10fc4-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="10fc4-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="10fc4-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="10fc4-104">Quand les types dans cet ensemble sont présents, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="10fc4-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="10fc4-105">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="10fc4-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="10fc4-106">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles d’élément de CustomEntry vue (Format) pour CustomEntries pour les contrôles d’élément de EntrySelectedBy vue (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition vue (Format) pour EntrySelectedBy pour les contrôles pour afficher ( Format), élément SelectionSetName pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="10fc4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="10fc4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10fc4-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10fc4-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="10fc4-108">Attributes and Elements</span></span>

<span data-ttu-id="10fc4-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="10fc4-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="10fc4-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="10fc4-110">Attributes</span></span>

<span data-ttu-id="10fc4-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="10fc4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="10fc4-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="10fc4-112">Child Elements</span></span>

<span data-ttu-id="10fc4-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="10fc4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="10fc4-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="10fc4-114">Parent Elements</span></span>

|<span data-ttu-id="10fc4-115">Élément</span><span class="sxs-lookup"><span data-stu-id="10fc4-115">Element</span></span>|<span data-ttu-id="10fc4-116">Description</span><span class="sxs-lookup"><span data-stu-id="10fc4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10fc4-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="10fc4-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="10fc4-118">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="10fc4-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="10fc4-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="10fc4-119">Text Value</span></span>

<span data-ttu-id="10fc4-120">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="10fc4-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="10fc4-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="10fc4-121">Remarks</span></span>

<span data-ttu-id="10fc4-122">Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="10fc4-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="10fc4-123">Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition sélection définit](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="10fc4-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="10fc4-124">La condition de sélection peut spécifier un jeu de sélection ou d’un type .NET, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="10fc4-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="10fc4-125">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="10fc4-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="10fc4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10fc4-126">See Also</span></span>

[<span data-ttu-id="10fc4-127">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="10fc4-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="10fc4-128">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="10fc4-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="10fc4-129">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="10fc4-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="10fc4-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="10fc4-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
