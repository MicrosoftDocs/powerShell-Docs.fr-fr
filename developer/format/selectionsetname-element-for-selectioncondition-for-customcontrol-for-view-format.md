---
title: Élément SelectionSetName pour SelectionCondition pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862765"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="c5224-102">SelectionSetName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c5224-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="c5224-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="c5224-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c5224-104">Quand les types dans cet ensemble sont présents, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="c5224-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="c5224-105">Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c5224-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="c5224-106">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément CustomControl (Format) CustomEntries élément de configuration pour CustomControl pour l’élément d’affichage (Format) de CustomEntry pour CustomEntries pour EntrySelectedBy de vue (Format) Élément pour CustomEntry de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="c5224-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c5224-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5224-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c5224-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="c5224-108">Attributes and Elements</span></span>

<span data-ttu-id="c5224-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="c5224-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5224-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="c5224-110">Attributes</span></span>

<span data-ttu-id="c5224-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c5224-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c5224-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c5224-112">Child Elements</span></span>

<span data-ttu-id="c5224-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c5224-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c5224-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c5224-114">Parent Elements</span></span>

|<span data-ttu-id="c5224-115">Élément</span><span class="sxs-lookup"><span data-stu-id="c5224-115">Element</span></span>|<span data-ttu-id="c5224-116">Description</span><span class="sxs-lookup"><span data-stu-id="c5224-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5224-117">Élément SelectionCondition pour EntrySelectedBy pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="c5224-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="c5224-118">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c5224-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c5224-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="c5224-119">Text Value</span></span>

<span data-ttu-id="c5224-120">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="c5224-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5224-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5224-121">Remarks</span></span>

<span data-ttu-id="c5224-122">Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="c5224-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c5224-123">Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c5224-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c5224-124">La condition de sélection peut spécifier un jeu de sélection ou d’un type .NET, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="c5224-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c5224-125">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c5224-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c5224-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5224-126">See Also</span></span>

[<span data-ttu-id="c5224-127">Élément SelectionCondition pour EntrySelectedBy pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="c5224-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="c5224-128">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="c5224-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c5224-129">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="c5224-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c5224-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5224-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
