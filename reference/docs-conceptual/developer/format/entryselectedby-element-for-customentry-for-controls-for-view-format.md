---
title: Élément EntrySelectedBy pour CustomEntry pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5c82e02d23b1694d05f7a32578ccc5d33686f13f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774250"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="addd1-102">EntrySelectedBy, élément pour CustomEntry pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="addd1-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="addd1-103">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="addd1-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="addd1-104">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="addd1-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="addd1-105">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour la vue (format) élément CustomControl pour le contrôle pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour les contrôles pour l’élément CustomEntry (format) pour les contrôles pour la vue (format)</span><span class="sxs-lookup"><span data-stu-id="addd1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="addd1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="addd1-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="addd1-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="addd1-107">Attributes and Elements</span></span>

<span data-ttu-id="addd1-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `EntrySelectedBy` élément.</span><span class="sxs-lookup"><span data-stu-id="addd1-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="addd1-109">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour une définition.</span><span class="sxs-lookup"><span data-stu-id="addd1-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="addd1-110">Il n’existe pas de limite maximale pour le nombre d’éléments enfants que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="addd1-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="addd1-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="addd1-111">Attributes</span></span>

<span data-ttu-id="addd1-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="addd1-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="addd1-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="addd1-113">Child Elements</span></span>

|<span data-ttu-id="addd1-114">Élément</span><span class="sxs-lookup"><span data-stu-id="addd1-114">Element</span></span>|<span data-ttu-id="addd1-115">Description</span><span class="sxs-lookup"><span data-stu-id="addd1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="addd1-116">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="addd1-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="addd1-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="addd1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="addd1-118">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="addd1-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="addd1-119">SelectionSetName, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="addd1-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="addd1-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="addd1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="addd1-121">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="addd1-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="addd1-122">TypeName, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="addd1-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="addd1-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="addd1-123">Optional element.</span></span><br /><br /> <span data-ttu-id="addd1-124">Spécifie un type .NET qui utilise cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="addd1-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="addd1-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="addd1-125">Parent Elements</span></span>

|<span data-ttu-id="addd1-126">Élément</span><span class="sxs-lookup"><span data-stu-id="addd1-126">Element</span></span>|<span data-ttu-id="addd1-127">Description</span><span class="sxs-lookup"><span data-stu-id="addd1-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="addd1-128">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="addd1-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="addd1-129">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="addd1-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="addd1-130">Notes</span><span class="sxs-lookup"><span data-stu-id="addd1-130">Remarks</span></span>

<span data-ttu-id="addd1-131">Les conditions de sélection sont utilisées pour définir une condition qui doit exister pour la définition à utiliser, par exemple lorsqu’un objet a une propriété spécifique ou lorsqu’une valeur de propriété ou un script spécifique prend la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="addd1-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="addd1-132">Pour plus d’informations sur les conditions de sélection, consultez [définition des conditions d’utilisation d’une entrée ou d’un élément de vue](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="addd1-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="addd1-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="addd1-133">See Also</span></span>

[<span data-ttu-id="addd1-134">CustomEntry, élément pour CustomEntries pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="addd1-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="addd1-135">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="addd1-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
