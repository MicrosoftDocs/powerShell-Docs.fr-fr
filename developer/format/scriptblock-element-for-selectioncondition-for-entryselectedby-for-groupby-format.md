---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064338"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="08651-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="08651-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="08651-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="08651-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="08651-104">Lorsque ce script est évalué à `true`, la condition est remplie et que la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="08651-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="08651-105">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="08651-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="08651-106">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de EntrySelectedBy GroupBy (Format) pour CustomEntry d’élément de SelectionCondition GroupBy (Format) pour EntrySelectedBy pour GroupBy (Format), élément ScriptBlock pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="08651-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08651-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08651-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08651-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="08651-108">Attributes and Elements</span></span>

<span data-ttu-id="08651-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="08651-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="08651-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="08651-110">Attributes</span></span>

<span data-ttu-id="08651-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="08651-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08651-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="08651-112">Child Elements</span></span>

<span data-ttu-id="08651-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="08651-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="08651-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="08651-114">Parent Elements</span></span>

|<span data-ttu-id="08651-115">Élément</span><span class="sxs-lookup"><span data-stu-id="08651-115">Element</span></span>|<span data-ttu-id="08651-116">Description</span><span class="sxs-lookup"><span data-stu-id="08651-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08651-117">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="08651-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="08651-118">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="08651-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="08651-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="08651-119">Text Value</span></span>

<span data-ttu-id="08651-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="08651-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="08651-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="08651-121">Remarks</span></span>

<span data-ttu-id="08651-122">La condition de sélection doit spécifier un moins un script ou le nom à évaluer, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="08651-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="08651-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="08651-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="08651-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08651-124">See Also</span></span>

[<span data-ttu-id="08651-125">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="08651-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="08651-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="08651-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
