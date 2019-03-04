---
title: Élément ScriptBlock pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856205"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="6ba25-102">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6ba25-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="6ba25-103">Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="6ba25-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="6ba25-104">Configuration élément (Format) élément ViewDefinitions (Format) élément (Format) GroupBy élément d’affichage pour l’élément ScriptBlock de vue (Format) pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6ba25-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ba25-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ba25-105">Syntax</span></span>

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ba25-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="6ba25-106">Attributes and Elements</span></span>

<span data-ttu-id="6ba25-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="6ba25-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ba25-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="6ba25-108">Attributes</span></span>

<span data-ttu-id="6ba25-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6ba25-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ba25-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6ba25-110">Child Elements</span></span>

<span data-ttu-id="6ba25-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6ba25-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6ba25-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6ba25-112">Parent Elements</span></span>

|<span data-ttu-id="6ba25-113">Élément</span><span class="sxs-lookup"><span data-stu-id="6ba25-113">Element</span></span>|<span data-ttu-id="6ba25-114">Description</span><span class="sxs-lookup"><span data-stu-id="6ba25-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ba25-115">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="6ba25-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="6ba25-116">Définit la façon dont un groupe d’objets .NET est affiché.</span><span class="sxs-lookup"><span data-stu-id="6ba25-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6ba25-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="6ba25-117">Text Value</span></span>

<span data-ttu-id="6ba25-118">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="6ba25-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ba25-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="6ba25-119">Remarks</span></span>

<span data-ttu-id="6ba25-120">Windows PowerShell démarre un nouveau groupe chaque fois que la valeur de ce script change.</span><span class="sxs-lookup"><span data-stu-id="6ba25-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="6ba25-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) élément pour démarrer un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="6ba25-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ba25-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ba25-122">See Also</span></span>

[<span data-ttu-id="6ba25-123">Élément PropertyName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6ba25-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="6ba25-124">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="6ba25-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="6ba25-125">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ba25-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
