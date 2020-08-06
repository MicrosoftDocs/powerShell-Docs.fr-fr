---
title: Expand, élément (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: deee832254bb8a774ee2c1f5bd451d3ced1bd47a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783651"
---
# <a name="expand-element-format"></a><span data-ttu-id="801fc-102">Expand, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="801fc-102">Expand Element (Format)</span></span>

<span data-ttu-id="801fc-103">Spécifie comment l’objet de collection est développé pour cette définition.</span><span class="sxs-lookup"><span data-stu-id="801fc-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="801fc-104">Élément de configuration (format) DefaultSettings, élément (format) élément EnumerableExpansions (format) élément EnumerableExpansion (format) Expand, élément (format)</span><span class="sxs-lookup"><span data-stu-id="801fc-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="801fc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="801fc-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="801fc-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="801fc-106">Attributes and Elements</span></span>

<span data-ttu-id="801fc-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Expand` élément.</span><span class="sxs-lookup"><span data-stu-id="801fc-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="801fc-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="801fc-108">Attributes</span></span>

<span data-ttu-id="801fc-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="801fc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="801fc-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="801fc-110">Child Elements</span></span>

<span data-ttu-id="801fc-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="801fc-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="801fc-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="801fc-112">Parent Elements</span></span>

|<span data-ttu-id="801fc-113">Élément</span><span class="sxs-lookup"><span data-stu-id="801fc-113">Element</span></span>|<span data-ttu-id="801fc-114">Description</span><span class="sxs-lookup"><span data-stu-id="801fc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="801fc-115">EnumerableExpansion, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="801fc-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="801fc-116">Définit la façon dont des objets de collection .NET spécifiques sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="801fc-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="801fc-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="801fc-117">Text Value</span></span>

<span data-ttu-id="801fc-118">Spécifiez l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="801fc-118">Specify one of the following values:</span></span>

- <span data-ttu-id="801fc-119">EnumOnly : affiche uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="801fc-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="801fc-120">CoreOnly : affiche uniquement les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="801fc-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="801fc-121">Both : affiche les propriétés des objets dans la collection et les propriétés de l’objet de collection.</span><span class="sxs-lookup"><span data-stu-id="801fc-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="801fc-122">Notes</span><span class="sxs-lookup"><span data-stu-id="801fc-122">Remarks</span></span>

<span data-ttu-id="801fc-123">Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="801fc-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="801fc-124">Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="801fc-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="801fc-125">Le comportement par défaut consiste à afficher uniquement les propriétés des objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="801fc-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="801fc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="801fc-126">See Also</span></span>

[<span data-ttu-id="801fc-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="801fc-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
