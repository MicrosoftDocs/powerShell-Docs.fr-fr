---
title: Élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9467c8c2d80e46c0a47c31569efbddbabe25bb1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774267"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="de62c-102">EntrySelectedBy, élément pour CustomEntry pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="de62c-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="de62c-103">Définit les types .NET qui utilisent la définition du contrôle commun ou la condition qui doit exister pour que ce contrôle soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="de62c-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="de62c-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="de62c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="de62c-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="de62c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de62c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de62c-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de62c-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="de62c-107">Attributes and Elements</span></span>

<span data-ttu-id="de62c-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="de62c-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de62c-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="de62c-109">Attributes</span></span>

<span data-ttu-id="de62c-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="de62c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de62c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="de62c-111">Child Elements</span></span>

|<span data-ttu-id="de62c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="de62c-112">Element</span></span>|<span data-ttu-id="de62c-113">Description</span><span class="sxs-lookup"><span data-stu-id="de62c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de62c-114">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="de62c-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="de62c-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="de62c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="de62c-116">Définit la condition qui doit exister pour que la définition de contrôle commun soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="de62c-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="de62c-117">SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="de62c-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="de62c-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="de62c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="de62c-119">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="de62c-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="de62c-120">TypeName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="de62c-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="de62c-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="de62c-121">Optional element.</span></span><br /><br /> <span data-ttu-id="de62c-122">Spécifie un type .NET qui utilise cette définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="de62c-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="de62c-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="de62c-123">Parent Elements</span></span>

|<span data-ttu-id="de62c-124">Élément</span><span class="sxs-lookup"><span data-stu-id="de62c-124">Element</span></span>|<span data-ttu-id="de62c-125">Description</span><span class="sxs-lookup"><span data-stu-id="de62c-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de62c-126">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="de62c-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="de62c-127">Fournit une définition du contrôle commun.</span><span class="sxs-lookup"><span data-stu-id="de62c-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="de62c-128">Notes</span><span class="sxs-lookup"><span data-stu-id="de62c-128">Remarks</span></span>

<span data-ttu-id="de62c-129">Au minimum, chaque définition doit avoir au moins un type .NET, un jeu de sélection ou une condition de sélection spécifiés.</span><span class="sxs-lookup"><span data-stu-id="de62c-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="de62c-130">Il n’existe pas de limite maximale pour le nombre de types, de jeux de sélection ou de conditions de sélection que vous pouvez spécifier.</span><span class="sxs-lookup"><span data-stu-id="de62c-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="de62c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de62c-131">See Also</span></span>

[<span data-ttu-id="de62c-132">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="de62c-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="de62c-133">SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="de62c-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="de62c-134">CustomEntry, élément pour CustomControl pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="de62c-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="de62c-135">TypeName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="de62c-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="de62c-136">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="de62c-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
