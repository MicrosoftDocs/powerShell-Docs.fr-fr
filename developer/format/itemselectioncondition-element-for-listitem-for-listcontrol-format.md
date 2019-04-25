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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065442"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="d4b98-102">ItemSelectionCondition, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d4b98-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="d4b98-103">Définit la condition qui doit exister pour cet élément de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d4b98-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="d4b98-104">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément d’élément de ListEntry ListControl (Format) pour situés d’élément de ListItems ListControl (Format) pour ListEntry élément de ListItem ListControl (Format) pour ListItems d’élément de ItemSelectionCondition ListControl (Format) pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d4b98-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d4b98-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4b98-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4b98-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d4b98-106">Attributes and Elements</span></span>

<span data-ttu-id="d4b98-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ItemSelectionCondition` élément.</span><span class="sxs-lookup"><span data-stu-id="d4b98-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4b98-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="d4b98-108">Attributes</span></span>

<span data-ttu-id="d4b98-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d4b98-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4b98-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d4b98-110">Child Elements</span></span>

|<span data-ttu-id="d4b98-111">Élément</span><span class="sxs-lookup"><span data-stu-id="d4b98-111">Element</span></span>|<span data-ttu-id="d4b98-112">Description</span><span class="sxs-lookup"><span data-stu-id="d4b98-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4b98-113">Élément PropertyName pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d4b98-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="d4b98-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d4b98-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d4b98-115">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="d4b98-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d4b98-116">Élément ScriptBlock pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d4b98-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="d4b98-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d4b98-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d4b98-118">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="d4b98-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d4b98-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d4b98-119">Parent Elements</span></span>

|<span data-ttu-id="d4b98-120">Élément</span><span class="sxs-lookup"><span data-stu-id="d4b98-120">Element</span></span>|<span data-ttu-id="d4b98-121">Description</span><span class="sxs-lookup"><span data-stu-id="d4b98-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4b98-122">Élément ListItem pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d4b98-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="d4b98-123">Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="d4b98-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d4b98-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="d4b98-124">Remarks</span></span>

<span data-ttu-id="d4b98-125">Vous pouvez spécifier un nom de propriété ou un script pour cette condition mais que vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d4b98-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4b98-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4b98-126">See Also</span></span>

[<span data-ttu-id="d4b98-127">Élément ListItem pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d4b98-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="d4b98-128">Élément PropertyName pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d4b98-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="d4b98-129">Élément ScriptBlock pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d4b98-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="d4b98-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d4b98-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
