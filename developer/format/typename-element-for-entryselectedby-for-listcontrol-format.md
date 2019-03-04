---
title: Élément TypeName pour EntrySelectedBy pour ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856105"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="51709-102">TypeName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="51709-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="51709-103">Spécifie un type .NET qui utilise cette entrée de la liste.</span><span class="sxs-lookup"><span data-stu-id="51709-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="51709-104">Il n’existe aucune limite au nombre de types qui peuvent être spécifiées pour une entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="51709-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="51709-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) d’élément objet ListControl, élément (Format) situés (Format) ListEntry, élément (Format) EntrySelectedBy élément d’élément de TypeName ListEntry (Format) pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="51709-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="51709-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51709-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51709-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="51709-107">Attributes and Elements</span></span>

<span data-ttu-id="51709-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="51709-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="51709-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="51709-109">Attributes</span></span>

<span data-ttu-id="51709-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="51709-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="51709-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="51709-111">Child Elements</span></span>

<span data-ttu-id="51709-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="51709-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="51709-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="51709-113">Parent Elements</span></span>

|<span data-ttu-id="51709-114">Élément</span><span class="sxs-lookup"><span data-stu-id="51709-114">Element</span></span>|<span data-ttu-id="51709-115">Description</span><span class="sxs-lookup"><span data-stu-id="51709-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51709-116">Élément EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="51709-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="51709-117">Définit les types .NET qui utilisent cette entrée de liste ou la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="51709-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="51709-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="51709-118">Text Value</span></span>

<span data-ttu-id="51709-119">Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="51709-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="51709-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="51709-120">Remarks</span></span>

<span data-ttu-id="51709-121">Chaque entrée de liste doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="51709-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="51709-122">Pour plus d’informations sur la façon dont cet élément est utilisé dans une vue de liste, consultez [mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="51709-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="51709-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="51709-123">Example</span></span>

<span data-ttu-id="51709-124">L’exemple suivant montre comment spécifier une jeu de sélection pour une entrée d’une vue liste.</span><span class="sxs-lookup"><span data-stu-id="51709-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="51709-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51709-125">See Also</span></span>

[<span data-ttu-id="51709-126">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="51709-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="51709-127">Élément EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="51709-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="51709-128">Élément SelectionSetName pour EnrtySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="51709-128">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="51709-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="51709-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
