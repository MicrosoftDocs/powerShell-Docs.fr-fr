---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368598"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="bf925-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf925-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="bf925-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="bf925-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="bf925-104">Lorsque ce script est évalué pour `true`, la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="bf925-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="bf925-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="bf925-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bf925-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) EntrySelectedBy, élément pour CustomEntry pour GroupBy (format) élément SelectionCondition pour EntrySelectedBy pour l’élément ScriptBlock GroupBy (format) pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bf925-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bf925-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf925-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bf925-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="bf925-108">Attributes and Elements</span></span>

<span data-ttu-id="bf925-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="bf925-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bf925-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="bf925-110">Attributes</span></span>

<span data-ttu-id="bf925-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="bf925-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bf925-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bf925-112">Child Elements</span></span>

<span data-ttu-id="bf925-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="bf925-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bf925-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bf925-114">Parent Elements</span></span>

|<span data-ttu-id="bf925-115">Élément</span><span class="sxs-lookup"><span data-stu-id="bf925-115">Element</span></span>|<span data-ttu-id="bf925-116">Description</span><span class="sxs-lookup"><span data-stu-id="bf925-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bf925-117">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bf925-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bf925-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="bf925-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bf925-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="bf925-119">Text Value</span></span>

<span data-ttu-id="bf925-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="bf925-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf925-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="bf925-121">Remarks</span></span>

<span data-ttu-id="bf925-122">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="bf925-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="bf925-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bf925-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf925-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf925-124">See Also</span></span>

[<span data-ttu-id="bf925-125">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bf925-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bf925-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf925-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
