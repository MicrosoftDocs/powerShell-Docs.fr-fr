---
title: Élément PropertyName pour ItemSelectionCondition pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362388"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="27086-102">PropertyName, élément pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="27086-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="27086-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="27086-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="27086-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et la vue est utilisée.</span><span class="sxs-lookup"><span data-stu-id="27086-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="27086-105">Cet élément est utilisé lors de la définition d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="27086-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="27086-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) ListControl, élément (format) ListEntries, élément (format) ListEntry, élément pour ListControl (format) élément ListItems pour ListEntry pour ListControl (format) ListItem Élément de ListItems pour ListControl (format) élément ItemSelectionCondition pour ListItem pour l’élément ListControls PropertyName pour ItemSelectionCondition pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="27086-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="27086-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27086-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27086-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="27086-108">Attributes and Elements</span></span>

<span data-ttu-id="27086-109">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="27086-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="27086-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="27086-110">Attributes</span></span>

<span data-ttu-id="27086-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="27086-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27086-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="27086-112">Child Elements</span></span>

<span data-ttu-id="27086-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="27086-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="27086-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="27086-114">Parent Elements</span></span>

|<span data-ttu-id="27086-115">Élément</span><span class="sxs-lookup"><span data-stu-id="27086-115">Element</span></span>|<span data-ttu-id="27086-116">Description</span><span class="sxs-lookup"><span data-stu-id="27086-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27086-117">Élément ItemSelectionCondition pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="27086-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="27086-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="27086-118">Text Value</span></span>

<span data-ttu-id="27086-119">Spécifiez le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="27086-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="27086-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="27086-120">Remarks</span></span>

<span data-ttu-id="27086-121">Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="27086-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="27086-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27086-122">See Also</span></span>

[<span data-ttu-id="27086-123">Élément ScriptBlock pour ItemSelectionCondition pour ListIControl (format)</span><span class="sxs-lookup"><span data-stu-id="27086-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="27086-124">Élément ItemSelectionCondition pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="27086-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="27086-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="27086-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
