---
title: Élément SelectionSetName pour SelectionCondition pour les contrôles de configuration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368278"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="a6416-102">SelectionSetName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a6416-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a6416-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="a6416-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="a6416-104">Quand l’un des types de cet ensemble est présent, la condition est remplie et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="a6416-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="a6416-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="a6416-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a6416-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour les contrôles pour Configuration (format) élément CustomEntry pour CustomControl pour les contrôles pour la configuration (format) EntrySelectedBy, élément de CustomEntry pour les contrôles de configuration (format) SelectionCondition, élément pour EntrySelectedBy pour les contrôles de Élément de configuration (format) SelectionSetName pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a6416-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6416-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6416-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6416-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="a6416-108">Attributes and Elements</span></span>

<span data-ttu-id="a6416-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="a6416-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6416-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a6416-110">Attributes</span></span>

<span data-ttu-id="a6416-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="a6416-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6416-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a6416-112">Child Elements</span></span>

<span data-ttu-id="a6416-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="a6416-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6416-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a6416-114">Parent Elements</span></span>

|<span data-ttu-id="a6416-115">Élément</span><span class="sxs-lookup"><span data-stu-id="a6416-115">Element</span></span>|<span data-ttu-id="a6416-116">Description</span><span class="sxs-lookup"><span data-stu-id="a6416-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6416-117">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a6416-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="a6416-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a6416-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a6416-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="a6416-119">Text Value</span></span>

<span data-ttu-id="a6416-120">Spécifiez le nom du jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="a6416-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6416-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="a6416-121">Remarks</span></span>

<span data-ttu-id="a6416-122">Les jeux de sélection sont des groupes communs d’objets .NET qui peuvent être utilisés par n’importe quelle vue définie par le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="a6416-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="a6416-123">Pour plus d’informations sur la création et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a6416-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a6416-124">La condition de sélection peut spécifier un jeu de sélection ou un type .NET, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="a6416-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="a6416-125">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a6416-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6416-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6416-126">See Also</span></span>

[<span data-ttu-id="a6416-127">Élément SelectionCondition pour EntrySelectedBy pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a6416-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="a6416-128">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="a6416-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a6416-129">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="a6416-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a6416-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6416-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
