---
title: Élément TypeName pour SelectionCondition pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361558"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="e000d-102">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e000d-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="e000d-103">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e000d-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="e000d-104">Lorsque ce type est présent, l’entrée de liste est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e000d-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="e000d-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) EntrySelectedBy, élément de ListEntry pour ListControl (format) élément SelectionCondition pour l’élément EntrySelectedBy pour ListControl (format) TypeName pour SelectionCondition pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="e000d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e000d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e000d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e000d-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e000d-107">Attributes and Elements</span></span>

<span data-ttu-id="e000d-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="e000d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e000d-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="e000d-109">Attributes</span></span>

<span data-ttu-id="e000d-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e000d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e000d-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e000d-111">Child Elements</span></span>

<span data-ttu-id="e000d-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e000d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e000d-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e000d-113">Parent Elements</span></span>

|<span data-ttu-id="e000d-114">Élément</span><span class="sxs-lookup"><span data-stu-id="e000d-114">Element</span></span>|<span data-ttu-id="e000d-115">Description</span><span class="sxs-lookup"><span data-stu-id="e000d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e000d-116">Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="e000d-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e000d-117">Définit la condition qui doit exister pour que cette entrée de liste soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="e000d-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e000d-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="e000d-118">Text Value</span></span>

<span data-ttu-id="e000d-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="e000d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e000d-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="e000d-120">Remarks</span></span>

<span data-ttu-id="e000d-121">La condition de sélection peut spécifier un nombre quelconque de types .NET ou de jeux de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="e000d-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="e000d-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e000d-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e000d-123">Pour plus d’informations sur les autres composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e000d-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e000d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e000d-124">See Also</span></span>

[<span data-ttu-id="e000d-125">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="e000d-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e000d-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="e000d-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e000d-127">Élément SelectionCondition pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="e000d-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="e000d-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e000d-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
