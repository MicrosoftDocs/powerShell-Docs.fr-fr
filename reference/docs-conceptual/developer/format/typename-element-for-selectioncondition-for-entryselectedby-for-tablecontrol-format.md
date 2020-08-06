---
title: Élément TypeName pour SelectionCondition pour EntrySelectedBy pour table ((format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b9367f0ea659b9dce8fe200a5a08873d53bc03a8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772584"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="d40ee-102">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d40ee-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="d40ee-103">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="d40ee-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="d40ee-104">Lorsque ce type est présent, la condition est remplie et la ligne de table est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d40ee-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="d40ee-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément table ((format) TableRowEntries, élément (format) TableRowEntry élément (format) élément EntrySelectedBy pour TableRowEntry (format) élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format) élément TypeName pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="d40ee-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d40ee-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d40ee-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d40ee-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d40ee-107">Attributes and Elements</span></span>

<span data-ttu-id="d40ee-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="d40ee-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d40ee-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="d40ee-109">Attributes</span></span>

<span data-ttu-id="d40ee-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d40ee-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d40ee-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d40ee-111">Child Elements</span></span>

<span data-ttu-id="d40ee-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d40ee-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d40ee-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d40ee-113">Parent Elements</span></span>

|<span data-ttu-id="d40ee-114">Élément</span><span class="sxs-lookup"><span data-stu-id="d40ee-114">Element</span></span>|<span data-ttu-id="d40ee-115">Description</span><span class="sxs-lookup"><span data-stu-id="d40ee-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d40ee-116">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d40ee-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="d40ee-117">Définit la condition qui doit exister pour cette ligne de table à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d40ee-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d40ee-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="d40ee-118">Text Value</span></span>

<span data-ttu-id="d40ee-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="d40ee-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d40ee-120">Notes</span><span class="sxs-lookup"><span data-stu-id="d40ee-120">Remarks</span></span>

<span data-ttu-id="d40ee-121">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="d40ee-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="d40ee-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d40ee-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d40ee-123">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d40ee-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d40ee-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d40ee-124">See Also</span></span>

[<span data-ttu-id="d40ee-125">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="d40ee-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d40ee-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="d40ee-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d40ee-127">Élément SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d40ee-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d40ee-128">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d40ee-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d40ee-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d40ee-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
