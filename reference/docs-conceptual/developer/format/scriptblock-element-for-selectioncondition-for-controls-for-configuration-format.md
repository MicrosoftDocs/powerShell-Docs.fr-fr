---
title: Élément ScriptBlock pour SelectionCondition pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 24584aacd7869abd3dcfc6ff546e6dea4c2c04fc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785436"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="a3edc-102">ScriptBlock, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a3edc-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a3edc-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="a3edc-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="a3edc-104">Lorsque ce script est évalué à `true` , la condition est remplie et la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a3edc-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="a3edc-105">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="a3edc-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a3edc-106">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour la configuration (format) CustomEntry, élément de CustomControl pour les contrôles de configuration (format) élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) élément SelectionCondition pour EntrySelectedBy pour les contrôles pour la configuration (format) élément ScriptBlock pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a3edc-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a3edc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3edc-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a3edc-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a3edc-108">Attributes and Elements</span></span>

<span data-ttu-id="a3edc-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="a3edc-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a3edc-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a3edc-110">Attributes</span></span>

<span data-ttu-id="a3edc-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a3edc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a3edc-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a3edc-112">Child Elements</span></span>

<span data-ttu-id="a3edc-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a3edc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a3edc-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a3edc-114">Parent Elements</span></span>

|<span data-ttu-id="a3edc-115">Élément</span><span class="sxs-lookup"><span data-stu-id="a3edc-115">Element</span></span>|<span data-ttu-id="a3edc-116">Description</span><span class="sxs-lookup"><span data-stu-id="a3edc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3edc-117">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a3edc-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="a3edc-118">Définit une condition qui doit exister pour que la définition de contrôle commun soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a3edc-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a3edc-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="a3edc-119">Text Value</span></span>

<span data-ttu-id="a3edc-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="a3edc-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3edc-121">Notes</span><span class="sxs-lookup"><span data-stu-id="a3edc-121">Remarks</span></span>

<span data-ttu-id="a3edc-122">La condition de sélection doit spécifier au moins un script ou un nom de propriété à évaluer, mais ne peut pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="a3edc-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="a3edc-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a3edc-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a3edc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3edc-124">See Also</span></span>

[<span data-ttu-id="a3edc-125">SelectionCondition, élément pour EntrySelectedBy pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a3edc-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="a3edc-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3edc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
