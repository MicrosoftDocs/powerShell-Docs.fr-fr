---
title: Élément TypeName pour EntrySelectedBy pour WideEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9af443067467f590df824b28636f57b807a4fc94
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780183"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="a81d7-102">TypeName, élément pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a81d7-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="a81d7-103">Spécifie un type .NET pour la définition.</span><span class="sxs-lookup"><span data-stu-id="a81d7-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="a81d7-104">La définition est utilisée chaque fois que cet objet est affiché.</span><span class="sxs-lookup"><span data-stu-id="a81d7-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="a81d7-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément TypeName pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a81d7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a81d7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a81d7-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a81d7-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a81d7-107">Attributes and Elements</span></span>

<span data-ttu-id="a81d7-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="a81d7-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a81d7-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="a81d7-109">Attributes</span></span>

<span data-ttu-id="a81d7-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a81d7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a81d7-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a81d7-111">Child Elements</span></span>

<span data-ttu-id="a81d7-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a81d7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a81d7-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a81d7-113">Parent Elements</span></span>

|<span data-ttu-id="a81d7-114">Élément</span><span class="sxs-lookup"><span data-stu-id="a81d7-114">Element</span></span>|<span data-ttu-id="a81d7-115">Description</span><span class="sxs-lookup"><span data-stu-id="a81d7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a81d7-116">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a81d7-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="a81d7-117">Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a81d7-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a81d7-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="a81d7-118">Text Value</span></span>

<span data-ttu-id="a81d7-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="a81d7-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a81d7-120">Notes</span><span class="sxs-lookup"><span data-stu-id="a81d7-120">Remarks</span></span>

<span data-ttu-id="a81d7-121">Chaque entrée à grande largeur doit spécifier un ou plusieurs types .NET, un jeu de sélection ou la condition de sélection qui doit exister pour la définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a81d7-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="a81d7-122">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a81d7-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a81d7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a81d7-123">See Also</span></span>

[<span data-ttu-id="a81d7-124">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="a81d7-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a81d7-125">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a81d7-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="a81d7-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a81d7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
