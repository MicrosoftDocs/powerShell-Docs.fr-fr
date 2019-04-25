---
title: Élément EntrySelectedBy pour CustomEntry pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066292"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="49c6e-102">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="49c6e-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="49c6e-103">Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour ce contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="49c6e-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="49c6e-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="49c6e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="49c6e-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de EntrySelectedBy Configuration (Format) pour CustomEntry pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="49c6e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="49c6e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49c6e-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49c6e-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="49c6e-107">Attributes and Elements</span></span>

<span data-ttu-id="49c6e-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="49c6e-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="49c6e-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="49c6e-109">Attributes</span></span>

<span data-ttu-id="49c6e-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="49c6e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49c6e-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="49c6e-111">Child Elements</span></span>

|<span data-ttu-id="49c6e-112">Élément</span><span class="sxs-lookup"><span data-stu-id="49c6e-112">Element</span></span>|<span data-ttu-id="49c6e-113">Description</span><span class="sxs-lookup"><span data-stu-id="49c6e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49c6e-114">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="49c6e-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="49c6e-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="49c6e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="49c6e-116">Définit la condition qui doit exister pour la définition du contrôle commun à utiliser.</span><span class="sxs-lookup"><span data-stu-id="49c6e-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="49c6e-117">Élément SelectionSetName pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="49c6e-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="49c6e-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="49c6e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="49c6e-119">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="49c6e-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="49c6e-120">Élément TypeName pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="49c6e-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="49c6e-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="49c6e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="49c6e-122">Spécifie un type .NET qui utilise cette définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="49c6e-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="49c6e-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="49c6e-123">Parent Elements</span></span>

|<span data-ttu-id="49c6e-124">Élément</span><span class="sxs-lookup"><span data-stu-id="49c6e-124">Element</span></span>|<span data-ttu-id="49c6e-125">Description</span><span class="sxs-lookup"><span data-stu-id="49c6e-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49c6e-126">Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="49c6e-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="49c6e-127">Fournit une définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="49c6e-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="49c6e-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="49c6e-128">Remarks</span></span>

<span data-ttu-id="49c6e-129">Au minimum, chaque définition doit avoir au moins un type .NET, jeu de sélection ou le critère de sélection spécifié.</span><span class="sxs-lookup"><span data-stu-id="49c6e-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="49c6e-130">Il n’existe aucune limite maximale pour le nombre de types, des jeux de sélection ou des conditions de sélection que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="49c6e-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="49c6e-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49c6e-131">See Also</span></span>

[<span data-ttu-id="49c6e-132">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="49c6e-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="49c6e-133">Élément SelectionSetName pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="49c6e-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="49c6e-134">Élément CustomEntry pour CustomControl pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="49c6e-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="49c6e-135">Élément TypeName pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="49c6e-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="49c6e-136">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="49c6e-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
