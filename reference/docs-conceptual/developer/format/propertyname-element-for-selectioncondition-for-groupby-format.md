---
title: PropertyName, élément de SelectionCondition pour GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364948"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="499f5-102">PropertyName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="499f5-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="499f5-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="499f5-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="499f5-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="499f5-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="499f5-105">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="499f5-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="499f5-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControl pour GroupBy (format) élément CustomEntries pour CustomControl pour l’élément CustomEntry GroupBy (format) pour CustomControl pour GroupBy (format) élément EntrySelectedBy pour CustomEntry pour GroupBy (format) élément SelectionCondition pour EntrySelectedBy pour l’élément GroupBy (format) PropertyName pour SelectionCondition pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="499f5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="499f5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="499f5-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="499f5-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="499f5-108">Attributes and Elements</span></span>

<span data-ttu-id="499f5-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="499f5-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="499f5-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="499f5-110">Attributes</span></span>

<span data-ttu-id="499f5-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="499f5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="499f5-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="499f5-112">Child Elements</span></span>

<span data-ttu-id="499f5-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="499f5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="499f5-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="499f5-114">Parent Elements</span></span>

|<span data-ttu-id="499f5-115">Élément</span><span class="sxs-lookup"><span data-stu-id="499f5-115">Element</span></span>|<span data-ttu-id="499f5-116">Description</span><span class="sxs-lookup"><span data-stu-id="499f5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="499f5-117">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="499f5-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="499f5-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="499f5-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="499f5-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="499f5-119">Text Value</span></span>

<span data-ttu-id="499f5-120">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="499f5-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="499f5-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="499f5-121">Remarks</span></span>

<span data-ttu-id="499f5-122">La condition de sélection doit spécifier au moins un nom de propriété ou un script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="499f5-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="499f5-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="499f5-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="499f5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="499f5-124">See Also</span></span>

[<span data-ttu-id="499f5-125">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="499f5-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="499f5-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="499f5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
