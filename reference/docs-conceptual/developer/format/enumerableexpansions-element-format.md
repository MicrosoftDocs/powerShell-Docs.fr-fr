---
title: Élément EnumerableExpansions (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2b536b1ab9b34b0089d0a38d3c5dc7a937176443
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774012"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="eddbc-102">EnumerableExpansions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="eddbc-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="eddbc-103">Définit la façon dont les objets de collection .NET sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="eddbc-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="eddbc-104">Élément de configuration (format) DefaultSettings, élément (format) EnumerableExpansions, élément (format)</span><span class="sxs-lookup"><span data-stu-id="eddbc-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eddbc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eddbc-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eddbc-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="eddbc-106">Attributes and Elements</span></span>

<span data-ttu-id="eddbc-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EnumerableExpansions` élément.</span><span class="sxs-lookup"><span data-stu-id="eddbc-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="eddbc-108">Il n’existe aucune limite quant au nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="eddbc-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="eddbc-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="eddbc-109">Attributes</span></span>

<span data-ttu-id="eddbc-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="eddbc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eddbc-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eddbc-111">Child Elements</span></span>

|<span data-ttu-id="eddbc-112">Élément</span><span class="sxs-lookup"><span data-stu-id="eddbc-112">Element</span></span>|<span data-ttu-id="eddbc-113">Description</span><span class="sxs-lookup"><span data-stu-id="eddbc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eddbc-114">EnumerableExpansion, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="eddbc-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="eddbc-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="eddbc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="eddbc-116">Définit les objets de collection .NET spécifiques qui sont développés lorsqu’ils sont affichés dans une vue.</span><span class="sxs-lookup"><span data-stu-id="eddbc-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="eddbc-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eddbc-117">Parent Elements</span></span>

|<span data-ttu-id="eddbc-118">Élément</span><span class="sxs-lookup"><span data-stu-id="eddbc-118">Element</span></span>|<span data-ttu-id="eddbc-119">Description</span><span class="sxs-lookup"><span data-stu-id="eddbc-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eddbc-120">DefaultSettings, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="eddbc-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="eddbc-121">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="eddbc-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eddbc-122">Notes</span><span class="sxs-lookup"><span data-stu-id="eddbc-122">Remarks</span></span>

<span data-ttu-id="eddbc-123">Cet élément est utilisé pour définir le mode d’affichage des objets de collection et des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="eddbc-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="eddbc-124">Dans ce cas, un objet de collection fait référence à tout objet qui prend en charge l’interface **System. Collections. ICollection** .</span><span class="sxs-lookup"><span data-stu-id="eddbc-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="eddbc-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eddbc-125">See Also</span></span>

[<span data-ttu-id="eddbc-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="eddbc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
