---
title: Élément Name pour SelectionSet (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362668"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="3eea4-102">Name, élément pour SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="3eea4-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="3eea4-103">Spécifie le nom utilisé pour référencer le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="3eea4-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="3eea4-104">Élément de configuration (format) élément SelectionSets (format) élément SelectionSet (format) élément Name de SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="3eea4-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3eea4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3eea4-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3eea4-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="3eea4-106">Attributes and Elements</span></span>

<span data-ttu-id="3eea4-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Name`.</span><span class="sxs-lookup"><span data-stu-id="3eea4-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3eea4-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="3eea4-108">Attributes</span></span>

<span data-ttu-id="3eea4-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3eea4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3eea4-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3eea4-110">Child Elements</span></span>

<span data-ttu-id="3eea4-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3eea4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3eea4-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3eea4-112">Parent Elements</span></span>

|<span data-ttu-id="3eea4-113">Élément</span><span class="sxs-lookup"><span data-stu-id="3eea4-113">Element</span></span>|<span data-ttu-id="3eea4-114">Description</span><span class="sxs-lookup"><span data-stu-id="3eea4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3eea4-115">Élément SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="3eea4-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="3eea4-116">Définit un ensemble unique d’objets .NET qui peuvent être référencés par le nom de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="3eea4-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3eea4-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="3eea4-117">Text Value</span></span>

<span data-ttu-id="3eea4-118">Spécifiez le nom pour faire référence au jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="3eea4-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="3eea4-119">Il n’existe aucune restriction quant aux caractères qui peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="3eea4-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="3eea4-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="3eea4-120">Remarks</span></span>

<span data-ttu-id="3eea4-121">Le nom spécifié ici est utilisé dans l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="3eea4-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="3eea4-122">Jeu de sélection qui peut être utilisé par une vue, par une définition d’une vue (les vues peuvent avoir plusieurs définitions) ou lors de la spécification d’une condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="3eea4-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="3eea4-123">Pour plus d’informations sur les jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3eea4-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="3eea4-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="3eea4-124">Example</span></span>

<span data-ttu-id="3eea4-125">Cet exemple montre un élément `SelectionSet` qui définit quatre types .NET.</span><span class="sxs-lookup"><span data-stu-id="3eea4-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="3eea4-126">Le nom du jeu de sélection est « FileSystemTypes ».</span><span class="sxs-lookup"><span data-stu-id="3eea4-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3eea4-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3eea4-127">See Also</span></span>

[<span data-ttu-id="3eea4-128">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="3eea4-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3eea4-129">Élément SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="3eea4-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="3eea4-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3eea4-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
