---
title: Élément PropertyName pour SelectionCondition pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853185"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="70ced-102">PropertyName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="70ced-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="70ced-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="70ced-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="70ced-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et que la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="70ced-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="70ced-105">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="70ced-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="70ced-106">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de EntrySelectedBy GroupBy (Format) pour CustomEntry d’élément de SelectionCondition GroupBy (Format) pour EntrySelectedBy d’élément de PropertyName GroupBy (Format) pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="70ced-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70ced-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70ced-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70ced-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="70ced-108">Attributes and Elements</span></span>

<span data-ttu-id="70ced-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="70ced-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70ced-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="70ced-110">Attributes</span></span>

<span data-ttu-id="70ced-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="70ced-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70ced-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="70ced-112">Child Elements</span></span>

<span data-ttu-id="70ced-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="70ced-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70ced-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="70ced-114">Parent Elements</span></span>

|<span data-ttu-id="70ced-115">Élément</span><span class="sxs-lookup"><span data-stu-id="70ced-115">Element</span></span>|<span data-ttu-id="70ced-116">Description</span><span class="sxs-lookup"><span data-stu-id="70ced-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70ced-117">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="70ced-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="70ced-118">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="70ced-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="70ced-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="70ced-119">Text Value</span></span>

<span data-ttu-id="70ced-120">Spécifiez le nom de propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="70ced-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="70ced-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="70ced-121">Remarks</span></span>

<span data-ttu-id="70ced-122">La condition de sélection doit spécifier un nom d’un propriété minimum ou un script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="70ced-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="70ced-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="70ced-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70ced-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70ced-124">See Also</span></span>

[<span data-ttu-id="70ced-125">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="70ced-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="70ced-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="70ced-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
