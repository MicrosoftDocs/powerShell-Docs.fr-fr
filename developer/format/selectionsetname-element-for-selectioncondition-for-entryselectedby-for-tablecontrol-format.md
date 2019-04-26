---
title: Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064048"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="5fe0f-102">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5fe0f-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="5fe0f-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="5fe0f-104">Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de cette définition de la vue de table.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="5fe0f-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableRowEntries, élément (Format) élément TableRowEntry (Format) EntrySelectedBy élément de configuration pour TableRowEntry (Format) Élément SelectionCondition pour EntrySelectedBy d’élément de SelectionSetName TableRowEntry (Format) pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5fe0f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5fe0f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fe0f-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5fe0f-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5fe0f-107">Attributes and Elements</span></span>

<span data-ttu-id="5fe0f-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5fe0f-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5fe0f-109">Attributes</span></span>

<span data-ttu-id="5fe0f-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5fe0f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5fe0f-111">Child Elements</span></span>

<span data-ttu-id="5fe0f-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5fe0f-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5fe0f-113">Parent Elements</span></span>

|<span data-ttu-id="5fe0f-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5fe0f-114">Element</span></span>|<span data-ttu-id="5fe0f-115">Description</span><span class="sxs-lookup"><span data-stu-id="5fe0f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5fe0f-116">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5fe0f-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="5fe0f-117">Définit la condition qui doit exister pour pouvoir le pour utiliser pour cette définition de la vue de table.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5fe0f-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="5fe0f-118">Text Value</span></span>

<span data-ttu-id="5fe0f-119">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="5fe0f-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="5fe0f-120">Remarks</span></span>

<span data-ttu-id="5fe0f-121">La condition de sélection peut spécifier un jeu de sélection ou d’un type .NET, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="5fe0f-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5fe0f-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5fe0f-123">Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="5fe0f-124">Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5fe0f-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="5fe0f-125">Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="5fe0f-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5fe0f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fe0f-126">See Also</span></span>

[<span data-ttu-id="5fe0f-127">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="5fe0f-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5fe0f-128">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="5fe0f-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5fe0f-129">Élément TypeName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5fe0f-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5fe0f-130">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5fe0f-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5fe0f-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fe0f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
