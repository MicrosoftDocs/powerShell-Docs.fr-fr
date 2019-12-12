---
title: Élément TypeName pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361658"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="ac806-102">TypeName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ac806-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="ac806-103">Spécifie un type .NET qui utilise cette entrée de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="ac806-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="ac806-104">Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="ac806-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="ac806-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour l’élément ListEntry (format) TypeName pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="ac806-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac806-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac806-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac806-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ac806-107">Attributes and Elements</span></span>

<span data-ttu-id="ac806-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="ac806-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac806-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="ac806-109">Attributes</span></span>

<span data-ttu-id="ac806-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ac806-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac806-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ac806-111">Child Elements</span></span>

<span data-ttu-id="ac806-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ac806-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac806-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ac806-113">Parent Elements</span></span>

|<span data-ttu-id="ac806-114">Élément</span><span class="sxs-lookup"><span data-stu-id="ac806-114">Element</span></span>|<span data-ttu-id="ac806-115">Description</span><span class="sxs-lookup"><span data-stu-id="ac806-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac806-116">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ac806-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="ac806-117">Définit les types .NET qui utilisent cette entrée de liste ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="ac806-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ac806-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="ac806-118">Text Value</span></span>

<span data-ttu-id="ac806-119">Spécifiez le nom complet du type .NET, par exemple `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="ac806-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac806-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="ac806-120">Remarks</span></span>

<span data-ttu-id="ac806-121">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="ac806-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ac806-122">Pour plus d’informations sur l’utilisation de cet élément dans un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="ac806-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ac806-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac806-123">Example</span></span>

<span data-ttu-id="ac806-124">L’exemple suivant montre comment spécifier un jeu de sélection pour une entrée d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="ac806-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="ac806-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac806-125">See Also</span></span>

[<span data-ttu-id="ac806-126">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="ac806-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ac806-127">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ac806-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="ac806-128">Élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ac806-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="ac806-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac806-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
