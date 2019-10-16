---
title: Élément ScriptBlock pour SelectionCondition pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368618"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="bd463-102">ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="bd463-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bd463-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="bd463-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="bd463-104">Lorsque ce script est évalué à `true`, la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="bd463-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="bd463-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="bd463-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bd463-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration ( Format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) SelectionCondition, élément pour EntrySelectedBy pour les contrôles de configuration (format) Élément ScriptBlock pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bd463-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd463-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd463-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd463-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="bd463-108">Attributes and Elements</span></span>

<span data-ttu-id="bd463-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="bd463-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd463-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="bd463-110">Attributes</span></span>

<span data-ttu-id="bd463-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="bd463-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd463-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bd463-112">Child Elements</span></span>

<span data-ttu-id="bd463-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="bd463-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bd463-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bd463-114">Parent Elements</span></span>

|<span data-ttu-id="bd463-115">Élément</span><span class="sxs-lookup"><span data-stu-id="bd463-115">Element</span></span>|<span data-ttu-id="bd463-116">Description</span><span class="sxs-lookup"><span data-stu-id="bd463-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd463-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bd463-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="bd463-118">Définit une condition qui doit exister pour que la définition de contrôle commun soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="bd463-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bd463-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="bd463-119">Text Value</span></span>

<span data-ttu-id="bd463-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="bd463-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd463-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="bd463-121">Remarks</span></span>

<span data-ttu-id="bd463-122">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="bd463-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="bd463-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bd463-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd463-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd463-124">See Also</span></span>

[<span data-ttu-id="bd463-125">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bd463-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="bd463-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd463-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
