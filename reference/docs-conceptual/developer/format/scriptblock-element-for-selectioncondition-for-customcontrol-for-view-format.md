---
title: Élément ScriptBlock pour SelectionCondition pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d3506188d32ce85ad6345dc0d0866dd789a1f293
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785402"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="2a739-102">ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="2a739-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="2a739-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="2a739-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="2a739-104">Lorsque ce script est évalué à `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2a739-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="2a739-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2a739-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2a739-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour la vue (format) élément CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour la vue (format) élément CustomItem pour CustomControl pour la vue (format), élément de CustomEntry pour CustomControl pour la vue (format) élément ScriptBlock pour SelectionCondition pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="2a739-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a739-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a739-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a739-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2a739-108">Attributes and Elements</span></span>

<span data-ttu-id="2a739-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="2a739-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a739-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="2a739-110">Attributes</span></span>

<span data-ttu-id="2a739-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2a739-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a739-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2a739-112">Child Elements</span></span>

<span data-ttu-id="2a739-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2a739-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2a739-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2a739-114">Parent Elements</span></span>

|<span data-ttu-id="2a739-115">Élément</span><span class="sxs-lookup"><span data-stu-id="2a739-115">Element</span></span>|<span data-ttu-id="2a739-116">Description</span><span class="sxs-lookup"><span data-stu-id="2a739-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a739-117">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="2a739-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="2a739-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="2a739-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2a739-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="2a739-119">Text Value</span></span>

<span data-ttu-id="2a739-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="2a739-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a739-121">Notes</span><span class="sxs-lookup"><span data-stu-id="2a739-121">Remarks</span></span>

<span data-ttu-id="2a739-122">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="2a739-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="2a739-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2a739-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a739-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a739-124">See Also</span></span>

[<span data-ttu-id="2a739-125">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="2a739-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="2a739-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a739-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
