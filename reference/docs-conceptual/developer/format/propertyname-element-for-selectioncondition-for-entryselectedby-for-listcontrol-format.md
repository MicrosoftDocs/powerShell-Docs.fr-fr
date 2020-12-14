---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)
description: PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)
ms.openlocfilehash: 1e318e3a29f07b157b9ae7343ba08759db8efbb5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665819"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="8affe-103">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8affe-103">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="8affe-104">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="8affe-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="8affe-105">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et l’entrée de liste est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8affe-105">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="8affe-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour l’élément EntrySelectedBy pour ListEntry (format) PropertyName pour SelectionCondition pour l’élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8affe-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8affe-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8affe-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8affe-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8affe-108">Attributes and Elements</span></span>

<span data-ttu-id="8affe-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="8affe-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8affe-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="8affe-110">Attributes</span></span>

<span data-ttu-id="8affe-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8affe-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8affe-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8affe-112">Child Elements</span></span>

<span data-ttu-id="8affe-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8affe-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8affe-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8affe-114">Parent Elements</span></span>

|<span data-ttu-id="8affe-115">Élément</span><span class="sxs-lookup"><span data-stu-id="8affe-115">Element</span></span>|<span data-ttu-id="8affe-116">Description</span><span class="sxs-lookup"><span data-stu-id="8affe-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8affe-117">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8affe-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="8affe-118">Définit la condition qui doit exister pour que cette entrée de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="8affe-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8affe-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="8affe-119">Text Value</span></span>

<span data-ttu-id="8affe-120">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="8affe-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="8affe-121">Notes</span><span class="sxs-lookup"><span data-stu-id="8affe-121">Remarks</span></span>

<span data-ttu-id="8affe-122">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="8affe-122">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="8affe-123">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8affe-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8affe-124">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez Création d’une [vue Liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8affe-124">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8affe-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8affe-125">See Also</span></span>

[<span data-ttu-id="8affe-126">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="8affe-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8affe-127">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="8affe-127">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8affe-128">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8affe-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="8affe-129">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8affe-129">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="8affe-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8affe-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
