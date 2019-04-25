---
title: Élément ScriptBlock pour SelectionCondition pour les contrôles de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064388"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="08a5d-102">ScriptBlock, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="08a5d-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="08a5d-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="08a5d-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="08a5d-104">Lorsque ce script est évalué à `true`, la condition est remplie et que la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="08a5d-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="08a5d-105">Cet élément est utilisé lors de la définition des contrôles qui peuvent être utilisées par une vue.</span><span class="sxs-lookup"><span data-stu-id="08a5d-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="08a5d-106">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) contrôles élément (Format) contrôle élément de configuration pour les contrôles d’élément de CustomControl vue (Format) pour le contrôle pour les contrôles d’élément de CustomEntries vue (Format) pour CustomControl pour les contrôles d’élément de CustomEntry vue (Format) pour CustomEntries pour les contrôles d’élément de EntrySelectedBy vue (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition vue (Format) pour EntrySelectedBy pour les contrôles pour afficher ( Format), élément ScriptBlock pour SelectionCondition pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="08a5d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08a5d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08a5d-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08a5d-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="08a5d-108">Attributes and Elements</span></span>

<span data-ttu-id="08a5d-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="08a5d-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="08a5d-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="08a5d-110">Attributes</span></span>

<span data-ttu-id="08a5d-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="08a5d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08a5d-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="08a5d-112">Child Elements</span></span>

<span data-ttu-id="08a5d-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="08a5d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="08a5d-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="08a5d-114">Parent Elements</span></span>

|<span data-ttu-id="08a5d-115">Élément</span><span class="sxs-lookup"><span data-stu-id="08a5d-115">Element</span></span>|<span data-ttu-id="08a5d-116">Description</span><span class="sxs-lookup"><span data-stu-id="08a5d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08a5d-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="08a5d-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="08a5d-118">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="08a5d-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="08a5d-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="08a5d-119">Text Value</span></span>

<span data-ttu-id="08a5d-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="08a5d-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="08a5d-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="08a5d-121">Remarks</span></span>

<span data-ttu-id="08a5d-122">La condition de sélection doit spécifier un moins un script ou le nom à évaluer, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="08a5d-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="08a5d-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="08a5d-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="08a5d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08a5d-124">See Also</span></span>

[<span data-ttu-id="08a5d-125">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="08a5d-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="08a5d-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="08a5d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
