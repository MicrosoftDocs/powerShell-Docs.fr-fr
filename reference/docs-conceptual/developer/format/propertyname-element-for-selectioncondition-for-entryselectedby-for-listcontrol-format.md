---
title: PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3f0a6b6b381f39492da36dab271503fc7cf6e7fc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785555"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="7e513-102">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7e513-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="7e513-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="7e513-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7e513-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et l’entrée de liste est utilisée.</span><span class="sxs-lookup"><span data-stu-id="7e513-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="7e513-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour l’élément EntrySelectedBy pour ListEntry (format) PropertyName pour SelectionCondition pour l’élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="7e513-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7e513-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e513-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7e513-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7e513-107">Attributes and Elements</span></span>

<span data-ttu-id="7e513-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="7e513-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7e513-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="7e513-109">Attributes</span></span>

<span data-ttu-id="7e513-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7e513-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7e513-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7e513-111">Child Elements</span></span>

<span data-ttu-id="7e513-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7e513-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7e513-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7e513-113">Parent Elements</span></span>

|<span data-ttu-id="7e513-114">Élément</span><span class="sxs-lookup"><span data-stu-id="7e513-114">Element</span></span>|<span data-ttu-id="7e513-115">Description</span><span class="sxs-lookup"><span data-stu-id="7e513-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e513-116">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="7e513-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="7e513-117">Définit la condition qui doit exister pour que cette entrée de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="7e513-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7e513-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="7e513-118">Text Value</span></span>

<span data-ttu-id="7e513-119">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="7e513-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e513-120">Notes</span><span class="sxs-lookup"><span data-stu-id="7e513-120">Remarks</span></span>

<span data-ttu-id="7e513-121">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="7e513-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="7e513-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7e513-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7e513-123">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez Création d’une [vue Liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7e513-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e513-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e513-124">See Also</span></span>

[<span data-ttu-id="7e513-125">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="7e513-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7e513-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="7e513-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7e513-127">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="7e513-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="7e513-128">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="7e513-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="7e513-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="7e513-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
