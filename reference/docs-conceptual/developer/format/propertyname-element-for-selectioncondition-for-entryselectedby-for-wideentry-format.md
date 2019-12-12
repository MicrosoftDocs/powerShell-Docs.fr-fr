---
title: PropertyName, élément de SelectionCondition pour EntrySelectedBy pour WideEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362238"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="708ae-102">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="708ae-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="708ae-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="708ae-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="708ae-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="708ae-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="708ae-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) SelectionCondition, élément pour EntrySelectedBy pour WideEntry (format) PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="708ae-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="708ae-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="708ae-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="708ae-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="708ae-107">Attributes and Elements</span></span>

<span data-ttu-id="708ae-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="708ae-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="708ae-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="708ae-109">Attributes</span></span>

<span data-ttu-id="708ae-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="708ae-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="708ae-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="708ae-111">Child Elements</span></span>

<span data-ttu-id="708ae-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="708ae-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="708ae-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="708ae-113">Parent Elements</span></span>

|<span data-ttu-id="708ae-114">Élément</span><span class="sxs-lookup"><span data-stu-id="708ae-114">Element</span></span>|<span data-ttu-id="708ae-115">Description</span><span class="sxs-lookup"><span data-stu-id="708ae-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="708ae-116">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="708ae-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="708ae-117">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="708ae-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="708ae-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="708ae-118">Text Value</span></span>

<span data-ttu-id="708ae-119">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="708ae-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="708ae-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="708ae-120">Remarks</span></span>

<span data-ttu-id="708ae-121">La condition de sélection doit spécifier au moins un nom de propriété ou un script à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="708ae-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="708ae-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="708ae-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="708ae-123">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="708ae-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="708ae-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="708ae-124">See Also</span></span>

[<span data-ttu-id="708ae-125">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="708ae-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="708ae-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="708ae-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="708ae-127">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="708ae-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="708ae-128">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="708ae-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="708ae-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="708ae-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
