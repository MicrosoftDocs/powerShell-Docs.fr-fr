---
title: PropertyName, élément de SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c0081cb724ccaf1c04241aafa177880d7c0e5dbe
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783464"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="0434c-102">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="0434c-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="0434c-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0434c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="0434c-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0434c-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="0434c-105">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) élément EntrySelectedBy pour EnumerableExpansion (format) élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (format) NomPropriété, élément pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="0434c-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0434c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0434c-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0434c-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0434c-107">Attributes and Elements</span></span>

<span data-ttu-id="0434c-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="0434c-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0434c-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="0434c-109">Attributes</span></span>

<span data-ttu-id="0434c-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0434c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0434c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0434c-111">Child Elements</span></span>

<span data-ttu-id="0434c-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0434c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0434c-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0434c-113">Parent Elements</span></span>

|<span data-ttu-id="0434c-114">Élément</span><span class="sxs-lookup"><span data-stu-id="0434c-114">Element</span></span>|<span data-ttu-id="0434c-115">Description</span><span class="sxs-lookup"><span data-stu-id="0434c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0434c-116">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="0434c-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0434c-117">Définit la condition qui doit exister pour développer les objets de collection de cette définition.</span><span class="sxs-lookup"><span data-stu-id="0434c-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0434c-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="0434c-118">Text Value</span></span>

<span data-ttu-id="0434c-119">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="0434c-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="0434c-120">Notes</span><span class="sxs-lookup"><span data-stu-id="0434c-120">Remarks</span></span>

<span data-ttu-id="0434c-121">La condition de sélection doit spécifier au moins un nom de propriété ou un script à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="0434c-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="0434c-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0434c-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0434c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0434c-123">See Also</span></span>

[<span data-ttu-id="0434c-124">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="0434c-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0434c-125">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="0434c-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="0434c-126">SelectionCondition, élément pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="0434c-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="0434c-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0434c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
