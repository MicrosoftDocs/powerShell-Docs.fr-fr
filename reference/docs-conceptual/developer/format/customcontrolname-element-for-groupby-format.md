---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControlName, élément pour GroupBy (Format)
description: CustomControlName, élément pour GroupBy (Format)
ms.openlocfilehash: 03664fe4d5559312e2720a3892493c90c15f7501
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655414"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="c41ec-103">CustomControlName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c41ec-103">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="c41ec-104">Spécifie le nom d’un contrôle personnalisé utilisé pour afficher le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="c41ec-104">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="c41ec-105">Cet élément est utilisé lors de la définition d’une vue de contrôle de table, de liste, étendue ou personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c41ec-105">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="c41ec-106">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément View (format) CustomControlName de GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c41ec-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c41ec-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c41ec-107">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c41ec-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c41ec-108">Attributes and Elements</span></span>

<span data-ttu-id="c41ec-109">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de l' `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="c41ec-109">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c41ec-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="c41ec-110">Attributes</span></span>

<span data-ttu-id="c41ec-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c41ec-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c41ec-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c41ec-112">Child Elements</span></span>

<span data-ttu-id="c41ec-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c41ec-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c41ec-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c41ec-114">Parent Elements</span></span>

|<span data-ttu-id="c41ec-115">Élément</span><span class="sxs-lookup"><span data-stu-id="c41ec-115">Element</span></span>|<span data-ttu-id="c41ec-116">Description</span><span class="sxs-lookup"><span data-stu-id="c41ec-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c41ec-117">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c41ec-117">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="c41ec-118">Définit la manière dont Windows PowerShell affiche un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="c41ec-118">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c41ec-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="c41ec-119">Text Value</span></span>

<span data-ttu-id="c41ec-120">Spécifiez le nom du contrôle personnalisé utilisé pour afficher un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="c41ec-120">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="c41ec-121">Notes</span><span class="sxs-lookup"><span data-stu-id="c41ec-121">Remarks</span></span>

<span data-ttu-id="c41ec-122">Vous pouvez créer des contrôles communs qui peuvent être utilisés par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisés par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="c41ec-122">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="c41ec-123">Les éléments suivants spécifient les noms de ces contrôles personnalisés :</span><span class="sxs-lookup"><span data-stu-id="c41ec-123">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="c41ec-124">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="c41ec-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="c41ec-125">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c41ec-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="c41ec-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c41ec-126">See Also</span></span>

[<span data-ttu-id="c41ec-127">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c41ec-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="c41ec-128">Name, élément pour Control pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="c41ec-128">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="c41ec-129">Name, élément pour Control pour Controls pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="c41ec-129">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c41ec-130">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="c41ec-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
