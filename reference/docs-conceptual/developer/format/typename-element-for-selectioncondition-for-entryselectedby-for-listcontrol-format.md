---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)
description: TypeName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)
ms.openlocfilehash: 2e8246e3ef2cba38824d8f8004acfffc3236df13
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645566"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="032a6-103">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="032a6-103">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="032a6-104">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="032a6-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="032a6-105">Lorsque ce type est présent, l’entrée de liste est utilisée.</span><span class="sxs-lookup"><span data-stu-id="032a6-105">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="032a6-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) élément EntrySelectedBy pour ListEntry pour ListControl (format) SelectionCondition élément pour EntrySelectedBy pour ListControl (format) TypeName, élément pour SelectionCondition pour pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="032a6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="032a6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="032a6-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="032a6-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="032a6-108">Attributes and Elements</span></span>

<span data-ttu-id="032a6-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="032a6-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="032a6-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="032a6-110">Attributes</span></span>

<span data-ttu-id="032a6-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="032a6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="032a6-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="032a6-112">Child Elements</span></span>

<span data-ttu-id="032a6-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="032a6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="032a6-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="032a6-114">Parent Elements</span></span>

|<span data-ttu-id="032a6-115">Élément</span><span class="sxs-lookup"><span data-stu-id="032a6-115">Element</span></span>|<span data-ttu-id="032a6-116">Description</span><span class="sxs-lookup"><span data-stu-id="032a6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="032a6-117">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="032a6-117">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="032a6-118">Définit la condition qui doit exister pour que cette entrée de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="032a6-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="032a6-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="032a6-119">Text Value</span></span>

<span data-ttu-id="032a6-120">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="032a6-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="032a6-121">Notes</span><span class="sxs-lookup"><span data-stu-id="032a6-121">Remarks</span></span>

<span data-ttu-id="032a6-122">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="032a6-122">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="032a6-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="032a6-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="032a6-124">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="032a6-124">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="032a6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="032a6-125">See Also</span></span>

[<span data-ttu-id="032a6-126">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="032a6-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="032a6-127">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="032a6-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="032a6-128">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="032a6-128">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="032a6-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="032a6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
