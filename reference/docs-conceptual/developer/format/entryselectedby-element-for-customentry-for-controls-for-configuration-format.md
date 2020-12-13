---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)
description: EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)
ms.openlocfilehash: fadcdb69ac71269ba2f2f80baf139bb363d4acba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666669"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="50ddc-103">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="50ddc-103">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="50ddc-104">Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="50ddc-104">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="50ddc-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="50ddc-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="50ddc-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="50ddc-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="50ddc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50ddc-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50ddc-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="50ddc-108">Attributes and Elements</span></span>

<span data-ttu-id="50ddc-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="50ddc-109">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="50ddc-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="50ddc-110">Attributes</span></span>

<span data-ttu-id="50ddc-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="50ddc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50ddc-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="50ddc-112">Child Elements</span></span>

|<span data-ttu-id="50ddc-113">Élément</span><span class="sxs-lookup"><span data-stu-id="50ddc-113">Element</span></span>|<span data-ttu-id="50ddc-114">Description</span><span class="sxs-lookup"><span data-stu-id="50ddc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50ddc-115">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="50ddc-115">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="50ddc-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="50ddc-116">Optional element.</span></span><br /><br /> <span data-ttu-id="50ddc-117">Définit la condition qui doit exister pour que la définition de contrôle commun soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="50ddc-117">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="50ddc-118">SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="50ddc-118">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="50ddc-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="50ddc-119">Optional element.</span></span><br /><br /> <span data-ttu-id="50ddc-120">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="50ddc-120">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="50ddc-121">TypeName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="50ddc-121">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="50ddc-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="50ddc-122">Optional element.</span></span><br /><br /> <span data-ttu-id="50ddc-123">Spécifie un type .NET qui utilise cette définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="50ddc-123">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="50ddc-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="50ddc-124">Parent Elements</span></span>

|<span data-ttu-id="50ddc-125">Élément</span><span class="sxs-lookup"><span data-stu-id="50ddc-125">Element</span></span>|<span data-ttu-id="50ddc-126">Description</span><span class="sxs-lookup"><span data-stu-id="50ddc-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50ddc-127">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="50ddc-127">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="50ddc-128">Fournit une définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="50ddc-128">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="50ddc-129">Notes</span><span class="sxs-lookup"><span data-stu-id="50ddc-129">Remarks</span></span>

<span data-ttu-id="50ddc-130">Au minimum, chaque définition doit avoir au moins un type .NET, un jeu de sélection ou une condition de sélection spécifiés.</span><span class="sxs-lookup"><span data-stu-id="50ddc-130">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="50ddc-131">Il n’existe pas de limite maximale pour le nombre de types, de jeux de sélection ou de conditions de sélection que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="50ddc-131">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="50ddc-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50ddc-132">See Also</span></span>

[<span data-ttu-id="50ddc-133">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="50ddc-133">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="50ddc-134">SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="50ddc-134">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="50ddc-135">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="50ddc-135">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="50ddc-136">TypeName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="50ddc-136">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="50ddc-137">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="50ddc-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
