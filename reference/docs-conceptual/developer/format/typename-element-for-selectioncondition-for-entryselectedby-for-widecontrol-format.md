---
title: Élément TypeName pour SelectionCondition pour EntrySelectedBy pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5021f665b994581f9ff982e13af922d7940ebf2b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783311"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="63147-102">TypeName, élément pour SelectionCondition pour EntrySelectedBy pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="63147-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="63147-103">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="63147-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="63147-104">Lorsque ce type est présent, la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="63147-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="63147-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry élément (format) élément EntrySelectedBy pour WideEntry (format) élément SelectionCondition pour EntrySelectedBy pour WideEntry (format) élément TypeName pour SelectionCondition pour EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="63147-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63147-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63147-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63147-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="63147-107">Attributes and Elements</span></span>

<span data-ttu-id="63147-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="63147-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="63147-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="63147-109">Attributes</span></span>

<span data-ttu-id="63147-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="63147-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63147-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="63147-111">Child Elements</span></span>

<span data-ttu-id="63147-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="63147-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="63147-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="63147-113">Parent Elements</span></span>

|<span data-ttu-id="63147-114">Élément</span><span class="sxs-lookup"><span data-stu-id="63147-114">Element</span></span>|<span data-ttu-id="63147-115">Description</span><span class="sxs-lookup"><span data-stu-id="63147-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63147-116">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="63147-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="63147-117">Définit la condition qui doit exister pour cette grande entrée à utiliser.</span><span class="sxs-lookup"><span data-stu-id="63147-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="63147-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="63147-118">Text Value</span></span>

<span data-ttu-id="63147-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="63147-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="63147-120">Notes</span><span class="sxs-lookup"><span data-stu-id="63147-120">Remarks</span></span>

<span data-ttu-id="63147-121">La condition de sélection peut spécifier un type .NET ou un jeu de sélection, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="63147-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="63147-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="63147-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="63147-123">Pour plus d’informations sur les autres composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="63147-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63147-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63147-124">See Also</span></span>

[<span data-ttu-id="63147-125">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="63147-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="63147-126">Définition des conditions d’affichage des données</span><span class="sxs-lookup"><span data-stu-id="63147-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="63147-127">Élément SelectionCondition pour EntrySelectedBy pour WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="63147-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="63147-128">SelectionSetName, élément pour SelectionCondition pour EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="63147-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="63147-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="63147-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
