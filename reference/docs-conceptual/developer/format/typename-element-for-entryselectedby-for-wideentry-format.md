---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour EntrySelectedBy pour WideEntry (Format)
description: TypeName, élément pour EntrySelectedBy pour WideEntry (Format)
ms.openlocfilehash: 2e0facd6ff7c6fec96dabf488449a8502429bcff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654786"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="9873e-103">TypeName, élément pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9873e-103">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="9873e-104">Spécifie un type .NET pour la définition.</span><span class="sxs-lookup"><span data-stu-id="9873e-104">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="9873e-105">La définition est utilisée chaque fois que cet objet est affiché.</span><span class="sxs-lookup"><span data-stu-id="9873e-105">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="9873e-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément TypeName pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9873e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9873e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9873e-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9873e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9873e-108">Attributes and Elements</span></span>

<span data-ttu-id="9873e-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="9873e-109">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9873e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="9873e-110">Attributes</span></span>

<span data-ttu-id="9873e-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9873e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9873e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9873e-112">Child Elements</span></span>

<span data-ttu-id="9873e-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9873e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9873e-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9873e-114">Parent Elements</span></span>

|<span data-ttu-id="9873e-115">Élément</span><span class="sxs-lookup"><span data-stu-id="9873e-115">Element</span></span>|<span data-ttu-id="9873e-116">Description</span><span class="sxs-lookup"><span data-stu-id="9873e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9873e-117">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9873e-117">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="9873e-118">Définit les types .NET qui utilisent cette entrée étendue ou la condition qui doit exister pour que cette entrée soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="9873e-118">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9873e-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="9873e-119">Text Value</span></span>

<span data-ttu-id="9873e-120">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="9873e-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9873e-121">Notes</span><span class="sxs-lookup"><span data-stu-id="9873e-121">Remarks</span></span>

<span data-ttu-id="9873e-122">Chaque entrée à grande largeur doit spécifier un ou plusieurs types .NET, un jeu de sélection ou la condition de sélection qui doit exister pour la définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="9873e-122">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="9873e-123">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9873e-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9873e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9873e-124">See Also</span></span>

[<span data-ttu-id="9873e-125">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="9873e-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9873e-126">EntrySelectedBy, élément pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9873e-126">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="9873e-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9873e-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
