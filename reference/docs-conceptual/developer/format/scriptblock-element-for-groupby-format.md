---
title: Élément ScriptBlock pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364928"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="34f72-102">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34f72-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="34f72-103">Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="34f72-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="34f72-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément d’affichage (format) ScriptBlock pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="34f72-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34f72-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34f72-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34f72-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="34f72-106">Attributes and Elements</span></span>

<span data-ttu-id="34f72-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="34f72-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34f72-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="34f72-108">Attributes</span></span>

<span data-ttu-id="34f72-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="34f72-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34f72-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="34f72-110">Child Elements</span></span>

<span data-ttu-id="34f72-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="34f72-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34f72-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="34f72-112">Parent Elements</span></span>

|<span data-ttu-id="34f72-113">Élément</span><span class="sxs-lookup"><span data-stu-id="34f72-113">Element</span></span>|<span data-ttu-id="34f72-114">Description</span><span class="sxs-lookup"><span data-stu-id="34f72-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34f72-115">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="34f72-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="34f72-116">Définit le mode d’affichage d’un groupe d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="34f72-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="34f72-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="34f72-117">Text Value</span></span>

<span data-ttu-id="34f72-118">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="34f72-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="34f72-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="34f72-119">Remarks</span></span>

<span data-ttu-id="34f72-120">PowerShell démarre un nouveau groupe chaque fois que la valeur de ce script change.</span><span class="sxs-lookup"><span data-stu-id="34f72-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="34f72-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément [PropertyName](propertyname-element-for-groupby-format.md) pour démarrer un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="34f72-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="34f72-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34f72-122">See Also</span></span>

[<span data-ttu-id="34f72-123">PropertyName, élément de GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="34f72-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="34f72-124">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="34f72-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="34f72-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="34f72-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
