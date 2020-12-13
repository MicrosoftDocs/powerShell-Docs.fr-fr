---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)
description: ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)
ms.openlocfilehash: 78b977548243b6f3a658f15a0249d8cad12e2f1b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664913"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="f5c1c-103">ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="f5c1c-103">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="f5c1c-104">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="f5c1c-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="f5c1c-105">Lorsque ce script est évalué à `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="f5c1c-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="f5c1c-106">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f5c1c-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f5c1c-107">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour la vue (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour la vue (format) élément CustomItem pour CustomControl pour la vue (format), élément de CustomEntry pour CustomControl pour la vue (format) élément ScriptBlock pour SelectionCondition pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="f5c1c-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5c1c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5c1c-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5c1c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f5c1c-109">Attributes and Elements</span></span>

<span data-ttu-id="f5c1c-110">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="f5c1c-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5c1c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f5c1c-111">Attributes</span></span>

<span data-ttu-id="f5c1c-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f5c1c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5c1c-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f5c1c-113">Child Elements</span></span>

<span data-ttu-id="f5c1c-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f5c1c-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5c1c-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f5c1c-115">Parent Elements</span></span>

|<span data-ttu-id="f5c1c-116">Élément</span><span class="sxs-lookup"><span data-stu-id="f5c1c-116">Element</span></span>|<span data-ttu-id="f5c1c-117">Description</span><span class="sxs-lookup"><span data-stu-id="f5c1c-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5c1c-118">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f5c1c-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="f5c1c-119">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="f5c1c-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f5c1c-120">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="f5c1c-120">Text Value</span></span>

<span data-ttu-id="f5c1c-121">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="f5c1c-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5c1c-122">Notes</span><span class="sxs-lookup"><span data-stu-id="f5c1c-122">Remarks</span></span>

<span data-ttu-id="f5c1c-123">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="f5c1c-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="f5c1c-124">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f5c1c-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5c1c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5c1c-125">See Also</span></span>

[<span data-ttu-id="f5c1c-126">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="f5c1c-126">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="f5c1c-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5c1c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
