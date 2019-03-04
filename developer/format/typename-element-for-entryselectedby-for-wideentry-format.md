---
title: Élément TypeName pour EntrySelectedBy pour WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862645"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="d16f0-102">TypeName, élément pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d16f0-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="d16f0-103">Spécifie un type .NET pour la définition.</span><span class="sxs-lookup"><span data-stu-id="d16f0-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="d16f0-104">La définition est utilisée chaque fois que cet objet s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d16f0-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="d16f0-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément WideControl (Format) élément WideEntries (Format) WideEntry, élément (Format) EntrySelectedBy élément de configuration pour WideEntry (Format), élément TypeName pour WideEntry ( Format)</span><span class="sxs-lookup"><span data-stu-id="d16f0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d16f0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d16f0-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d16f0-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d16f0-107">Attributes and Elements</span></span>

<span data-ttu-id="d16f0-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="d16f0-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d16f0-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d16f0-109">Attributes</span></span>

<span data-ttu-id="d16f0-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d16f0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d16f0-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d16f0-111">Child Elements</span></span>

<span data-ttu-id="d16f0-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d16f0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d16f0-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d16f0-113">Parent Elements</span></span>

|<span data-ttu-id="d16f0-114">Élément</span><span class="sxs-lookup"><span data-stu-id="d16f0-114">Element</span></span>|<span data-ttu-id="d16f0-115">Description</span><span class="sxs-lookup"><span data-stu-id="d16f0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d16f0-116">Élément EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d16f0-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="d16f0-117">Définit les types .NET qui utilisent cette entrée large ou la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d16f0-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d16f0-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="d16f0-118">Text Value</span></span>

<span data-ttu-id="d16f0-119">Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="d16f0-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d16f0-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="d16f0-120">Remarks</span></span>

<span data-ttu-id="d16f0-121">Chaque entrée large doit spécifier un ou plusieurs types .NET, un jeu de sélection ou la condition de sélection doit exister pour la définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d16f0-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="d16f0-122">Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d16f0-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d16f0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d16f0-123">See Also</span></span>

[<span data-ttu-id="d16f0-124">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="d16f0-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d16f0-125">Élément EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d16f0-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="d16f0-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d16f0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
