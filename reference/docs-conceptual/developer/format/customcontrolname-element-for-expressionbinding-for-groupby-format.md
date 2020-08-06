---
title: Élément CustomControlName pour ExpressionBinding pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 06e612b25accf81467108ca48500943153efd575
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785997"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="e6de1-102">CustomControlName, élément pour ExpressionBinding pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e6de1-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="e6de1-103">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="e6de1-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="e6de1-104">Cet élément est utilisé lors de la définition du mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="e6de1-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e6de1-105">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour la vue (format) CustomControl, élément de GroupBy (format) élément CustomEntries pour CustomControl pour la clause GroupBy (format) CustomEntry élément pour CustomControl pour GroupBy (format) CustomItem élément pour CustomEntry pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e6de1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6de1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6de1-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6de1-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e6de1-107">Attributes and Elements</span></span>

<span data-ttu-id="e6de1-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="e6de1-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6de1-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="e6de1-109">Attributes</span></span>

<span data-ttu-id="e6de1-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e6de1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6de1-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e6de1-111">Child Elements</span></span>

<span data-ttu-id="e6de1-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e6de1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e6de1-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e6de1-113">Parent Elements</span></span>

|<span data-ttu-id="e6de1-114">Élément</span><span class="sxs-lookup"><span data-stu-id="e6de1-114">Element</span></span>|<span data-ttu-id="e6de1-115">Description</span><span class="sxs-lookup"><span data-stu-id="e6de1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6de1-116">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e6de1-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e6de1-117">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6de1-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e6de1-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="e6de1-118">Text Value</span></span>

<span data-ttu-id="e6de1-119">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6de1-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6de1-120">Notes</span><span class="sxs-lookup"><span data-stu-id="e6de1-120">Remarks</span></span>

<span data-ttu-id="e6de1-121">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="e6de1-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="e6de1-122">Les éléments suivants spécifient les noms de ces contrôles :</span><span class="sxs-lookup"><span data-stu-id="e6de1-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="e6de1-123">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e6de1-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="e6de1-124">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e6de1-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="e6de1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6de1-125">See Also</span></span>

[<span data-ttu-id="e6de1-126">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e6de1-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="e6de1-127">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="e6de1-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="e6de1-128">ExpressionBinding, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e6de1-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e6de1-129">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="e6de1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
