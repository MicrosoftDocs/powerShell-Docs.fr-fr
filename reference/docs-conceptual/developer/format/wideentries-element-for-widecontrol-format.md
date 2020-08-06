---
title: Élément WideEntries pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74383b288c945008c1d7b5119363a166c04802ae
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785045"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="3d7b7-102">WideEntries, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3d7b7-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="3d7b7-103">Fournit les définitions de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="3d7b7-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="3d7b7-104">La vue étendue doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="3d7b7-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="3d7b7-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément WideControl (format) WideEntries, élément (format)</span><span class="sxs-lookup"><span data-stu-id="3d7b7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d7b7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d7b7-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d7b7-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3d7b7-107">Attributes and Elements</span></span>

<span data-ttu-id="3d7b7-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `WideEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="3d7b7-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="3d7b7-109">Au moins un élément enfant doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="3d7b7-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d7b7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="3d7b7-110">Attributes</span></span>

<span data-ttu-id="3d7b7-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3d7b7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d7b7-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3d7b7-112">Child Elements</span></span>

|<span data-ttu-id="3d7b7-113">Élément</span><span class="sxs-lookup"><span data-stu-id="3d7b7-113">Element</span></span>|<span data-ttu-id="3d7b7-114">Description</span><span class="sxs-lookup"><span data-stu-id="3d7b7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d7b7-115">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3d7b7-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="3d7b7-116">Fournit une définition de la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="3d7b7-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3d7b7-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3d7b7-117">Parent Elements</span></span>

|<span data-ttu-id="3d7b7-118">Élément</span><span class="sxs-lookup"><span data-stu-id="3d7b7-118">Element</span></span>|<span data-ttu-id="3d7b7-119">Description</span><span class="sxs-lookup"><span data-stu-id="3d7b7-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d7b7-120">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="3d7b7-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="3d7b7-121">Définit un format de liste larges (à valeur unique) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="3d7b7-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d7b7-122">Notes</span><span class="sxs-lookup"><span data-stu-id="3d7b7-122">Remarks</span></span>

<span data-ttu-id="3d7b7-123">Un affichage étendu est un format de liste qui affiche une valeur de propriété ou une valeur de script unique pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="3d7b7-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="3d7b7-124">Pour plus d’informations sur les composants d’une vue étendue, consultez [composants de vue larges](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3d7b7-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3d7b7-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="3d7b7-125">Example</span></span>

<span data-ttu-id="3d7b7-126">L’exemple suivant montre un `WideEntries` élément qui définit un `WideEntry` élément unique.</span><span class="sxs-lookup"><span data-stu-id="3d7b7-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="3d7b7-127">L' `WideEntry` élément contient un `WideItem` élément unique qui définit la valeur de la propriété ou du script qui est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="3d7b7-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="3d7b7-128">Pour obtenir un exemple complet d’une vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="3d7b7-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d7b7-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d7b7-129">See Also</span></span>

[<span data-ttu-id="3d7b7-130">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="3d7b7-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3d7b7-131">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="3d7b7-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="3d7b7-132">Élément WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3d7b7-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="3d7b7-133">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d7b7-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
