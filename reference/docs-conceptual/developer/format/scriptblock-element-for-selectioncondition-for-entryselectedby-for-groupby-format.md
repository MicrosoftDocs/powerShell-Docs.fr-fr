---
title: Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e70e1555a8f2fe0d15d3e864d80d35527af81b03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785385"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="1fa1c-102">ScriptBlock, élément pour SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1fa1c-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="1fa1c-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1fa1c-104">Lorsque ce script est évalué à `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="1fa1c-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1fa1c-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour View (format) CustomControl, élément pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) élément EntrySelectedBy pour l’élément CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1fa1c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1fa1c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fa1c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1fa1c-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1fa1c-108">Attributes and Elements</span></span>

<span data-ttu-id="1fa1c-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1fa1c-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="1fa1c-110">Attributes</span></span>

<span data-ttu-id="1fa1c-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1fa1c-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1fa1c-112">Child Elements</span></span>

<span data-ttu-id="1fa1c-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1fa1c-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1fa1c-114">Parent Elements</span></span>

|<span data-ttu-id="1fa1c-115">Élément</span><span class="sxs-lookup"><span data-stu-id="1fa1c-115">Element</span></span>|<span data-ttu-id="1fa1c-116">Description</span><span class="sxs-lookup"><span data-stu-id="1fa1c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1fa1c-117">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1fa1c-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="1fa1c-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1fa1c-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="1fa1c-119">Text Value</span></span>

<span data-ttu-id="1fa1c-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fa1c-121">Notes</span><span class="sxs-lookup"><span data-stu-id="1fa1c-121">Remarks</span></span>

<span data-ttu-id="1fa1c-122">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="1fa1c-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1fa1c-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1fa1c-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1fa1c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fa1c-124">See Also</span></span>

[<span data-ttu-id="1fa1c-125">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1fa1c-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="1fa1c-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1fa1c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
