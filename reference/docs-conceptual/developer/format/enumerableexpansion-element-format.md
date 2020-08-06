---
title: Élément EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 81a8959c19502a2e56f4cfa48a1e480509d84b6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774046"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="a7110-102">EnumerableExpansion, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a7110-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="a7110-103">Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="a7110-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="a7110-104">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) EnumerableExpansion, élément (format)</span><span class="sxs-lookup"><span data-stu-id="a7110-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a7110-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7110-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7110-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a7110-106">Attributes and Elements</span></span>

<span data-ttu-id="a7110-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EnumerableExpansion` élément.</span><span class="sxs-lookup"><span data-stu-id="a7110-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a7110-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="a7110-108">Attributes</span></span>

<span data-ttu-id="a7110-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a7110-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a7110-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a7110-110">Child Elements</span></span>

|<span data-ttu-id="a7110-111">Élément</span><span class="sxs-lookup"><span data-stu-id="a7110-111">Element</span></span>|<span data-ttu-id="a7110-112">Description</span><span class="sxs-lookup"><span data-stu-id="a7110-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7110-113">EntrySelectedBy, élément pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="a7110-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="a7110-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a7110-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a7110-115">Définit les objets de collection .NET développés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="a7110-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="a7110-116">Expand, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a7110-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="a7110-117">Spécifie comment l’objet de collection est développé pour cette définition.</span><span class="sxs-lookup"><span data-stu-id="a7110-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a7110-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a7110-118">Parent Elements</span></span>

|<span data-ttu-id="a7110-119">Élément</span><span class="sxs-lookup"><span data-stu-id="a7110-119">Element</span></span>|<span data-ttu-id="a7110-120">Description</span><span class="sxs-lookup"><span data-stu-id="a7110-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7110-121">EnumerableExpansions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a7110-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="a7110-122">Définit les différentes façons dont les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="a7110-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a7110-123">Notes</span><span class="sxs-lookup"><span data-stu-id="a7110-123">Remarks</span></span>

<span data-ttu-id="a7110-124">Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="a7110-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="a7110-125">Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="a7110-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="a7110-126">Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="a7110-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7110-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7110-127">See Also</span></span>

[<span data-ttu-id="a7110-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7110-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
