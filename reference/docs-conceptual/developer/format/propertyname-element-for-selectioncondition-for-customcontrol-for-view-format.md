---
title: PropertyName, élément de SelectionCondition pour CustomControl pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: aa3955b84b8de9901f394e8108f31440fcb6c942
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780795"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="8aae8-102">PropertyName, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="8aae8-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="8aae8-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="8aae8-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="8aae8-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8aae8-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="8aae8-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8aae8-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="8aae8-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour CustomControl pour l’élément View (format) CustomItem pour CustomEntry pour CustomControl pour View (format) EntrySelectedBy, élément pour CustomEntry pour CustomControl pour View (format) SelectionCondition element pour EntrySelectedBy pour CustomControl pour l’élément View (format) PropertyName pour SelectionCondition pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8aae8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8aae8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8aae8-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8aae8-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8aae8-108">Attributes and Elements</span></span>

<span data-ttu-id="8aae8-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="8aae8-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8aae8-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="8aae8-110">Attributes</span></span>

<span data-ttu-id="8aae8-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8aae8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8aae8-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8aae8-112">Child Elements</span></span>

<span data-ttu-id="8aae8-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8aae8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8aae8-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8aae8-114">Parent Elements</span></span>

|<span data-ttu-id="8aae8-115">Élément</span><span class="sxs-lookup"><span data-stu-id="8aae8-115">Element</span></span>|<span data-ttu-id="8aae8-116">Description</span><span class="sxs-lookup"><span data-stu-id="8aae8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8aae8-117">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8aae8-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="8aae8-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="8aae8-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8aae8-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="8aae8-119">Text Value</span></span>

<span data-ttu-id="8aae8-120">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="8aae8-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="8aae8-121">Notes</span><span class="sxs-lookup"><span data-stu-id="8aae8-121">Remarks</span></span>

<span data-ttu-id="8aae8-122">La condition de sélection doit spécifier au moins un nom de propriété ou un script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="8aae8-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="8aae8-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8aae8-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8aae8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8aae8-124">See Also</span></span>

[<span data-ttu-id="8aae8-125">Élément SelectionCondition pour EntrySelectedBy pour CustomControl pour View (format)</span><span class="sxs-lookup"><span data-stu-id="8aae8-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="8aae8-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="8aae8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
