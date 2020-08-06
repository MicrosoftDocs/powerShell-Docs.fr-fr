---
title: Élément ScriptBlock pour ItemSelectionCondition pour ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 38dc952bfadd6aed24bae8cbef05adcd22e61dd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787629"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="4ecb1-102">ScriptBlock, élément pour ItemSelectionCondition pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4ecb1-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="4ecb1-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="4ecb1-104">Lorsque ce script est évalué à `true` , la condition est remplie et l’élément de liste est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="4ecb1-105">Cet élément est utilisé lors de la définition d’un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="4ecb1-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) ListControl, élément (format) ListEntries, élément de ListControl (format) élément ListEntry pour ListEntries pour ListControl (format) ListItems, élément de l’élément ItemSelectionCondition de l’élément ListControl pour ListControl (format) pour l’élément ListItems pour le contrôle List (format)</span><span class="sxs-lookup"><span data-stu-id="4ecb1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ecb1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ecb1-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ecb1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4ecb1-108">Attributes and Elements</span></span>

<span data-ttu-id="4ecb1-109">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ecb1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4ecb1-110">Attributes</span></span>

<span data-ttu-id="4ecb1-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ecb1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4ecb1-112">Child Elements</span></span>

<span data-ttu-id="4ecb1-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ecb1-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4ecb1-114">Parent Elements</span></span>

|<span data-ttu-id="4ecb1-115">Élément</span><span class="sxs-lookup"><span data-stu-id="4ecb1-115">Element</span></span>|<span data-ttu-id="4ecb1-116">Description</span><span class="sxs-lookup"><span data-stu-id="4ecb1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ecb1-117">ItemSelectionCondition, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4ecb1-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="4ecb1-118">Définit la condition qui doit exister pour l’élément de liste à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4ecb1-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="4ecb1-119">Text Value</span></span>

<span data-ttu-id="4ecb1-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ecb1-121">Notes</span><span class="sxs-lookup"><span data-stu-id="4ecb1-121">Remarks</span></span>

<span data-ttu-id="4ecb1-122">Si cet élément est utilisé, vous ne pouvez pas spécifier l' `PropertyName` élément lors de la définition de la condition de sélection.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ecb1-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ecb1-123">See Also</span></span>

[<span data-ttu-id="4ecb1-124">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ecb1-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
