---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854125"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="11f2d-102">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="11f2d-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="11f2d-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="11f2d-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="11f2d-104">Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de cette définition de l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="11f2d-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="11f2d-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément pour l’élément de SelectionCondition WideEntry (Format) pour EntrySelectedBy d’élément de SelectionSetName WideEntry (Format) pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="11f2d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11f2d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11f2d-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11f2d-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="11f2d-107">Attributes and Elements</span></span>

<span data-ttu-id="11f2d-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="11f2d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11f2d-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="11f2d-109">Attributes</span></span>

<span data-ttu-id="11f2d-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="11f2d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11f2d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="11f2d-111">Child Elements</span></span>

<span data-ttu-id="11f2d-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="11f2d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11f2d-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="11f2d-113">Parent Elements</span></span>

|<span data-ttu-id="11f2d-114">Élément</span><span class="sxs-lookup"><span data-stu-id="11f2d-114">Element</span></span>|<span data-ttu-id="11f2d-115">Description</span><span class="sxs-lookup"><span data-stu-id="11f2d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11f2d-116">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="11f2d-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="11f2d-117">Définit la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="11f2d-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="11f2d-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="11f2d-118">Text Value</span></span>

<span data-ttu-id="11f2d-119">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="11f2d-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="11f2d-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="11f2d-120">Remarks</span></span>

<span data-ttu-id="11f2d-121">La condition de sélection peut spécifier un jeu de sélection ou d’un type .NET, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="11f2d-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="11f2d-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="11f2d-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="11f2d-123">Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="11f2d-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="11f2d-124">Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="11f2d-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="11f2d-125">Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="11f2d-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11f2d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11f2d-126">See Also</span></span>

[<span data-ttu-id="11f2d-127">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="11f2d-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="11f2d-128">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="11f2d-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="11f2d-129">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="11f2d-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="11f2d-130">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="11f2d-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="11f2d-131">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="11f2d-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="11f2d-132">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="11f2d-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
