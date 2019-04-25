---
title: Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083805"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="e7de9-102">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e7de9-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="e7de9-103">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e7de9-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="e7de9-104">Lorsque ce type est présent, la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e7de9-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="e7de9-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément pour l’élément de SelectionCondition WideEntry (Format) pour EntrySelectedBy d’élément de TypeName WideEntry (Format) pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e7de9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e7de9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7de9-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e7de9-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e7de9-107">Attributes and Elements</span></span>

<span data-ttu-id="e7de9-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="e7de9-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e7de9-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e7de9-109">Attributes</span></span>

<span data-ttu-id="e7de9-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e7de9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e7de9-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e7de9-111">Child Elements</span></span>

<span data-ttu-id="e7de9-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e7de9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e7de9-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e7de9-113">Parent Elements</span></span>

|<span data-ttu-id="e7de9-114">Élément</span><span class="sxs-lookup"><span data-stu-id="e7de9-114">Element</span></span>|<span data-ttu-id="e7de9-115">Description</span><span class="sxs-lookup"><span data-stu-id="e7de9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e7de9-116">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e7de9-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="e7de9-117">Définit la condition qui doit exister pour cette entrée de large à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e7de9-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e7de9-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="e7de9-118">Text Value</span></span>

<span data-ttu-id="e7de9-119">Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="e7de9-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7de9-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="e7de9-120">Remarks</span></span>

<span data-ttu-id="e7de9-121">La condition de sélection peut spécifier un type .NET ou une sélection définie, mais ne peut pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="e7de9-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="e7de9-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e7de9-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e7de9-123">Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e7de9-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e7de9-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7de9-124">See Also</span></span>

[<span data-ttu-id="e7de9-125">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="e7de9-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e7de9-126">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="e7de9-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e7de9-127">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e7de9-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e7de9-128">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e7de9-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="e7de9-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7de9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
