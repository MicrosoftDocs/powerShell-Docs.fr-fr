---
title: Élément CustomControlName pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066536"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="522d6-102">CustomControlName, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="522d6-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="522d6-103">Spécifie le nom d’un contrôle personnalisé qui est utilisé pour afficher le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="522d6-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="522d6-104">Cet élément est utilisé lors de la définition d’une table, la liste, l’affichage de contrôle de larges ou personnalisé.</span><span class="sxs-lookup"><span data-stu-id="522d6-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="522d6-105">Configuration élément (Format) élément ViewDefinitions (Format) (Format) d’élément GroupBy élément d’affichage pour élément d’affichage (Format) de CustomControlName de GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="522d6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="522d6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="522d6-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="522d6-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="522d6-107">Attributes and Elements</span></span>

<span data-ttu-id="522d6-108">Les sections suivantes décrivent les attributs, les éléments enfants et les éléments parents de la `CustomControlName` élément.</span><span class="sxs-lookup"><span data-stu-id="522d6-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="522d6-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="522d6-109">Attributes</span></span>

<span data-ttu-id="522d6-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="522d6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="522d6-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="522d6-111">Child Elements</span></span>

<span data-ttu-id="522d6-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="522d6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="522d6-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="522d6-113">Parent Elements</span></span>

|<span data-ttu-id="522d6-114">Élément</span><span class="sxs-lookup"><span data-stu-id="522d6-114">Element</span></span>|<span data-ttu-id="522d6-115">Description</span><span class="sxs-lookup"><span data-stu-id="522d6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="522d6-116">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="522d6-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="522d6-117">Définit la façon dont Windows PowerShell affiche un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="522d6-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="522d6-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="522d6-118">Text Value</span></span>

<span data-ttu-id="522d6-119">Spécifiez le nom du contrôle personnalisé qui est utilisé pour afficher un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="522d6-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="522d6-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="522d6-120">Remarks</span></span>

<span data-ttu-id="522d6-121">Vous pouvez créer des contrôles communs qui peuvent être utilisées par toutes les vues d’un fichier de mise en forme, et vous pouvez créer des contrôles d’affichage qui peuvent être utilisées par une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="522d6-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="522d6-122">Les éléments suivants spécifient les noms de ces contrôles personnalisés :</span><span class="sxs-lookup"><span data-stu-id="522d6-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="522d6-123">Name, élément pour le contrôle pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="522d6-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="522d6-124">Name, élément pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="522d6-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="522d6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="522d6-125">See Also</span></span>

[<span data-ttu-id="522d6-126">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="522d6-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="522d6-127">Name, élément pour le contrôle pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="522d6-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="522d6-128">Name, élément pour le contrôle pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="522d6-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="522d6-129">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="522d6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
