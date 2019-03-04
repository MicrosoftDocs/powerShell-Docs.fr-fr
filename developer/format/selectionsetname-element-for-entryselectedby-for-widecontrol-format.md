---
title: Élément SelectionSetName pour EntrySelectedBy pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856795"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="5964b-102">SelectionSetName, élément pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5964b-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="5964b-103">Spécifie un ensemble d’objets .NET pour la définition.</span><span class="sxs-lookup"><span data-stu-id="5964b-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="5964b-104">La définition est utilisée chaque fois qu’un de ces objets s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5964b-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="5964b-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) élément WideEntries (Format) élément WideEntry (Format) EntrySelectedBy élément pour l’élément de SelectionSetName WideEntry (Format) pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5964b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5964b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5964b-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5964b-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5964b-107">Attributes and Elements</span></span>

<span data-ttu-id="5964b-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="5964b-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5964b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5964b-109">Attributes</span></span>

<span data-ttu-id="5964b-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5964b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5964b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5964b-111">Child Elements</span></span>

<span data-ttu-id="5964b-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5964b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5964b-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5964b-113">Parent Elements</span></span>

|<span data-ttu-id="5964b-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5964b-114">Element</span></span>|<span data-ttu-id="5964b-115">Description</span><span class="sxs-lookup"><span data-stu-id="5964b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5964b-116">Élément EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5964b-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="5964b-117">Définit les types .NET qui utilisent cette entrée large ou la condition qui doit exister pour cette entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5964b-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5964b-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="5964b-118">Text Value</span></span>

<span data-ttu-id="5964b-119">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="5964b-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="5964b-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="5964b-120">Remarks</span></span>

<span data-ttu-id="5964b-121">Chaque définition doit spécifier un nom de type, jeu de sélection ou le critère de sélection.</span><span class="sxs-lookup"><span data-stu-id="5964b-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="5964b-122">Sélection jeux sont généralement utilisés lorsque vous souhaitez définir un groupe d’objets qui sont utilisés dans plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="5964b-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="5964b-123">Par exemple, vous souhaiterez peut-être créer une vue de table et une vue de liste pour le même ensemble d’objets.</span><span class="sxs-lookup"><span data-stu-id="5964b-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="5964b-124">Pour plus d’informations sur la définition de jeux de sélection, consultez [définition définit des objets pour une vue](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5964b-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="5964b-125">Pour plus d’informations sur d’autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="5964b-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5964b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5964b-126">See Also</span></span>

[<span data-ttu-id="5964b-127">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="5964b-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5964b-128">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="5964b-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="5964b-129">Élément EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5964b-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="5964b-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5964b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
