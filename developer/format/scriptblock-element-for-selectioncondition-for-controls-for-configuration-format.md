---
title: Élément ScriptBlock pour SelectionCondition pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064422"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="e9b38-102">ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e9b38-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e9b38-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="e9b38-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e9b38-104">Lorsque ce script est évalué à `true`, la condition est remplie et que la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e9b38-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="e9b38-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="e9b38-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e9b38-106">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de EntrySelectedBy Configuration (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition Configuration (Format) pour EntrySelectedBy pour les contrôles de Configuration (Format) Élément ScriptBlock pour SelectionCondition pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e9b38-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e9b38-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9b38-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9b38-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e9b38-108">Attributes and Elements</span></span>

<span data-ttu-id="e9b38-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="e9b38-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9b38-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="e9b38-110">Attributes</span></span>

<span data-ttu-id="e9b38-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e9b38-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9b38-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e9b38-112">Child Elements</span></span>

<span data-ttu-id="e9b38-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e9b38-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e9b38-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e9b38-114">Parent Elements</span></span>

|<span data-ttu-id="e9b38-115">Élément</span><span class="sxs-lookup"><span data-stu-id="e9b38-115">Element</span></span>|<span data-ttu-id="e9b38-116">Description</span><span class="sxs-lookup"><span data-stu-id="e9b38-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9b38-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e9b38-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="e9b38-118">Définit une condition qui doit exister pour la définition du contrôle commun à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e9b38-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e9b38-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="e9b38-119">Text Value</span></span>

<span data-ttu-id="e9b38-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="e9b38-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9b38-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="e9b38-121">Remarks</span></span>

<span data-ttu-id="e9b38-122">La condition de sélection doit spécifier un moins un script ou le nom à évaluer, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="e9b38-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e9b38-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e9b38-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9b38-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9b38-124">See Also</span></span>

[<span data-ttu-id="e9b38-125">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e9b38-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="e9b38-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9b38-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
