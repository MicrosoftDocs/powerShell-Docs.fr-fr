---
title: Élément ScriptBlock pour ItemSelectionCondition pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362098"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="8d8ac-102">ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8d8ac-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="8d8ac-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="8d8ac-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="8d8ac-104">Lorsque ce script est évalué à `true`, la condition est remplie et l’élément de liste est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8d8ac-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="8d8ac-105">Cet élément est utilisé lors de la définition d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="8d8ac-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="8d8ac-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) ListItems, élément de ListEntry pour l’élément ListControl (format) ListItem pour ListItems pour le contrôle List (format), élément ItemSelectionCondition pour ListItem pour ListControl (format) ScriptBlock, élément pour ItemSelectionCondition pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8d8ac-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8d8ac-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d8ac-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8d8ac-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="8d8ac-108">Attributes and Elements</span></span>

<span data-ttu-id="8d8ac-109">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="8d8ac-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8d8ac-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="8d8ac-110">Attributes</span></span>

<span data-ttu-id="8d8ac-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="8d8ac-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8d8ac-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8d8ac-112">Child Elements</span></span>

<span data-ttu-id="8d8ac-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="8d8ac-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8d8ac-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8d8ac-114">Parent Elements</span></span>

|<span data-ttu-id="8d8ac-115">Élément</span><span class="sxs-lookup"><span data-stu-id="8d8ac-115">Element</span></span>|<span data-ttu-id="8d8ac-116">Description</span><span class="sxs-lookup"><span data-stu-id="8d8ac-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8d8ac-117">Élément ItemSelectionCondition pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8d8ac-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="8d8ac-118">Définit la condition qui doit exister pour l’élément de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8d8ac-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8d8ac-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="8d8ac-119">Text Value</span></span>

<span data-ttu-id="8d8ac-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="8d8ac-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d8ac-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="8d8ac-121">Remarks</span></span>

<span data-ttu-id="8d8ac-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément `PropertyName` lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="8d8ac-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d8ac-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d8ac-123">See Also</span></span>

[<span data-ttu-id="8d8ac-124">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d8ac-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)