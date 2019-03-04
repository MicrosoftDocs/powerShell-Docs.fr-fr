---
title: Élément SelectionSetName pour EntrySelectedBy pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856095"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a6970-102">SelectionSetName, élément pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a6970-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a6970-103">Spécifie qu'un ensemble de .NET types l’utilisation de cette entrée de la vue de table.</span><span class="sxs-lookup"><span data-stu-id="a6970-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="a6970-104">Il n’existe aucune limite au nombre de jeux de sélection peut être spécifié pour une entrée.</span><span class="sxs-lookup"><span data-stu-id="a6970-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="a6970-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) table, élément (Format) TableRowEntries, élément (Format) TableRowEntry, élément (Format) EntrySelectedBy, élément (Format) SelectionSetName élément de configuration pour EntrySelectedBy pour TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a6970-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6970-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6970-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6970-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="a6970-107">Attributes and Elements</span></span>

<span data-ttu-id="a6970-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a6970-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6970-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="a6970-109">Attributes</span></span>

<span data-ttu-id="a6970-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="a6970-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6970-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a6970-111">Child Elements</span></span>

<span data-ttu-id="a6970-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="a6970-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6970-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a6970-113">Parent Elements</span></span>

|<span data-ttu-id="a6970-114">Élément</span><span class="sxs-lookup"><span data-stu-id="a6970-114">Element</span></span>|<span data-ttu-id="a6970-115">Description</span><span class="sxs-lookup"><span data-stu-id="a6970-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6970-116">Élément EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a6970-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="a6970-117">Définit les types .NET qui utilisent cette entrée ou la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a6970-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a6970-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="a6970-118">Text Value</span></span>

<span data-ttu-id="a6970-119">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="a6970-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6970-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="a6970-120">Remarks</span></span>

<span data-ttu-id="a6970-121">Sélection jeux sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="a6970-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="a6970-122">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="a6970-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="a6970-123">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition définit des objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a6970-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a6970-124">Si vous spécifiez une jeu de sélection pour une entrée, vous ne pouvez pas spécifier un nom de type.</span><span class="sxs-lookup"><span data-stu-id="a6970-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="a6970-125">Pour plus d’informations sur la façon de spécifier un type .NET, consultez [TypeName élément pour EntrySelectedBy pour TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="a6970-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="a6970-126">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a6970-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6970-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6970-127">See Also</span></span>

[<span data-ttu-id="a6970-128">Élément EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a6970-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="a6970-129">Définition de jeux d’objets pour une vue</span><span class="sxs-lookup"><span data-stu-id="a6970-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a6970-130">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="a6970-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a6970-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6970-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
