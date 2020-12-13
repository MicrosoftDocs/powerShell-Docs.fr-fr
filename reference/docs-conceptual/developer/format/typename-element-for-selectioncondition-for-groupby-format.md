---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName, élément pour SelectionCondition pour GroupBy (Format)
description: TypeName, élément pour SelectionCondition pour GroupBy (Format)
ms.openlocfilehash: 096d2355e113a7e44cc6ae31ea23efc3f01080a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664624"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="0f6cf-103">TypeName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0f6cf-103">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="0f6cf-104">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="0f6cf-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="0f6cf-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="0f6cf-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0f6cf-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour View (format) CustomControl, élément pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour l’élément GroupBy (format) pour l’élément CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0f6cf-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f6cf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f6cf-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f6cf-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0f6cf-108">Attributes and Elements</span></span>

<span data-ttu-id="0f6cf-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="0f6cf-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f6cf-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0f6cf-110">Attributes</span></span>

<span data-ttu-id="0f6cf-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0f6cf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f6cf-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0f6cf-112">Child Elements</span></span>

<span data-ttu-id="0f6cf-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0f6cf-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0f6cf-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0f6cf-114">Parent Elements</span></span>

|<span data-ttu-id="0f6cf-115">Élément</span><span class="sxs-lookup"><span data-stu-id="0f6cf-115">Element</span></span>|<span data-ttu-id="0f6cf-116">Description</span><span class="sxs-lookup"><span data-stu-id="0f6cf-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f6cf-117">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0f6cf-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0f6cf-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="0f6cf-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0f6cf-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="0f6cf-119">Text Value</span></span>

<span data-ttu-id="0f6cf-120">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="0f6cf-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f6cf-121">Notes</span><span class="sxs-lookup"><span data-stu-id="0f6cf-121">Remarks</span></span>

<span data-ttu-id="0f6cf-122">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="0f6cf-122">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="0f6cf-123">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0f6cf-123">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f6cf-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f6cf-124">See Also</span></span>

[<span data-ttu-id="0f6cf-125">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0f6cf-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0f6cf-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f6cf-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
