---
title: Élément EnumerableExpansions (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066088"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="1954b-102">EnumerableExpansions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="1954b-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="1954b-103">Définit comment les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="1954b-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="1954b-104">Configuration élément (Format) DefaultSettings (Format) EnumerableExpansions élément (Format)</span><span class="sxs-lookup"><span data-stu-id="1954b-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1954b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1954b-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1954b-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="1954b-106">Attributes and Elements</span></span>

<span data-ttu-id="1954b-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EnumerableExpansions` élément.</span><span class="sxs-lookup"><span data-stu-id="1954b-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="1954b-108">Il n’existe aucune limite au nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="1954b-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="1954b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="1954b-109">Attributes</span></span>

<span data-ttu-id="1954b-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="1954b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1954b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1954b-111">Child Elements</span></span>

|<span data-ttu-id="1954b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="1954b-112">Element</span></span>|<span data-ttu-id="1954b-113">Description</span><span class="sxs-lookup"><span data-stu-id="1954b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1954b-114">Élément EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="1954b-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="1954b-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="1954b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1954b-116">Définit les objets de collection .NET spécifiques qui sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="1954b-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1954b-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1954b-117">Parent Elements</span></span>

|<span data-ttu-id="1954b-118">Élément</span><span class="sxs-lookup"><span data-stu-id="1954b-118">Element</span></span>|<span data-ttu-id="1954b-119">Description</span><span class="sxs-lookup"><span data-stu-id="1954b-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1954b-120">Élément DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="1954b-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="1954b-121">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="1954b-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1954b-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="1954b-122">Remarks</span></span>

<span data-ttu-id="1954b-123">Cet élément est utilisé pour définir l’affichent des objets de collection et les objets dans la collection.</span><span class="sxs-lookup"><span data-stu-id="1954b-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="1954b-124">Dans ce cas, un objet de collection fait référence à n’importe quel objet qui prend en charge la **System.Collections.ICollection** interface.</span><span class="sxs-lookup"><span data-stu-id="1954b-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="1954b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1954b-125">See Also</span></span>

[<span data-ttu-id="1954b-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1954b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
