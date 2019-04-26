---
title: Élément SelectionSetName pour EntrySelectedBy pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063971"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="09459-102">SelectionSetName, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="09459-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="09459-103">Spécifie un ensemble de types .NET qui utilisent cette définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="09459-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="09459-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="09459-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="09459-105">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles d’élément de CustomControl Configuration (Format) pour le contrôle de l’élément de Configuration (Format) de CustomEntries pour CustomControl pour la Configuration ( Élément CustomEntry de format) pour CustomControl pour les contrôles d’élément de EntrySelectedBy Configuration (Format) pour CustomEntry pour les contrôles d’élément de SelectionSetName Configuration (Format) pour EntrySelectedBy pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="09459-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09459-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09459-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="09459-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="09459-107">Attributes and Elements</span></span>

<span data-ttu-id="09459-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="09459-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="09459-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="09459-109">Attributes</span></span>

<span data-ttu-id="09459-110">Aucune</span><span class="sxs-lookup"><span data-stu-id="09459-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="09459-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="09459-111">Child Elements</span></span>

<span data-ttu-id="09459-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="09459-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="09459-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="09459-113">Parent Elements</span></span>

|<span data-ttu-id="09459-114">Élément</span><span class="sxs-lookup"><span data-stu-id="09459-114">Element</span></span>|<span data-ttu-id="09459-115">Description</span><span class="sxs-lookup"><span data-stu-id="09459-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09459-116">Élément EntrySelectedBy pour CustomEntry pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="09459-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="09459-117">Définit les types .NET qui utilisent cette définition de contrôle ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="09459-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="09459-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="09459-118">Text Value</span></span>

<span data-ttu-id="09459-119">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="09459-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="09459-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="09459-120">Remarks</span></span>

<span data-ttu-id="09459-121">Chaque définition de contrôle doit avoir au moins un nom de type, jeu de sélection ou défini par le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="09459-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="09459-122">Sélection jeux sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="09459-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="09459-123">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition sélection définit](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="09459-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="09459-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09459-124">See Also</span></span>

[<span data-ttu-id="09459-125">Élément EntrySelectedBy pour CustomEntry pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="09459-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="09459-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="09459-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
