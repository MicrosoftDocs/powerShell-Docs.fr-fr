---
title: Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368058"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="b74f2-102">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b74f2-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="b74f2-103">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="b74f2-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="b74f2-104">Lorsque ce type est présent, la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b74f2-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="b74f2-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) SelectionCondition, élément pour EntrySelectedBy pour l’élément WideEntry (format) TypeName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="b74f2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b74f2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b74f2-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b74f2-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="b74f2-107">Attributes and Elements</span></span>

<span data-ttu-id="b74f2-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="b74f2-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b74f2-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="b74f2-109">Attributes</span></span>

<span data-ttu-id="b74f2-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b74f2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b74f2-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b74f2-111">Child Elements</span></span>

<span data-ttu-id="b74f2-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b74f2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b74f2-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b74f2-113">Parent Elements</span></span>

|<span data-ttu-id="b74f2-114">Élément</span><span class="sxs-lookup"><span data-stu-id="b74f2-114">Element</span></span>|<span data-ttu-id="b74f2-115">Description</span><span class="sxs-lookup"><span data-stu-id="b74f2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b74f2-116">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="b74f2-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="b74f2-117">Définit la condition qui doit exister pour cette grande entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b74f2-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b74f2-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="b74f2-118">Text Value</span></span>

<span data-ttu-id="b74f2-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="b74f2-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b74f2-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="b74f2-120">Remarks</span></span>

<span data-ttu-id="b74f2-121">La condition de sélection peut spécifier un type .NET ou un jeu de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="b74f2-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="b74f2-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b74f2-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b74f2-123">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b74f2-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b74f2-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b74f2-124">See Also</span></span>

[<span data-ttu-id="b74f2-125">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="b74f2-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b74f2-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="b74f2-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b74f2-127">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="b74f2-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="b74f2-128">Élément SelectionSetName pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="b74f2-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="b74f2-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b74f2-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
