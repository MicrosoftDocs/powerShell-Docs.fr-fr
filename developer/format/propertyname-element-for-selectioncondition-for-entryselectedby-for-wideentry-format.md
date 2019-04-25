---
title: Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064677"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="5fefa-102">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5fefa-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="5fefa-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="5fefa-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5fefa-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et que la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5fefa-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="5fefa-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément pour l’élément de SelectionCondition WideEntry (Format) pour EntrySelectedBy d’élément de PropertyName WideEntry (Format) pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5fefa-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5fefa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fefa-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5fefa-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5fefa-107">Attributes and Elements</span></span>

<span data-ttu-id="5fefa-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="5fefa-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5fefa-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5fefa-109">Attributes</span></span>

<span data-ttu-id="5fefa-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5fefa-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5fefa-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5fefa-111">Child Elements</span></span>

<span data-ttu-id="5fefa-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5fefa-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5fefa-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5fefa-113">Parent Elements</span></span>

|<span data-ttu-id="5fefa-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5fefa-114">Element</span></span>|<span data-ttu-id="5fefa-115">Description</span><span class="sxs-lookup"><span data-stu-id="5fefa-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5fefa-116">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5fefa-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="5fefa-117">Définit la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5fefa-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5fefa-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="5fefa-118">Text Value</span></span>

<span data-ttu-id="5fefa-119">Spécifiez le nom de propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="5fefa-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5fefa-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="5fefa-120">Remarks</span></span>

<span data-ttu-id="5fefa-121">La condition de sélection doit spécifier nom d’au moins une propriété ou un script pour évaluer, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="5fefa-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="5fefa-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5fefa-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5fefa-123">Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [Affichage large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="5fefa-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5fefa-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fefa-124">See Also</span></span>

[<span data-ttu-id="5fefa-125">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="5fefa-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5fefa-126">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="5fefa-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5fefa-127">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5fefa-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="5fefa-128">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5fefa-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="5fefa-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fefa-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
