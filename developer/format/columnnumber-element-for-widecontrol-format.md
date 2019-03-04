---
title: Élément ColumnNumber pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856225"
---
# <a name="columnnumber-element-for-widecontrol-format"></a><span data-ttu-id="a8d41-102">ColumnNumber, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a8d41-102">ColumnNumber Element for WideControl (Format)</span></span>

<span data-ttu-id="a8d41-103">Spécifie le nombre de colonnes affichées dans l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="a8d41-103">Specifies the number of columns displayed in the wide view.</span></span>

<span data-ttu-id="a8d41-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément WideControl (Format) ColumnNumber élément de configuration pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a8d41-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) ColumnNumber Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8d41-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8d41-105">Syntax</span></span>

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a8d41-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="a8d41-106">Attributes and Elements</span></span>

<span data-ttu-id="a8d41-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ColumnNumber` élément.</span><span class="sxs-lookup"><span data-stu-id="a8d41-107">The following sections describe attributes, child elements, and the parent element of the `ColumnNumber` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8d41-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="a8d41-108">Attributes</span></span>

<span data-ttu-id="a8d41-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="a8d41-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a8d41-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a8d41-110">Child Elements</span></span>

<span data-ttu-id="a8d41-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="a8d41-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8d41-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a8d41-112">Parent Elements</span></span>

|<span data-ttu-id="a8d41-113">Élément</span><span class="sxs-lookup"><span data-stu-id="a8d41-113">Element</span></span>|<span data-ttu-id="a8d41-114">Description</span><span class="sxs-lookup"><span data-stu-id="a8d41-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8d41-115">Élément WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a8d41-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="a8d41-116">Définit un (valeur unique) à l’échelle du format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="a8d41-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a8d41-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="a8d41-117">Text Value</span></span>

<span data-ttu-id="a8d41-118">Spécifiez une valeur entière positive.</span><span class="sxs-lookup"><span data-stu-id="a8d41-118">Specify a positive integer value.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8d41-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="a8d41-119">Remarks</span></span>

<span data-ttu-id="a8d41-120">Lorsque vous définissez un affichage plus large, vous pouvez ajouter la `AutoSize` élément ou `ColumnNumber` élément, mais vous ne pouvez pas ajouter à la fois.</span><span class="sxs-lookup"><span data-stu-id="a8d41-120">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` element, but you cannot add both.</span></span>

<span data-ttu-id="a8d41-121">Pour plus d’informations sur les composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a8d41-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="a8d41-122">Pour obtenir un exemple d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="a8d41-122">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8d41-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8d41-123">See Also</span></span>

[<span data-ttu-id="a8d41-124">Élément AutoSize pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a8d41-124">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="a8d41-125">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="a8d41-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a8d41-126">Affichage plus large (Basic)</span><span class="sxs-lookup"><span data-stu-id="a8d41-126">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="a8d41-127">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8d41-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
