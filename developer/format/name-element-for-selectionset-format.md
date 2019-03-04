---
title: Nom d’élément pour SelectionSet (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858165"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="63728-102">Name, élément pour SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="63728-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="63728-103">Spécifie le nom utilisé pour référencer le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="63728-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="63728-104">Configuration (Format) élément SelectionSets (Format) élément SelectionSet (Format) nom Element du SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="63728-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63728-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63728-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63728-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="63728-106">Attributes and Elements</span></span>

<span data-ttu-id="63728-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `Name` élément.</span><span class="sxs-lookup"><span data-stu-id="63728-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="63728-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="63728-108">Attributes</span></span>

<span data-ttu-id="63728-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="63728-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63728-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="63728-110">Child Elements</span></span>

<span data-ttu-id="63728-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="63728-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="63728-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="63728-112">Parent Elements</span></span>

|<span data-ttu-id="63728-113">Élément</span><span class="sxs-lookup"><span data-stu-id="63728-113">Element</span></span>|<span data-ttu-id="63728-114">Description</span><span class="sxs-lookup"><span data-stu-id="63728-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63728-115">Élément SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="63728-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="63728-116">Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="63728-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="63728-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="63728-117">Text Value</span></span>

<span data-ttu-id="63728-118">Spécifiez le nom pour faire référence à l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="63728-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="63728-119">Il existe aucune restriction concernant les caractères ne peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="63728-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="63728-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="63728-120">Remarks</span></span>

<span data-ttu-id="63728-121">Le nom spécifié ici est utilisé dans le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="63728-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="63728-122">Le jeu de sélection qui peut être utilisé par une vue, en une définition d’une vue (vues peuvent avoir plusieurs définitions), ou lorsque vous spécifiez une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="63728-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="63728-123">Pour plus d’informations sur les jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="63728-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="63728-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="63728-124">Example</span></span>

<span data-ttu-id="63728-125">Cet exemple montre un `SelectionSet` élément qui définit les quatre types de .NET.</span><span class="sxs-lookup"><span data-stu-id="63728-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="63728-126">Le nom de l’ensemble de la sélection est « FileSystemTypes ».</span><span class="sxs-lookup"><span data-stu-id="63728-126">The name of the selection set is "FileSystemTypes".</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="63728-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63728-127">See Also</span></span>

[<span data-ttu-id="63728-128">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="63728-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="63728-129">Élément SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="63728-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="63728-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="63728-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
