---
title: Élément ItemSelectionCondition pour ListItem pour un objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861865"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="96ed0-102">ItemSelectionCondition, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96ed0-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="96ed0-103">Définit la condition qui doit exister pour cet élément de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="96ed0-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="96ed0-104">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément d’élément de ListEntry ListControl (Format) pour situés d’élément de ListItems ListControl (Format) pour ListEntry élément de ListItem ListControl (Format) pour ListItems d’élément de ItemSelectionCondition ListControl (Format) pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96ed0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="96ed0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96ed0-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="96ed0-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="96ed0-106">Attributes and Elements</span></span>

<span data-ttu-id="96ed0-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="96ed0-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="96ed0-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="96ed0-108">Attributes</span></span>

<span data-ttu-id="96ed0-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="96ed0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="96ed0-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="96ed0-110">Child Elements</span></span>

|<span data-ttu-id="96ed0-111">Élément</span><span class="sxs-lookup"><span data-stu-id="96ed0-111">Element</span></span>|<span data-ttu-id="96ed0-112">Description</span><span class="sxs-lookup"><span data-stu-id="96ed0-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96ed0-113">Élément PropertyName pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96ed0-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="96ed0-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="96ed0-114">Optional element.</span></span><br /><br /> <span data-ttu-id="96ed0-115">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="96ed0-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="96ed0-116">Élément ScriptBlock pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96ed0-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="96ed0-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="96ed0-117">Optional element.</span></span><br /><br /> <span data-ttu-id="96ed0-118">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="96ed0-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="96ed0-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="96ed0-119">Parent Elements</span></span>

|<span data-ttu-id="96ed0-120">Élément</span><span class="sxs-lookup"><span data-stu-id="96ed0-120">Element</span></span>|<span data-ttu-id="96ed0-121">Description</span><span class="sxs-lookup"><span data-stu-id="96ed0-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96ed0-122">Élément ListItem pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96ed0-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="96ed0-123">Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="96ed0-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="96ed0-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="96ed0-124">Remarks</span></span>

<span data-ttu-id="96ed0-125">Vous pouvez spécifier un nom de propriété ou un script pour cette condition mais que vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="96ed0-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="96ed0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96ed0-126">See Also</span></span>

[<span data-ttu-id="96ed0-127">Élément ListItem pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96ed0-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="96ed0-128">Élément PropertyName pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96ed0-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="96ed0-129">Élément ScriptBlock pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96ed0-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="96ed0-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="96ed0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
