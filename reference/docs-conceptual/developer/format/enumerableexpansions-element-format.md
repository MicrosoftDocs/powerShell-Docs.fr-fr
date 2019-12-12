---
title: Élément EnumerableExpansions (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363298"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="35d08-102">EnumerableExpansions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="35d08-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="35d08-103">Définit la façon dont les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="35d08-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="35d08-104">Élément de configuration (format) DefaultSettings, élément (format) EnumerableExpansions, élément (format)</span><span class="sxs-lookup"><span data-stu-id="35d08-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="35d08-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35d08-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="35d08-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="35d08-106">Attributes and Elements</span></span>

<span data-ttu-id="35d08-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EnumerableExpansions`.</span><span class="sxs-lookup"><span data-stu-id="35d08-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="35d08-108">Il n’existe aucune limite quant au nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="35d08-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="35d08-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="35d08-109">Attributes</span></span>

<span data-ttu-id="35d08-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="35d08-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="35d08-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="35d08-111">Child Elements</span></span>

|<span data-ttu-id="35d08-112">Élément</span><span class="sxs-lookup"><span data-stu-id="35d08-112">Element</span></span>|<span data-ttu-id="35d08-113">Description</span><span class="sxs-lookup"><span data-stu-id="35d08-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="35d08-114">Élément EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="35d08-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="35d08-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="35d08-115">Optional element.</span></span><br /><br /> <span data-ttu-id="35d08-116">Définit les objets de collection .NET spécifiques qui sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="35d08-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="35d08-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="35d08-117">Parent Elements</span></span>

|<span data-ttu-id="35d08-118">Élément</span><span class="sxs-lookup"><span data-stu-id="35d08-118">Element</span></span>|<span data-ttu-id="35d08-119">Description</span><span class="sxs-lookup"><span data-stu-id="35d08-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="35d08-120">Élément DefaultSettings (format)</span><span class="sxs-lookup"><span data-stu-id="35d08-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="35d08-121">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="35d08-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="35d08-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="35d08-122">Remarks</span></span>

<span data-ttu-id="35d08-123">Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="35d08-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="35d08-124">Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="35d08-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="35d08-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35d08-125">See Also</span></span>

[<span data-ttu-id="35d08-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="35d08-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
