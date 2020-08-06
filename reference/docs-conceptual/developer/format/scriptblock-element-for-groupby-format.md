---
title: Élément ScriptBlock pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e761e02a7910cd598449d564e827889162da9f25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787680"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="c1ebc-102">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c1ebc-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="c1ebc-103">Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="c1ebc-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="c1ebc-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément d’affichage (format) ScriptBlock pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c1ebc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1ebc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1ebc-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1ebc-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c1ebc-106">Attributes and Elements</span></span>

<span data-ttu-id="c1ebc-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="c1ebc-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1ebc-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="c1ebc-108">Attributes</span></span>

<span data-ttu-id="c1ebc-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c1ebc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1ebc-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c1ebc-110">Child Elements</span></span>

<span data-ttu-id="c1ebc-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c1ebc-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1ebc-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c1ebc-112">Parent Elements</span></span>

|<span data-ttu-id="c1ebc-113">Élément</span><span class="sxs-lookup"><span data-stu-id="c1ebc-113">Element</span></span>|<span data-ttu-id="c1ebc-114">Description</span><span class="sxs-lookup"><span data-stu-id="c1ebc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1ebc-115">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c1ebc-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="c1ebc-116">Définit le mode d’affichage d’un groupe d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="c1ebc-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c1ebc-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="c1ebc-117">Text Value</span></span>

<span data-ttu-id="c1ebc-118">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="c1ebc-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1ebc-119">Notes</span><span class="sxs-lookup"><span data-stu-id="c1ebc-119">Remarks</span></span>

<span data-ttu-id="c1ebc-120">PowerShell démarre un nouveau groupe chaque fois que la valeur de ce script change.</span><span class="sxs-lookup"><span data-stu-id="c1ebc-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="c1ebc-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [PropertyName](propertyname-element-for-groupby-format.md) pour démarrer un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="c1ebc-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1ebc-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1ebc-122">See Also</span></span>

[<span data-ttu-id="c1ebc-123">PropertyName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c1ebc-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="c1ebc-124">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c1ebc-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="c1ebc-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1ebc-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
