---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)
description: CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)
ms.openlocfilehash: 24b27428c07d7178f0069f6d0e5b7ffc555efe34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666805"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="808cc-103">CustomControlName, élément pour ExpressionBinding pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="808cc-103">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="808cc-104">Spécifie le nom d’un contrôle commun ou d’un contrôle View.</span><span class="sxs-lookup"><span data-stu-id="808cc-104">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="808cc-105">Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="808cc-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="808cc-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément CustomControl pour l’élément View (format) CustomEntries pour CustomControl pour la vue (format) élément CustomEntry pour CustomEntries pour l’élément View (format) CustomItem pour CustomEntry pour l’élément View (format) ExpressionBinding pour CustomItem (format) CustomControlName élément pour la liaison d’expression pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="808cc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="808cc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="808cc-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="808cc-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="808cc-108">Attributes and Elements</span></span>

<span data-ttu-id="808cc-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="808cc-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="808cc-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="808cc-110">Attributes</span></span>

<span data-ttu-id="808cc-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="808cc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="808cc-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="808cc-112">Child Elements</span></span>

<span data-ttu-id="808cc-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="808cc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="808cc-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="808cc-114">Parent Elements</span></span>

|<span data-ttu-id="808cc-115">Élément</span><span class="sxs-lookup"><span data-stu-id="808cc-115">Element</span></span>|<span data-ttu-id="808cc-116">Description</span><span class="sxs-lookup"><span data-stu-id="808cc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="808cc-117">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="808cc-117">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="808cc-118">Définit les données affichées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="808cc-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="808cc-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="808cc-119">Text Value</span></span>

<span data-ttu-id="808cc-120">Spécifiez le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="808cc-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="808cc-121">Notes</span><span class="sxs-lookup"><span data-stu-id="808cc-121">Remarks</span></span>

<span data-ttu-id="808cc-122">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="808cc-122">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="808cc-123">Les noms de ces contrôles sont spécifiés par les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="808cc-123">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="808cc-124">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="808cc-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="808cc-125">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="808cc-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="808cc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="808cc-126">See Also</span></span>

[<span data-ttu-id="808cc-127">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="808cc-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="808cc-128">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="808cc-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="808cc-129">Élément ExpressionBinding pour CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="808cc-129">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="808cc-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="808cc-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
