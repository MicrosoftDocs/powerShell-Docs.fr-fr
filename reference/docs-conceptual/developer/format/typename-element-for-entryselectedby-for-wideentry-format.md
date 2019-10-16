---
title: Élément TypeName pour EntrySelectedBy pour WideEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361618"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="c910a-102">TypeName, élément pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c910a-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="c910a-103">Spécifie un type .NET pour la définition.</span><span class="sxs-lookup"><span data-stu-id="c910a-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="c910a-104">La définition est utilisée chaque fois que cet objet est affiché.</span><span class="sxs-lookup"><span data-stu-id="c910a-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="c910a-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément TypeName pour WideEntry ( Format</span><span class="sxs-lookup"><span data-stu-id="c910a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c910a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c910a-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c910a-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="c910a-107">Attributes and Elements</span></span>

<span data-ttu-id="c910a-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="c910a-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c910a-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="c910a-109">Attributes</span></span>

<span data-ttu-id="c910a-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c910a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c910a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c910a-111">Child Elements</span></span>

<span data-ttu-id="c910a-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c910a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c910a-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c910a-113">Parent Elements</span></span>

|<span data-ttu-id="c910a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c910a-114">Element</span></span>|<span data-ttu-id="c910a-115">Description</span><span class="sxs-lookup"><span data-stu-id="c910a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c910a-116">Élément EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c910a-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="c910a-117">Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="c910a-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c910a-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="c910a-118">Text Value</span></span>

<span data-ttu-id="c910a-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="c910a-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c910a-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="c910a-120">Remarks</span></span>

<span data-ttu-id="c910a-121">Chaque entrée à grande largeur doit spécifier un ou plusieurs types .NET, un jeu de sélection ou la condition de sélection qui doit exister pour la définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c910a-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="c910a-122">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="c910a-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c910a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c910a-123">See Also</span></span>

[<span data-ttu-id="c910a-124">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="c910a-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c910a-125">Élément EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c910a-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="c910a-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c910a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
