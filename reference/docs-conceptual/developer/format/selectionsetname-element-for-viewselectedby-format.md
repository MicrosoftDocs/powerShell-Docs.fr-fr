---
title: Élément SelectionSetName pour ViewSelectedBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368258"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="70fe2-102">SelectionSetName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="70fe2-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="70fe2-103">Spécifie un jeu d’objets .NET qui sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="70fe2-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="70fe2-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément ViewSelectedBy (format) élément SelectionSetName pour ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="70fe2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70fe2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70fe2-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70fe2-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="70fe2-106">Attributes and Elements</span></span>

<span data-ttu-id="70fe2-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="70fe2-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70fe2-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="70fe2-108">Attributes</span></span>

<span data-ttu-id="70fe2-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="70fe2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70fe2-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="70fe2-110">Child Elements</span></span>

<span data-ttu-id="70fe2-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="70fe2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70fe2-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="70fe2-112">Parent Elements</span></span>

|<span data-ttu-id="70fe2-113">Élément</span><span class="sxs-lookup"><span data-stu-id="70fe2-113">Element</span></span>|<span data-ttu-id="70fe2-114">Description</span><span class="sxs-lookup"><span data-stu-id="70fe2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70fe2-115">Élément ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="70fe2-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="70fe2-116">Définit les objets .NET affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="70fe2-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="70fe2-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="70fe2-117">Text Value</span></span>

<span data-ttu-id="70fe2-118">Spécifiez le nom du jeu de sélection défini par l’élément `Name` pour le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="70fe2-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="70fe2-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="70fe2-119">Remarks</span></span>

<span data-ttu-id="70fe2-120">Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="70fe2-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="70fe2-121">Pour plus d’informations sur la définition et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="70fe2-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="70fe2-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="70fe2-122">Example</span></span>

<span data-ttu-id="70fe2-123">L’exemple suivant montre comment spécifier un jeu de sélection pour un mode liste.</span><span class="sxs-lookup"><span data-stu-id="70fe2-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="70fe2-124">Le même schéma est utilisé pour les vues de table, larges et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="70fe2-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="70fe2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70fe2-125">See Also</span></span>

[<span data-ttu-id="70fe2-126">Définition des jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="70fe2-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="70fe2-127">Élément ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="70fe2-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="70fe2-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="70fe2-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
