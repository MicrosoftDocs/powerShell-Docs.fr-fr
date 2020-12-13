---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour EntrySelectedBy pour ListControl (Format)
description: TypeName, élément pour EntrySelectedBy pour ListControl (Format)
ms.openlocfilehash: 6fc5a2385fde3140abbc984e3da6a4dda483b2a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645659"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="828e0-103">TypeName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="828e0-103">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="828e0-104">Spécifie un type .NET qui utilise cette entrée de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="828e0-104">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="828e0-105">Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="828e0-105">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="828e0-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément TypeName pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="828e0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="828e0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="828e0-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="828e0-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="828e0-108">Attributes and Elements</span></span>

<span data-ttu-id="828e0-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="828e0-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="828e0-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="828e0-110">Attributes</span></span>

<span data-ttu-id="828e0-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="828e0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="828e0-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="828e0-112">Child Elements</span></span>

<span data-ttu-id="828e0-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="828e0-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="828e0-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="828e0-114">Parent Elements</span></span>

|<span data-ttu-id="828e0-115">Élément</span><span class="sxs-lookup"><span data-stu-id="828e0-115">Element</span></span>|<span data-ttu-id="828e0-116">Description</span><span class="sxs-lookup"><span data-stu-id="828e0-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="828e0-117">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="828e0-117">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="828e0-118">Définit les types .NET qui utilisent cette entrée de liste ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="828e0-118">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="828e0-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="828e0-119">Text Value</span></span>

<span data-ttu-id="828e0-120">Spécifiez le nom complet du type .NET, tel que `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="828e0-120">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="828e0-121">Notes</span><span class="sxs-lookup"><span data-stu-id="828e0-121">Remarks</span></span>

<span data-ttu-id="828e0-122">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="828e0-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="828e0-123">Pour plus d’informations sur l’utilisation de cet élément dans un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="828e0-123">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="828e0-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="828e0-124">Example</span></span>

<span data-ttu-id="828e0-125">L’exemple suivant montre comment spécifier un jeu de sélection pour une entrée d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="828e0-125">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="828e0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="828e0-126">See Also</span></span>

[<span data-ttu-id="828e0-127">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="828e0-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="828e0-128">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="828e0-128">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="828e0-129">Élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="828e0-129">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="828e0-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="828e0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
