---
title: Élément SelectionSetName pour SelectionCondition pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368268"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="fe0af-102">SelectionSetName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="fe0af-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="fe0af-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="fe0af-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="fe0af-104">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="fe0af-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="fe0af-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fe0af-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="fe0af-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) CustomControl, élément (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour la vue (format) EntrySelectedBy , Élément de CustomEntry pour View (format)</span><span class="sxs-lookup"><span data-stu-id="fe0af-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe0af-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe0af-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe0af-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="fe0af-108">Attributes and Elements</span></span>

<span data-ttu-id="fe0af-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="fe0af-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe0af-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="fe0af-110">Attributes</span></span>

<span data-ttu-id="fe0af-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="fe0af-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe0af-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fe0af-112">Child Elements</span></span>

<span data-ttu-id="fe0af-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="fe0af-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe0af-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fe0af-114">Parent Elements</span></span>

|<span data-ttu-id="fe0af-115">Élément</span><span class="sxs-lookup"><span data-stu-id="fe0af-115">Element</span></span>|<span data-ttu-id="fe0af-116">Description</span><span class="sxs-lookup"><span data-stu-id="fe0af-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe0af-117">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="fe0af-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="fe0af-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="fe0af-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fe0af-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="fe0af-119">Text Value</span></span>

<span data-ttu-id="fe0af-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="fe0af-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe0af-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="fe0af-121">Remarks</span></span>

<span data-ttu-id="fe0af-122">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="fe0af-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="fe0af-123">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="fe0af-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="fe0af-124">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="fe0af-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="fe0af-125">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fe0af-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe0af-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe0af-126">See Also</span></span>

[<span data-ttu-id="fe0af-127">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="fe0af-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="fe0af-128">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="fe0af-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fe0af-129">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="fe0af-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="fe0af-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe0af-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
