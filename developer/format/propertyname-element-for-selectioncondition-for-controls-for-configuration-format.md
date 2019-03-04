---
title: Élément PropertyName pour SelectionCondition pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861025"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="75eda-102">PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="75eda-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="75eda-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="75eda-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="75eda-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et l’entrée est utilisée.</span><span class="sxs-lookup"><span data-stu-id="75eda-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="75eda-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="75eda-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="75eda-106">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Format), élément pour CustomControl pour les contrôles d’élément de EntrySelectedBy Configuration (Format) pour CustomEntry pour les contrôles d’élément de SelectionCondition Configuration (Format) pour EntrySelectedBy pour CustomEntry pour la Configuration (CustomEntry Élément de PropertyName format) pour SelectionCondition pour EntrySelectedBy pour ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="75eda-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75eda-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75eda-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75eda-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="75eda-108">Attributes and Elements</span></span>

<span data-ttu-id="75eda-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="75eda-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="75eda-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="75eda-110">Attributes</span></span>

<span data-ttu-id="75eda-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="75eda-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75eda-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="75eda-112">Child Elements</span></span>

<span data-ttu-id="75eda-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="75eda-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75eda-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="75eda-114">Parent Elements</span></span>

|<span data-ttu-id="75eda-115">Élément</span><span class="sxs-lookup"><span data-stu-id="75eda-115">Element</span></span>|<span data-ttu-id="75eda-116">Description</span><span class="sxs-lookup"><span data-stu-id="75eda-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75eda-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="75eda-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="75eda-118">Définit une condition qui doit exister pour une définition commune de contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="75eda-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="75eda-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="75eda-119">Text Value</span></span>

<span data-ttu-id="75eda-120">Spécifiez le nom de propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="75eda-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="75eda-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="75eda-121">Remarks</span></span>

<span data-ttu-id="75eda-122">La condition de sélection doit spécifier un nom d’un propriété minimum ou un script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="75eda-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="75eda-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="75eda-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75eda-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75eda-124">See Also</span></span>

[<span data-ttu-id="75eda-125">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="75eda-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="75eda-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75eda-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
