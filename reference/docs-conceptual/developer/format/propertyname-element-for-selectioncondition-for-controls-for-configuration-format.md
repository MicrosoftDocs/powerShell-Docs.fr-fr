---
title: PropertyName, élément de SelectionCondition pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362398"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="4c4c8-102">PropertyName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="4c4c8-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4c4c8-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="4c4c8-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="4c4c8-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et l’entrée est utilisée.</span><span class="sxs-lookup"><span data-stu-id="4c4c8-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="4c4c8-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="4c4c8-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4c4c8-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration ( Format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles pour la configuration (format) SelectionCondition élément pour EntrySelectedBy pour la configuration ( Format) PropertyName, élément de SelectionCondition pour EntrySelectedBy pour ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="4c4c8-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4c4c8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c4c8-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4c4c8-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="4c4c8-108">Attributes and Elements</span></span>

<span data-ttu-id="4c4c8-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="4c4c8-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c4c8-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4c4c8-110">Attributes</span></span>

<span data-ttu-id="4c4c8-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="4c4c8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4c4c8-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4c4c8-112">Child Elements</span></span>

<span data-ttu-id="4c4c8-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="4c4c8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4c4c8-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4c4c8-114">Parent Elements</span></span>

|<span data-ttu-id="4c4c8-115">Élément</span><span class="sxs-lookup"><span data-stu-id="4c4c8-115">Element</span></span>|<span data-ttu-id="4c4c8-116">Description</span><span class="sxs-lookup"><span data-stu-id="4c4c8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c4c8-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="4c4c8-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="4c4c8-118">Définit une condition qui doit exister pour qu’une définition de contrôle commun soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="4c4c8-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4c4c8-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="4c4c8-119">Text Value</span></span>

<span data-ttu-id="4c4c8-120">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="4c4c8-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c4c8-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c4c8-121">Remarks</span></span>

<span data-ttu-id="4c4c8-122">La condition de sélection doit spécifier au moins un nom de propriété ou un script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="4c4c8-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="4c4c8-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4c4c8-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c4c8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c4c8-124">See Also</span></span>

[<span data-ttu-id="4c4c8-125">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="4c4c8-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="4c4c8-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c4c8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
