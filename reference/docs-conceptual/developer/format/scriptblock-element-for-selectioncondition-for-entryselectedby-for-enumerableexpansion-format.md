---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368608"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="acae4-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="acae4-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="acae4-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="acae4-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="acae4-104">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="acae4-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="acae4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acae4-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="acae4-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="acae4-106">Attributes and Elements</span></span>

<span data-ttu-id="acae4-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="acae4-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="acae4-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="acae4-108">Attributes</span></span>

<span data-ttu-id="acae4-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="acae4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="acae4-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="acae4-110">Child Elements</span></span>

<span data-ttu-id="acae4-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="acae4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="acae4-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="acae4-112">Parent Elements</span></span>

|<span data-ttu-id="acae4-113">Élément</span><span class="sxs-lookup"><span data-stu-id="acae4-113">Element</span></span>|<span data-ttu-id="acae4-114">Description</span><span class="sxs-lookup"><span data-stu-id="acae4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="acae4-115">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="acae4-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="acae4-116">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="acae4-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="acae4-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="acae4-117">Text Value</span></span>

<span data-ttu-id="acae4-118">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="acae4-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="acae4-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="acae4-119">Remarks</span></span>

<span data-ttu-id="acae4-120">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="acae4-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="acae4-121">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="acae4-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="acae4-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acae4-122">See Also</span></span>

[<span data-ttu-id="acae4-123">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="acae4-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="acae4-124">PropertyName, élément de SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="acae4-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="acae4-125">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="acae4-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="acae4-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="acae4-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
