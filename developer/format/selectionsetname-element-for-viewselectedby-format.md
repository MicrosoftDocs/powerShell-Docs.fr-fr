---
title: Élément SelectionSetName pour ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858335"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="f343b-102">SelectionSetName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f343b-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="f343b-103">Spécifie un ensemble d’objets .NET qui sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="f343b-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="f343b-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément ViewSelectedBy (Format) SelectionSetName élément de configuration pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f343b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f343b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f343b-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f343b-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="f343b-106">Attributes and Elements</span></span>

<span data-ttu-id="f343b-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="f343b-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f343b-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="f343b-108">Attributes</span></span>

<span data-ttu-id="f343b-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f343b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f343b-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f343b-110">Child Elements</span></span>

<span data-ttu-id="f343b-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="f343b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f343b-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f343b-112">Parent Elements</span></span>

|<span data-ttu-id="f343b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="f343b-113">Element</span></span>|<span data-ttu-id="f343b-114">Description</span><span class="sxs-lookup"><span data-stu-id="f343b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f343b-115">Élément ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f343b-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="f343b-116">Définit les objets .NET qui sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="f343b-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f343b-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="f343b-117">Text Value</span></span>

<span data-ttu-id="f343b-118">Spécifiez le nom de l’ensemble de sélection qui est défini par le `Name` élément pour l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="f343b-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f343b-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="f343b-119">Remarks</span></span>

<span data-ttu-id="f343b-120">Vous pouvez utiliser des jeux de sélection lorsque vous avez un ensemble d’objets connexes que vous souhaitez faire référence à l’aide d’un nom unique, comme un ensemble d’objets qui sont liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="f343b-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="f343b-121">Pour plus d’informations sur la définition et référencement des jeux de sélection, consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f343b-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="f343b-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="f343b-122">Example</span></span>

<span data-ttu-id="f343b-123">L’exemple suivant montre comment spécifier une jeu de sélection pour un affichage de liste.</span><span class="sxs-lookup"><span data-stu-id="f343b-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="f343b-124">Le même schéma est utilisé pour les vues table, large et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f343b-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="f343b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f343b-125">See Also</span></span>

[<span data-ttu-id="f343b-126">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="f343b-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f343b-127">Élément ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f343b-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="f343b-128">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f343b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
