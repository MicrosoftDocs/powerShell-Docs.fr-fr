---
title: Élément TypeName pour SelectionCondition pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083771"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="ad4fe-102">TypeName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ad4fe-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="ad4fe-103">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="ad4fe-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="ad4fe-104">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="ad4fe-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ad4fe-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de EntrySelectedBy GroupBy (Format) pour CustomEntry d’élément de SelectionCondition GroupBy (Format) pour EntrySelectedBy d’élément de TypeName GroupBy (Format) pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ad4fe-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad4fe-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad4fe-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad4fe-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="ad4fe-107">Attributes and Elements</span></span>

<span data-ttu-id="ad4fe-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="ad4fe-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad4fe-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ad4fe-109">Attributes</span></span>

<span data-ttu-id="ad4fe-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ad4fe-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad4fe-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ad4fe-111">Child Elements</span></span>

<span data-ttu-id="ad4fe-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ad4fe-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ad4fe-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ad4fe-113">Parent Elements</span></span>

|<span data-ttu-id="ad4fe-114">Élément</span><span class="sxs-lookup"><span data-stu-id="ad4fe-114">Element</span></span>|<span data-ttu-id="ad4fe-115">Description</span><span class="sxs-lookup"><span data-stu-id="ad4fe-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad4fe-116">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ad4fe-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="ad4fe-117">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ad4fe-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ad4fe-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="ad4fe-118">Text Value</span></span>

<span data-ttu-id="ad4fe-119">Spécifiez le nom qualifié complet du type .NET, tel que `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="ad4fe-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad4fe-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="ad4fe-120">Remarks</span></span>

<span data-ttu-id="ad4fe-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="ad4fe-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="ad4fe-122">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ad4fe-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad4fe-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad4fe-123">See Also</span></span>

[<span data-ttu-id="ad4fe-124">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ad4fe-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="ad4fe-125">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad4fe-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
