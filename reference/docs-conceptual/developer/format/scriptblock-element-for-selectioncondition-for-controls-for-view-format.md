---
title: Élément ScriptBlock pour SelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364798"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="3546f-102">ScriptBlock, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="3546f-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="3546f-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="3546f-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="3546f-104">Lorsque ce script est évalué pour `true`, la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3546f-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="3546f-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="3546f-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3546f-106">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément d’affichage (format) CustomEntry pour CustomEntries pour les contrôles pour l’élément EntrySelectedBy (format) de vue pour CustomEntry pour les contrôles pour l’élément d’affichage (format) SelectionCondition pour les contrôles pour la vue ( Format) élément ScriptBlock pour SelectionCondition pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3546f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3546f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3546f-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3546f-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="3546f-108">Attributes and Elements</span></span>

<span data-ttu-id="3546f-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="3546f-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3546f-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="3546f-110">Attributes</span></span>

<span data-ttu-id="3546f-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3546f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3546f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3546f-112">Child Elements</span></span>

<span data-ttu-id="3546f-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3546f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3546f-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3546f-114">Parent Elements</span></span>

|<span data-ttu-id="3546f-115">Élément</span><span class="sxs-lookup"><span data-stu-id="3546f-115">Element</span></span>|<span data-ttu-id="3546f-116">Description</span><span class="sxs-lookup"><span data-stu-id="3546f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3546f-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3546f-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="3546f-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="3546f-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3546f-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="3546f-119">Text Value</span></span>

<span data-ttu-id="3546f-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="3546f-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="3546f-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="3546f-121">Remarks</span></span>

<span data-ttu-id="3546f-122">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="3546f-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="3546f-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3546f-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3546f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3546f-124">See Also</span></span>

[<span data-ttu-id="3546f-125">Élément SelectionCondition pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="3546f-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="3546f-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3546f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
