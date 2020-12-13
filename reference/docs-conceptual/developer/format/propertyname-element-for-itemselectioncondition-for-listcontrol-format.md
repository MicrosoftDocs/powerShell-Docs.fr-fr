---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour ItemSelectionCondition pour ListControl (Format)
description: PropertyName, élément pour ItemSelectionCondition pour ListControl (Format)
ms.openlocfilehash: c515efe70afdb1c1186c0a07fe1f52dc49ad57b9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665989"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="37bdc-103">PropertyName, élément pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="37bdc-103">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="37bdc-104">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="37bdc-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="37bdc-105">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la vue est utilisée.</span><span class="sxs-lookup"><span data-stu-id="37bdc-105">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="37bdc-106">Cet élément est utilisé lors de la définition d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="37bdc-106">This element is used when defining a list view.</span></span>

<span data-ttu-id="37bdc-107">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément de ListControl (format) élément ListItems pour l’élément ListItem pour ListControl (format) ListItem pour l’élément ListItems pour ListControl (format) ItemSelectionCondition, élément pour ListItem pour l’élément ListControls PropertyName pour ItemSelectionCondition pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="37bdc-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37bdc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37bdc-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37bdc-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="37bdc-109">Attributes and Elements</span></span>

<span data-ttu-id="37bdc-110">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="37bdc-110">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37bdc-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="37bdc-111">Attributes</span></span>

<span data-ttu-id="37bdc-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="37bdc-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37bdc-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="37bdc-113">Child Elements</span></span>

<span data-ttu-id="37bdc-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="37bdc-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="37bdc-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="37bdc-115">Parent Elements</span></span>

|<span data-ttu-id="37bdc-116">Élément</span><span class="sxs-lookup"><span data-stu-id="37bdc-116">Element</span></span>|<span data-ttu-id="37bdc-117">Description</span><span class="sxs-lookup"><span data-stu-id="37bdc-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37bdc-118">ItemSelectionCondition, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="37bdc-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="37bdc-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="37bdc-119">Text Value</span></span>

<span data-ttu-id="37bdc-120">Spécifiez le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="37bdc-120">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="37bdc-121">Notes</span><span class="sxs-lookup"><span data-stu-id="37bdc-121">Remarks</span></span>

<span data-ttu-id="37bdc-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="37bdc-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="37bdc-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37bdc-123">See Also</span></span>

[<span data-ttu-id="37bdc-124">Élément ScriptBlock pour ItemSelectionCondition pour ListIControl (format)</span><span class="sxs-lookup"><span data-stu-id="37bdc-124">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="37bdc-125">ItemSelectionCondition, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="37bdc-125">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="37bdc-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="37bdc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
