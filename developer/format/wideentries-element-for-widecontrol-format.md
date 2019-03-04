---
title: Élément WideEntries pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853275"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="67277-102">WideEntries, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="67277-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="67277-103">Fournit les définitions de l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="67277-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="67277-104">L’affichage large doit spécifier une ou plusieurs définitions.</span><span class="sxs-lookup"><span data-stu-id="67277-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="67277-105">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément WideControl (Format) WideEntries élément (Format)</span><span class="sxs-lookup"><span data-stu-id="67277-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67277-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67277-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="67277-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="67277-107">Attributes and Elements</span></span>

<span data-ttu-id="67277-108">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `WideEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="67277-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="67277-109">Au moins un élément enfant doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="67277-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="67277-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="67277-110">Attributes</span></span>

<span data-ttu-id="67277-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="67277-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67277-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="67277-112">Child Elements</span></span>

|<span data-ttu-id="67277-113">Élément</span><span class="sxs-lookup"><span data-stu-id="67277-113">Element</span></span>|<span data-ttu-id="67277-114">Description</span><span class="sxs-lookup"><span data-stu-id="67277-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67277-115">Élément WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="67277-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="67277-116">Fournit une définition de l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="67277-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="67277-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="67277-117">Parent Elements</span></span>

|<span data-ttu-id="67277-118">Élément</span><span class="sxs-lookup"><span data-stu-id="67277-118">Element</span></span>|<span data-ttu-id="67277-119">Description</span><span class="sxs-lookup"><span data-stu-id="67277-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67277-120">Élément WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="67277-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="67277-121">Définit un (valeur unique) à l’échelle du format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="67277-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="67277-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="67277-122">Remarks</span></span>

<span data-ttu-id="67277-123">Un affichage plus large est un format de liste qui affiche une valeur de propriété unique ou une valeur de script pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="67277-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="67277-124">Pour plus d’informations sur les composants d’un affichage plus large, consultez [les composants de vue large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="67277-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="67277-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="67277-125">Example</span></span>

<span data-ttu-id="67277-126">L’exemple suivant montre un `WideEntries` élément qui définit un seul `WideEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="67277-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="67277-127">Le `WideEntry` élément contienne un seul `WideItem` élément qui définit quelle valeur de propriété ou un script s’affiche dans la vue.</span><span class="sxs-lookup"><span data-stu-id="67277-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="67277-128">Pour obtenir un exemple complet d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="67277-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67277-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67277-129">See Also</span></span>

[<span data-ttu-id="67277-130">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="67277-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="67277-131">Élément WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="67277-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="67277-132">Élément WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="67277-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="67277-133">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="67277-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
