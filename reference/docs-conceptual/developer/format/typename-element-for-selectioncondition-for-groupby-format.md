---
title: Élément TypeName pour SelectionCondition pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ea1e0cb50c3a749f6c26d13fff4b001240ce6b95
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772550"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="289d4-102">TypeName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="289d4-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="289d4-103">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="289d4-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="289d4-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="289d4-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="289d4-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour View (format) CustomControl, élément pour GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour l’élément GroupBy (format) pour l’élément CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="289d4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="289d4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="289d4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="289d4-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="289d4-107">Attributes and Elements</span></span>

<span data-ttu-id="289d4-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="289d4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="289d4-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="289d4-109">Attributes</span></span>

<span data-ttu-id="289d4-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="289d4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="289d4-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="289d4-111">Child Elements</span></span>

<span data-ttu-id="289d4-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="289d4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="289d4-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="289d4-113">Parent Elements</span></span>

|<span data-ttu-id="289d4-114">Élément</span><span class="sxs-lookup"><span data-stu-id="289d4-114">Element</span></span>|<span data-ttu-id="289d4-115">Description</span><span class="sxs-lookup"><span data-stu-id="289d4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="289d4-116">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="289d4-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="289d4-117">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="289d4-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="289d4-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="289d4-118">Text Value</span></span>

<span data-ttu-id="289d4-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="289d4-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="289d4-120">Notes</span><span class="sxs-lookup"><span data-stu-id="289d4-120">Remarks</span></span>

<span data-ttu-id="289d4-121">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier l' `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="289d4-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="289d4-122">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="289d4-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="289d4-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="289d4-123">See Also</span></span>

[<span data-ttu-id="289d4-124">SelectionCondition, élément pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="289d4-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="289d4-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="289d4-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
