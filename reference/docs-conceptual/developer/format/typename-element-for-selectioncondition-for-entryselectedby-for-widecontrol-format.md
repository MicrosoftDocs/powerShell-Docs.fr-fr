---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)
description: TypeName, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)
ms.openlocfilehash: af6e4782c345b43e16bce59c333bdaaceba0d845
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645499"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="449da-103">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="449da-103">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="449da-104">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="449da-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="449da-105">Lorsque ce type est présent, la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="449da-105">When this type is present, the definition is used.</span></span>

<span data-ttu-id="449da-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément SelectionCondition pour EntrySelectedBy pour WideEntry (format) élément TypeName pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="449da-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="449da-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="449da-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="449da-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="449da-108">Attributes and Elements</span></span>

<span data-ttu-id="449da-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="449da-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="449da-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="449da-110">Attributes</span></span>

<span data-ttu-id="449da-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="449da-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="449da-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="449da-112">Child Elements</span></span>

<span data-ttu-id="449da-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="449da-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="449da-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="449da-114">Parent Elements</span></span>

|<span data-ttu-id="449da-115">Élément</span><span class="sxs-lookup"><span data-stu-id="449da-115">Element</span></span>|<span data-ttu-id="449da-116">Description</span><span class="sxs-lookup"><span data-stu-id="449da-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="449da-117">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="449da-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="449da-118">Définit la condition qui doit exister pour cette grande entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="449da-118">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="449da-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="449da-119">Text Value</span></span>

<span data-ttu-id="449da-120">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="449da-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="449da-121">Notes</span><span class="sxs-lookup"><span data-stu-id="449da-121">Remarks</span></span>

<span data-ttu-id="449da-122">La condition de sélection peut spécifier un type .NET ou un jeu de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="449da-122">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="449da-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="449da-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="449da-124">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="449da-124">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="449da-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="449da-125">See Also</span></span>

[<span data-ttu-id="449da-126">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="449da-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="449da-127">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="449da-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="449da-128">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="449da-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="449da-129">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="449da-129">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="449da-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="449da-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
