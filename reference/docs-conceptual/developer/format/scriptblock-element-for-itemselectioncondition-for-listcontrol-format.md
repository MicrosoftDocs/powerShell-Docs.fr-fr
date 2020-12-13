---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)
description: ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)
ms.openlocfilehash: 1e518f898e0e1e62ca64f9897b1323cc6dd89ae9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665064"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="984f5-103">ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="984f5-103">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="984f5-104">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="984f5-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="984f5-105">Lorsque ce script est évalué à `true` , la condition est remplie et l’élément de liste est utilisé.</span><span class="sxs-lookup"><span data-stu-id="984f5-105">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="984f5-106">Cet élément est utilisé lors de la définition d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="984f5-106">This element is used when defining a list view.</span></span>

<span data-ttu-id="984f5-107">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) élément ListEntry pour ListEntries pour ListControl (format) ListItems, élément de l’élément ItemSelectionCondition de l’élément ListControl pour ListControl (format) pour l’élément ListItems pour le contrôle List (format)</span><span class="sxs-lookup"><span data-stu-id="984f5-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="984f5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="984f5-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="984f5-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="984f5-109">Attributes and Elements</span></span>

<span data-ttu-id="984f5-110">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="984f5-110">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="984f5-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="984f5-111">Attributes</span></span>

<span data-ttu-id="984f5-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="984f5-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="984f5-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="984f5-113">Child Elements</span></span>

<span data-ttu-id="984f5-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="984f5-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="984f5-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="984f5-115">Parent Elements</span></span>

|<span data-ttu-id="984f5-116">Élément</span><span class="sxs-lookup"><span data-stu-id="984f5-116">Element</span></span>|<span data-ttu-id="984f5-117">Description</span><span class="sxs-lookup"><span data-stu-id="984f5-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="984f5-118">ItemSelectionCondition, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="984f5-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="984f5-119">Définit la condition qui doit exister pour l’élément de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="984f5-119">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="984f5-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="984f5-120">Text Value</span></span>

<span data-ttu-id="984f5-121">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="984f5-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="984f5-122">Notes</span><span class="sxs-lookup"><span data-stu-id="984f5-122">Remarks</span></span>

<span data-ttu-id="984f5-123">Si cet élément est utilisé, vous ne pouvez pas spécifier l' `PropertyName` élément lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="984f5-123">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="984f5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="984f5-124">See Also</span></span>

[<span data-ttu-id="984f5-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="984f5-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
