---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 71fd969fd3e5c0a4e39762c9a026982a8ca2a9d1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785368"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="05f83-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="05f83-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="05f83-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="05f83-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="05f83-104">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) élément ScriptBlock pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="05f83-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="05f83-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05f83-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05f83-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="05f83-106">Attributes and Elements</span></span>

<span data-ttu-id="05f83-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="05f83-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="05f83-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="05f83-108">Attributes</span></span>

<span data-ttu-id="05f83-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="05f83-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="05f83-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="05f83-110">Child Elements</span></span>

<span data-ttu-id="05f83-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="05f83-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="05f83-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="05f83-112">Parent Elements</span></span>

|<span data-ttu-id="05f83-113">Élément</span><span class="sxs-lookup"><span data-stu-id="05f83-113">Element</span></span>|<span data-ttu-id="05f83-114">Description</span><span class="sxs-lookup"><span data-stu-id="05f83-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05f83-115">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="05f83-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="05f83-116">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="05f83-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="05f83-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="05f83-117">Text Value</span></span>

<span data-ttu-id="05f83-118">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="05f83-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="05f83-119">Notes</span><span class="sxs-lookup"><span data-stu-id="05f83-119">Remarks</span></span>

<span data-ttu-id="05f83-120">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="05f83-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="05f83-121">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="05f83-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05f83-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05f83-122">See Also</span></span>

[<span data-ttu-id="05f83-123">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="05f83-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="05f83-124">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="05f83-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="05f83-125">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="05f83-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="05f83-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="05f83-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
