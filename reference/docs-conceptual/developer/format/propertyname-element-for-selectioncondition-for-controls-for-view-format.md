---
title: Élément PropertyName pour SelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 251fc129896cfa4a6255330e23854b014675ac5f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780812"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="42fd9-102">PropertyName, élément pour SelectionCondition pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="42fd9-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="42fd9-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="42fd9-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="42fd9-104">Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true` , la condition est remplie et l’entrée est utilisée.</span><span class="sxs-lookup"><span data-stu-id="42fd9-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="42fd9-105">Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.</span><span class="sxs-lookup"><span data-stu-id="42fd9-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="42fd9-106">Élément de configuration (format) élément ViewDefinitions (format) vue, élément (format) contrôle l’élément (format) contrôle élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour View (format) CustomEntries element pour CustomControl pour les contrôles pour View (format) élément CustomEntry pour CustomEntries pour les contrôles de l’élément View (format) EntrySelectedBy pour CustomEntry pour les contrôles pour l’élément View (format) SelectionCondition pour les contrôles pour l’élément View (format) PropertyName pour EntrySelectedBy pour les contrôles pour View (format)</span><span class="sxs-lookup"><span data-stu-id="42fd9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42fd9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42fd9-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42fd9-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="42fd9-108">Attributes and Elements</span></span>

<span data-ttu-id="42fd9-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="42fd9-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42fd9-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="42fd9-110">Attributes</span></span>

<span data-ttu-id="42fd9-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="42fd9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42fd9-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="42fd9-112">Child Elements</span></span>

<span data-ttu-id="42fd9-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="42fd9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="42fd9-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="42fd9-114">Parent Elements</span></span>

|<span data-ttu-id="42fd9-115">Élément</span><span class="sxs-lookup"><span data-stu-id="42fd9-115">Element</span></span>|<span data-ttu-id="42fd9-116">Description</span><span class="sxs-lookup"><span data-stu-id="42fd9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42fd9-117">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="42fd9-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="42fd9-118">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="42fd9-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="42fd9-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="42fd9-119">Text Value</span></span>

<span data-ttu-id="42fd9-120">Spécifiez le nom de la propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="42fd9-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="42fd9-121">Notes</span><span class="sxs-lookup"><span data-stu-id="42fd9-121">Remarks</span></span>

<span data-ttu-id="42fd9-122">La condition de sélection doit spécifier au moins un nom de propriété ou un script, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="42fd9-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="42fd9-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="42fd9-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42fd9-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42fd9-124">See Also</span></span>

[<span data-ttu-id="42fd9-125">SelectionCondition, élément pour EntrySelectedBy pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="42fd9-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="42fd9-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="42fd9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
