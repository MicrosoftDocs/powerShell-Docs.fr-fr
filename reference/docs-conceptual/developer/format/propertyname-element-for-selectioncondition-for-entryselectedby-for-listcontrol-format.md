---
title: PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362288"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="1fbe7-102">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1fbe7-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="1fbe7-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1fbe7-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1fbe7-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et l’entrée de liste est utilisée.</span><span class="sxs-lookup"><span data-stu-id="1fbe7-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="1fbe7-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément SelectionCondition pour EntrySelectedBy pour ListEntry (format) PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1fbe7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1fbe7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fbe7-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1fbe7-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="1fbe7-107">Attributes and Elements</span></span>

<span data-ttu-id="1fbe7-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="1fbe7-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1fbe7-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="1fbe7-109">Attributes</span></span>

<span data-ttu-id="1fbe7-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1fbe7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1fbe7-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1fbe7-111">Child Elements</span></span>

<span data-ttu-id="1fbe7-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1fbe7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1fbe7-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1fbe7-113">Parent Elements</span></span>

|<span data-ttu-id="1fbe7-114">Élément</span><span class="sxs-lookup"><span data-stu-id="1fbe7-114">Element</span></span>|<span data-ttu-id="1fbe7-115">Description</span><span class="sxs-lookup"><span data-stu-id="1fbe7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1fbe7-116">Élément SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1fbe7-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1fbe7-117">Définit la condition qui doit exister pour que cette entrée de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="1fbe7-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1fbe7-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="1fbe7-118">Text Value</span></span>

<span data-ttu-id="1fbe7-119">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="1fbe7-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fbe7-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="1fbe7-120">Remarks</span></span>

<span data-ttu-id="1fbe7-121">La condition de sélection doit spécifier au moins un nom de propriété ou un bloc de script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="1fbe7-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="1fbe7-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1fbe7-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1fbe7-123">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez Création d’une [vue Liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1fbe7-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1fbe7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fbe7-124">See Also</span></span>

[<span data-ttu-id="1fbe7-125">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="1fbe7-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1fbe7-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="1fbe7-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1fbe7-127">Élément ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1fbe7-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="1fbe7-128">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1fbe7-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1fbe7-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1fbe7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
