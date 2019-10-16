---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368558"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="9a93c-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9a93c-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="9a93c-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="9a93c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="9a93c-104">Lorsque ce script est évalué à `true`, la condition est remplie et la définition d’entrée étendue est utilisée.</span><span class="sxs-lookup"><span data-stu-id="9a93c-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="9a93c-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) SelectionCondition, élément pour EntrySelectedBy pour WideEntry (format) élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9a93c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a93c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a93c-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a93c-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="9a93c-107">Attributes and Elements</span></span>

<span data-ttu-id="9a93c-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="9a93c-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a93c-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="9a93c-109">Attributes</span></span>

<span data-ttu-id="9a93c-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9a93c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a93c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9a93c-111">Child Elements</span></span>

<span data-ttu-id="9a93c-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="9a93c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a93c-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9a93c-113">Parent Elements</span></span>

|<span data-ttu-id="9a93c-114">Élément</span><span class="sxs-lookup"><span data-stu-id="9a93c-114">Element</span></span>|<span data-ttu-id="9a93c-115">Description</span><span class="sxs-lookup"><span data-stu-id="9a93c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a93c-116">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9a93c-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9a93c-117">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="9a93c-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a93c-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="9a93c-118">Text Value</span></span>

<span data-ttu-id="9a93c-119">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="9a93c-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a93c-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="9a93c-120">Remarks</span></span>

<span data-ttu-id="9a93c-121">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="9a93c-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="9a93c-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9a93c-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9a93c-123">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9a93c-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a93c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a93c-124">See Also</span></span>

[<span data-ttu-id="9a93c-125">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="9a93c-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9a93c-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="9a93c-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9a93c-127">PropertyName, élément de SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9a93c-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="9a93c-128">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9a93c-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9a93c-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a93c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
