---
title: Élément ScriptBlock pour SelectionCondition pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368638"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="68bc1-102">ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="68bc1-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="68bc1-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="68bc1-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="68bc1-104">Lorsque ce script est évalué pour `true`, la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="68bc1-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="68bc1-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="68bc1-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="68bc1-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour View ( Format) élément CustomItem pour CustomEntry pour CustomControl pour la vue (format) élément SelectionCondition pour EntrySelectedBy pour CustomControl pour la vue (format) élément ScriptBlock pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="68bc1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68bc1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68bc1-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68bc1-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="68bc1-108">Attributes and Elements</span></span>

<span data-ttu-id="68bc1-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="68bc1-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="68bc1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="68bc1-110">Attributes</span></span>

<span data-ttu-id="68bc1-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="68bc1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68bc1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="68bc1-112">Child Elements</span></span>

<span data-ttu-id="68bc1-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="68bc1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="68bc1-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="68bc1-114">Parent Elements</span></span>

|<span data-ttu-id="68bc1-115">Élément</span><span class="sxs-lookup"><span data-stu-id="68bc1-115">Element</span></span>|<span data-ttu-id="68bc1-116">Description</span><span class="sxs-lookup"><span data-stu-id="68bc1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68bc1-117">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="68bc1-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="68bc1-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="68bc1-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="68bc1-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="68bc1-119">Text Value</span></span>

<span data-ttu-id="68bc1-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="68bc1-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="68bc1-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="68bc1-121">Remarks</span></span>

<span data-ttu-id="68bc1-122">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="68bc1-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="68bc1-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="68bc1-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68bc1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68bc1-124">See Also</span></span>

[<span data-ttu-id="68bc1-125">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="68bc1-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="68bc1-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="68bc1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
