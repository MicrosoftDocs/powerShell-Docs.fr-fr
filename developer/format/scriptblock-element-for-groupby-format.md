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
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229326"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="71329-102">ScriptBlock, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="71329-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="71329-103">Spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change.</span><span class="sxs-lookup"><span data-stu-id="71329-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="71329-104">Configuration élément (Format) élément ViewDefinitions (Format) élément (Format) GroupBy élément d’affichage pour l’élément ScriptBlock de vue (Format) pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="71329-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="71329-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71329-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="71329-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="71329-106">Attributes and Elements</span></span>

<span data-ttu-id="71329-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="71329-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="71329-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="71329-108">Attributes</span></span>

<span data-ttu-id="71329-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="71329-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="71329-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="71329-110">Child Elements</span></span>

<span data-ttu-id="71329-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="71329-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="71329-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="71329-112">Parent Elements</span></span>

|<span data-ttu-id="71329-113">Élément</span><span class="sxs-lookup"><span data-stu-id="71329-113">Element</span></span>|<span data-ttu-id="71329-114">Description</span><span class="sxs-lookup"><span data-stu-id="71329-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71329-115">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="71329-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="71329-116">Définit la façon dont un groupe d’objets .NET est affiché.</span><span class="sxs-lookup"><span data-stu-id="71329-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="71329-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="71329-117">Text Value</span></span>

<span data-ttu-id="71329-118">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="71329-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="71329-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="71329-119">Remarks</span></span>

<span data-ttu-id="71329-120">PowerShell démarre un nouveau groupe chaque fois que la valeur de ce script change.</span><span class="sxs-lookup"><span data-stu-id="71329-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="71329-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [PropertyName](propertyname-element-for-groupby-format.md) élément pour démarrer un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="71329-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="71329-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71329-122">See Also</span></span>

[<span data-ttu-id="71329-123">Élément PropertyName pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="71329-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="71329-124">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="71329-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="71329-125">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="71329-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
