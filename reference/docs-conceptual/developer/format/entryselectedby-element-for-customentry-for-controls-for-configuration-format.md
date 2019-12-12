---
title: Élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368768"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="3ee5f-102">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3ee5f-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3ee5f-103">Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="3ee5f-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3ee5f-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration ( Format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee5f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ee5f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ee5f-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ee5f-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="3ee5f-107">Attributes and Elements</span></span>

<span data-ttu-id="3ee5f-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ee5f-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="3ee5f-109">Attributes</span></span>

<span data-ttu-id="3ee5f-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ee5f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3ee5f-111">Child Elements</span></span>

|<span data-ttu-id="3ee5f-112">Élément</span><span class="sxs-lookup"><span data-stu-id="3ee5f-112">Element</span></span>|<span data-ttu-id="3ee5f-113">Description</span><span class="sxs-lookup"><span data-stu-id="3ee5f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ee5f-114">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee5f-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="3ee5f-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3ee5f-116">Définit la condition qui doit exister pour que la définition de contrôle commun soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="3ee5f-117">Élément SelectionSetName pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee5f-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="3ee5f-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3ee5f-119">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="3ee5f-120">Élément TypeName pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee5f-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="3ee5f-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3ee5f-122">Spécifie un type .NET qui utilise cette définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3ee5f-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3ee5f-123">Parent Elements</span></span>

|<span data-ttu-id="3ee5f-124">Élément</span><span class="sxs-lookup"><span data-stu-id="3ee5f-124">Element</span></span>|<span data-ttu-id="3ee5f-125">Description</span><span class="sxs-lookup"><span data-stu-id="3ee5f-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ee5f-126">Élément CustomEntry pour CustomControl pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee5f-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="3ee5f-127">Fournit une définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3ee5f-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="3ee5f-128">Remarks</span></span>

<span data-ttu-id="3ee5f-129">Au minimum, chaque définition doit avoir au moins un type .NET, un jeu de sélection ou une condition de sélection spécifiés.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="3ee5f-130">Il n’existe pas de limite maximale pour le nombre de types, de jeux de sélection ou de conditions de sélection que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="3ee5f-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ee5f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ee5f-131">See Also</span></span>

[<span data-ttu-id="3ee5f-132">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee5f-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="3ee5f-133">Élément SelectionSetName pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee5f-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="3ee5f-134">Élément CustomEntry pour CustomControl pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee5f-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="3ee5f-135">Élément TypeName pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3ee5f-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="3ee5f-136">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ee5f-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
