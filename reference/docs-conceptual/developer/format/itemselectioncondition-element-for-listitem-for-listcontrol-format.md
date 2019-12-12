---
title: Élément ItemSelectionCondition pour ListItem pour ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365188"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="11104-102">ItemSelectionCondition, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="11104-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="11104-103">Définit la condition qui doit exister pour l’élément de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="11104-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="11104-104">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) ListEntry, élément de ListEntries pour ListControl (format) ListItems, élément de ListEntry pour l’élément ListControl (format) ListItem pour ListItems pour ListControl (format), élément ItemSelectionCondition pour ListItem pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="11104-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11104-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11104-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11104-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="11104-106">Attributes and Elements</span></span>

<span data-ttu-id="11104-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="11104-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11104-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="11104-108">Attributes</span></span>

<span data-ttu-id="11104-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="11104-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11104-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="11104-110">Child Elements</span></span>

|<span data-ttu-id="11104-111">Élément</span><span class="sxs-lookup"><span data-stu-id="11104-111">Element</span></span>|<span data-ttu-id="11104-112">Description</span><span class="sxs-lookup"><span data-stu-id="11104-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11104-113">Élément PropertyName pour ItemSelectionCondition pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="11104-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="11104-114">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="11104-114">Optional element.</span></span><br /><br /> <span data-ttu-id="11104-115">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="11104-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="11104-116">Élément ScriptBlock pour ItemSelectionCondition pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="11104-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="11104-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="11104-117">Optional element.</span></span><br /><br /> <span data-ttu-id="11104-118">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="11104-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="11104-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="11104-119">Parent Elements</span></span>

|<span data-ttu-id="11104-120">Élément</span><span class="sxs-lookup"><span data-stu-id="11104-120">Element</span></span>|<span data-ttu-id="11104-121">Description</span><span class="sxs-lookup"><span data-stu-id="11104-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11104-122">Élément ListItem pour ListItems pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="11104-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="11104-123">Définit la propriété ou le script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="11104-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="11104-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="11104-124">Remarks</span></span>

<span data-ttu-id="11104-125">Vous pouvez spécifier un nom de propriété ou un script pour cette condition, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="11104-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="11104-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11104-126">See Also</span></span>

[<span data-ttu-id="11104-127">Élément ListItem pour ListItems pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="11104-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="11104-128">Élément PropertyName pour ItemSelectionCondition pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="11104-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="11104-129">Élément ScriptBlock pour ItemSelectionCondition pour ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="11104-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="11104-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="11104-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
