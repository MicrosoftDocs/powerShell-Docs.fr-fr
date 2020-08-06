---
title: Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bc58d630e65b316f9223bf3c529f928358e38ebc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787373"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="48b0c-102">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="48b0c-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="48b0c-103">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="48b0c-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="48b0c-104">Lorsque ce type est présent, l’entrée de liste est utilisée.</span><span class="sxs-lookup"><span data-stu-id="48b0c-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="48b0c-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) élément EntrySelectedBy pour ListEntry pour ListControl (format) SelectionCondition élément pour EntrySelectedBy pour ListControl (format) TypeName, élément pour SelectionCondition pour pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="48b0c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48b0c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48b0c-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48b0c-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="48b0c-107">Attributes and Elements</span></span>

<span data-ttu-id="48b0c-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="48b0c-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="48b0c-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="48b0c-109">Attributes</span></span>

<span data-ttu-id="48b0c-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="48b0c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48b0c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="48b0c-111">Child Elements</span></span>

<span data-ttu-id="48b0c-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="48b0c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="48b0c-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="48b0c-113">Parent Elements</span></span>

|<span data-ttu-id="48b0c-114">Élément</span><span class="sxs-lookup"><span data-stu-id="48b0c-114">Element</span></span>|<span data-ttu-id="48b0c-115">Description</span><span class="sxs-lookup"><span data-stu-id="48b0c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48b0c-116">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="48b0c-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="48b0c-117">Définit la condition qui doit exister pour que cette entrée de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="48b0c-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="48b0c-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="48b0c-118">Text Value</span></span>

<span data-ttu-id="48b0c-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="48b0c-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="48b0c-120">Notes</span><span class="sxs-lookup"><span data-stu-id="48b0c-120">Remarks</span></span>

<span data-ttu-id="48b0c-121">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="48b0c-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="48b0c-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="48b0c-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="48b0c-123">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="48b0c-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="48b0c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48b0c-124">See Also</span></span>

[<span data-ttu-id="48b0c-125">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="48b0c-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="48b0c-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="48b0c-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="48b0c-127">SelectionCondition, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="48b0c-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="48b0c-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="48b0c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
