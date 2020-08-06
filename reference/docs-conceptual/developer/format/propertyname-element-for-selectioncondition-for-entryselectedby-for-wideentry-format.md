---
title: PropertyName, élément de SelectionCondition pour EntrySelectedBy pour WideEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ca2106dbbd8da345e71e83a3ead3cf7a1cb44cb4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773111"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="9621f-102">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9621f-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="9621f-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="9621f-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="9621f-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="9621f-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="9621f-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément SelectionCondition pour EntrySelectedBy (format) NomPropriété, élément pour WideEntry pour SelectionCondition (format)</span><span class="sxs-lookup"><span data-stu-id="9621f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9621f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9621f-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9621f-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9621f-107">Attributes and Elements</span></span>

<span data-ttu-id="9621f-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="9621f-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9621f-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="9621f-109">Attributes</span></span>

<span data-ttu-id="9621f-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9621f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9621f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9621f-111">Child Elements</span></span>

<span data-ttu-id="9621f-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9621f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9621f-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9621f-113">Parent Elements</span></span>

|<span data-ttu-id="9621f-114">Élément</span><span class="sxs-lookup"><span data-stu-id="9621f-114">Element</span></span>|<span data-ttu-id="9621f-115">Description</span><span class="sxs-lookup"><span data-stu-id="9621f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9621f-116">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9621f-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9621f-117">Définit la condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="9621f-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9621f-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="9621f-118">Text Value</span></span>

<span data-ttu-id="9621f-119">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="9621f-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="9621f-120">Notes</span><span class="sxs-lookup"><span data-stu-id="9621f-120">Remarks</span></span>

<span data-ttu-id="9621f-121">La condition de sélection doit spécifier au moins un nom de propriété ou un script à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="9621f-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="9621f-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9621f-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9621f-123">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9621f-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9621f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9621f-124">See Also</span></span>

[<span data-ttu-id="9621f-125">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="9621f-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9621f-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="9621f-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9621f-127">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9621f-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9621f-128">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9621f-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9621f-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="9621f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
