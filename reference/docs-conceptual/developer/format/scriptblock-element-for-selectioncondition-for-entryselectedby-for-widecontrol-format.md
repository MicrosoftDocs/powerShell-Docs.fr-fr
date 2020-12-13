---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)
description: ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)
ms.openlocfilehash: 53d3eba9d453dbcc96afbe8f81a16b61573f2874
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651971"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="e467e-103">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e467e-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="e467e-104">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e467e-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e467e-105">Lorsque ce script est évalué à `true` , la condition est remplie et la définition d’entrée étendue est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e467e-105">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="e467e-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément SelectionCondition pour EntrySelectedBy pour WideEntry (format) élément ScriptBlock pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="e467e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e467e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e467e-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e467e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e467e-108">Attributes and Elements</span></span>

<span data-ttu-id="e467e-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="e467e-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e467e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e467e-110">Attributes</span></span>

<span data-ttu-id="e467e-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e467e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e467e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e467e-112">Child Elements</span></span>

<span data-ttu-id="e467e-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e467e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e467e-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e467e-114">Parent Elements</span></span>

|<span data-ttu-id="e467e-115">Élément</span><span class="sxs-lookup"><span data-stu-id="e467e-115">Element</span></span>|<span data-ttu-id="e467e-116">Description</span><span class="sxs-lookup"><span data-stu-id="e467e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e467e-117">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e467e-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="e467e-118">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e467e-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e467e-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="e467e-119">Text Value</span></span>

<span data-ttu-id="e467e-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="e467e-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e467e-121">Notes</span><span class="sxs-lookup"><span data-stu-id="e467e-121">Remarks</span></span>

<span data-ttu-id="e467e-122">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="e467e-122">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e467e-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e467e-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e467e-124">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e467e-124">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e467e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e467e-125">See Also</span></span>

[<span data-ttu-id="e467e-126">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="e467e-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e467e-127">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="e467e-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e467e-128">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e467e-128">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="e467e-129">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e467e-129">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e467e-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e467e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
