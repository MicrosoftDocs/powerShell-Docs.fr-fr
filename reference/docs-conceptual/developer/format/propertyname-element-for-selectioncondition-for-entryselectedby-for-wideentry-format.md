---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)
description: PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)
ms.openlocfilehash: bda34b0c1e97fb85536132bedcec3986072801b7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665700"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="1ac5c-103">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1ac5c-103">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="1ac5c-104">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1ac5c-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1ac5c-105">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="1ac5c-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="1ac5c-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément SelectionCondition pour EntrySelectedBy (format) NomPropriété, élément pour WideEntry pour SelectionCondition (format)</span><span class="sxs-lookup"><span data-stu-id="1ac5c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ac5c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ac5c-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ac5c-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1ac5c-108">Attributes and Elements</span></span>

<span data-ttu-id="1ac5c-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="1ac5c-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ac5c-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="1ac5c-110">Attributes</span></span>

<span data-ttu-id="1ac5c-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1ac5c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ac5c-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1ac5c-112">Child Elements</span></span>

<span data-ttu-id="1ac5c-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1ac5c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ac5c-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1ac5c-114">Parent Elements</span></span>

|<span data-ttu-id="1ac5c-115">Élément</span><span class="sxs-lookup"><span data-stu-id="1ac5c-115">Element</span></span>|<span data-ttu-id="1ac5c-116">Description</span><span class="sxs-lookup"><span data-stu-id="1ac5c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ac5c-117">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1ac5c-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="1ac5c-118">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="1ac5c-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ac5c-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="1ac5c-119">Text Value</span></span>

<span data-ttu-id="1ac5c-120">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="1ac5c-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ac5c-121">Notes</span><span class="sxs-lookup"><span data-stu-id="1ac5c-121">Remarks</span></span>

<span data-ttu-id="1ac5c-122">La condition de sélection doit spécifier au moins un nom de propriété ou un script à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="1ac5c-122">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1ac5c-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1ac5c-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1ac5c-124">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1ac5c-124">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ac5c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ac5c-125">See Also</span></span>

[<span data-ttu-id="1ac5c-126">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="1ac5c-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1ac5c-127">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="1ac5c-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1ac5c-128">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1ac5c-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1ac5c-129">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1ac5c-129">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1ac5c-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ac5c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
