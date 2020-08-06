---
title: Élément SelectionSetName pour ViewSelectedBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6410b463bcb00d2758849c2f7e13cd839277e50
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772601"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="120e5-102">SelectionSetName, élément pour ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="120e5-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="120e5-103">Spécifie un jeu d’objets .NET qui sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="120e5-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="120e5-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément ViewSelectedBy (format) élément SelectionSetName pour ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="120e5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="120e5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="120e5-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="120e5-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="120e5-106">Attributes and Elements</span></span>

<span data-ttu-id="120e5-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="120e5-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="120e5-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="120e5-108">Attributes</span></span>

<span data-ttu-id="120e5-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="120e5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="120e5-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="120e5-110">Child Elements</span></span>

<span data-ttu-id="120e5-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="120e5-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="120e5-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="120e5-112">Parent Elements</span></span>

|<span data-ttu-id="120e5-113">Élément</span><span class="sxs-lookup"><span data-stu-id="120e5-113">Element</span></span>|<span data-ttu-id="120e5-114">Description</span><span class="sxs-lookup"><span data-stu-id="120e5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="120e5-115">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="120e5-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="120e5-116">Définit les objets .NET affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="120e5-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="120e5-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="120e5-117">Text Value</span></span>

<span data-ttu-id="120e5-118">Spécifiez le nom du jeu de sélection défini par l' `Name` élément pour le jeu de sélection.</span><span class="sxs-lookup"><span data-stu-id="120e5-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="120e5-119">Notes</span><span class="sxs-lookup"><span data-stu-id="120e5-119">Remarks</span></span>

<span data-ttu-id="120e5-120">Vous pouvez utiliser des jeux de sélection quand vous avez un ensemble d’objets connexes que vous souhaitez référencer à l’aide d’un nom unique, tel qu’un ensemble d’objets liés par héritage.</span><span class="sxs-lookup"><span data-stu-id="120e5-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="120e5-121">Pour plus d’informations sur la définition et le référencement des jeux de sélection, consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="120e5-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="120e5-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="120e5-122">Example</span></span>

<span data-ttu-id="120e5-123">L’exemple suivant montre comment spécifier un jeu de sélection pour un mode liste.</span><span class="sxs-lookup"><span data-stu-id="120e5-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="120e5-124">Le même schéma est utilisé pour les vues de table, larges et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="120e5-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="120e5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="120e5-125">See Also</span></span>

[<span data-ttu-id="120e5-126">Définition de jeux de sélections</span><span class="sxs-lookup"><span data-stu-id="120e5-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="120e5-127">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="120e5-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="120e5-128">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="120e5-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
