---
title: Élément WideEntries pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361428"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="21e81-102">WideEntries, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="21e81-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="21e81-103">Fournit les définitions de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="21e81-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="21e81-104">La vue étendue doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="21e81-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="21e81-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément WideControl (format) WideEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="21e81-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21e81-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21e81-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="21e81-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="21e81-107">Attributes and Elements</span></span>

<span data-ttu-id="21e81-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `WideEntries`.</span><span class="sxs-lookup"><span data-stu-id="21e81-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="21e81-109">Au moins un élément enfant doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="21e81-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="21e81-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="21e81-110">Attributes</span></span>

<span data-ttu-id="21e81-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="21e81-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21e81-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="21e81-112">Child Elements</span></span>

|<span data-ttu-id="21e81-113">Élément</span><span class="sxs-lookup"><span data-stu-id="21e81-113">Element</span></span>|<span data-ttu-id="21e81-114">Description</span><span class="sxs-lookup"><span data-stu-id="21e81-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21e81-115">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="21e81-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="21e81-116">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="21e81-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="21e81-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="21e81-117">Parent Elements</span></span>

|<span data-ttu-id="21e81-118">Élément</span><span class="sxs-lookup"><span data-stu-id="21e81-118">Element</span></span>|<span data-ttu-id="21e81-119">Description</span><span class="sxs-lookup"><span data-stu-id="21e81-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21e81-120">Élément WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="21e81-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="21e81-121">Définit un format de liste larges (à valeur unique) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="21e81-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="21e81-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="21e81-122">Remarks</span></span>

<span data-ttu-id="21e81-123">Un affichage étendu est un format de liste qui affiche une valeur de propriété ou une valeur de script unique pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="21e81-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="21e81-124">Pour plus d’informations sur les composants d’une vue étendue, consultez [composants de vue larges](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="21e81-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="21e81-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="21e81-125">Example</span></span>

<span data-ttu-id="21e81-126">L’exemple suivant montre un élément `WideEntries` qui définit un élément `WideEntry` unique.</span><span class="sxs-lookup"><span data-stu-id="21e81-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="21e81-127">L’élément `WideEntry` contient un seul élément `WideItem` qui définit la valeur de la propriété ou du script qui est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="21e81-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="21e81-128">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="21e81-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21e81-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21e81-129">See Also</span></span>

[<span data-ttu-id="21e81-130">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="21e81-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="21e81-131">Élément WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="21e81-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="21e81-132">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="21e81-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="21e81-133">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e81-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
