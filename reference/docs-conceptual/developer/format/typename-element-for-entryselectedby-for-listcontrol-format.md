---
title: Élément TypeName pour EntrySelectedBy pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5e7b73db5aa597d96141454008c5c58b1827df24
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780217"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="9a805-102">TypeName, élément pour EntrySelectedBy pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9a805-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="9a805-103">Spécifie un type .NET qui utilise cette entrée de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="9a805-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="9a805-104">Il n’existe aucune limite au nombre de types pouvant être spécifiés pour une entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="9a805-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="9a805-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément (format) élément EntrySelectedBy pour ListEntry (format) élément TypeName pour EntrySelectedBy pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="9a805-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a805-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a805-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a805-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9a805-107">Attributes and Elements</span></span>

<span data-ttu-id="9a805-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="9a805-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a805-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="9a805-109">Attributes</span></span>

<span data-ttu-id="9a805-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9a805-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a805-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9a805-111">Child Elements</span></span>

<span data-ttu-id="9a805-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9a805-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a805-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9a805-113">Parent Elements</span></span>

|<span data-ttu-id="9a805-114">Élément</span><span class="sxs-lookup"><span data-stu-id="9a805-114">Element</span></span>|<span data-ttu-id="9a805-115">Description</span><span class="sxs-lookup"><span data-stu-id="9a805-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a805-116">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9a805-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="9a805-117">Définit les types .NET qui utilisent cette entrée de liste ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="9a805-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a805-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="9a805-118">Text Value</span></span>

<span data-ttu-id="9a805-119">Spécifiez le nom complet du type .NET, tel que `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="9a805-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a805-120">Notes</span><span class="sxs-lookup"><span data-stu-id="9a805-120">Remarks</span></span>

<span data-ttu-id="9a805-121">Au moins un nom de type, un jeu de sélection ou une condition de sélection doivent être définis pour chaque entrée de liste.</span><span class="sxs-lookup"><span data-stu-id="9a805-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9a805-122">Pour plus d’informations sur l’utilisation de cet élément dans un affichage de liste, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="9a805-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9a805-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="9a805-123">Example</span></span>

<span data-ttu-id="9a805-124">L’exemple suivant montre comment spécifier un jeu de sélection pour une entrée d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="9a805-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="9a805-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a805-125">See Also</span></span>

[<span data-ttu-id="9a805-126">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="9a805-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9a805-127">Élément EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9a805-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="9a805-128">Élément SelectionSetName pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9a805-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="9a805-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a805-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
