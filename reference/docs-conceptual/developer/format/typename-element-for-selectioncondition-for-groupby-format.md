---
title: Élément TypeName pour SelectionCondition pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361478"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="c28f5-102">TypeName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c28f5-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="c28f5-103">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="c28f5-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="c28f5-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="c28f5-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c28f5-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément EntrySelectedBy pour CustomEntry pour GroupBy (format) élément SelectionCondition pour EntrySelectedBy pour l’élément GroupBy (format) TypeName pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c28f5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c28f5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c28f5-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c28f5-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="c28f5-107">Attributes and Elements</span></span>

<span data-ttu-id="c28f5-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="c28f5-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c28f5-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="c28f5-109">Attributes</span></span>

<span data-ttu-id="c28f5-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c28f5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c28f5-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c28f5-111">Child Elements</span></span>

<span data-ttu-id="c28f5-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="c28f5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c28f5-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c28f5-113">Parent Elements</span></span>

|<span data-ttu-id="c28f5-114">Élément</span><span class="sxs-lookup"><span data-stu-id="c28f5-114">Element</span></span>|<span data-ttu-id="c28f5-115">Description</span><span class="sxs-lookup"><span data-stu-id="c28f5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c28f5-116">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c28f5-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="c28f5-117">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="c28f5-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c28f5-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="c28f5-118">Text Value</span></span>

<span data-ttu-id="c28f5-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="c28f5-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c28f5-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="c28f5-120">Remarks</span></span>

<span data-ttu-id="c28f5-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="c28f5-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="c28f5-122">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c28f5-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c28f5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c28f5-123">See Also</span></span>

[<span data-ttu-id="c28f5-124">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c28f5-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="c28f5-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c28f5-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
