---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock, élément pour WideItem pour WideControl (Format)
description: ScriptBlock, élément pour WideItem pour WideControl (Format)
ms.openlocfilehash: 68e47926e5e6b846c8a0a3dbc16d1f0d59f11dee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659879"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="1c45a-103">ScriptBlock, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1c45a-103">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="1c45a-104">Spécifie le script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="1c45a-104">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="1c45a-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément WideControl (format) élément WideEntries (format) WideEntry élément (format) WideItem élément (format) élément ScriptBlock pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="1c45a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c45a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c45a-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c45a-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1c45a-107">Attributes and Elements</span></span>

<span data-ttu-id="1c45a-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="1c45a-108">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c45a-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="1c45a-109">Attributes</span></span>

<span data-ttu-id="1c45a-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1c45a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c45a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1c45a-111">Child Elements</span></span>

<span data-ttu-id="1c45a-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1c45a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1c45a-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1c45a-113">Parent Elements</span></span>

|<span data-ttu-id="1c45a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="1c45a-114">Element</span></span>|<span data-ttu-id="1c45a-115">Description</span><span class="sxs-lookup"><span data-stu-id="1c45a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c45a-116">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="1c45a-116">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="1c45a-117">Définit la propriété ou le bloc de script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="1c45a-117">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1c45a-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="1c45a-118">Text Value</span></span>

<span data-ttu-id="1c45a-119">Spécifiez le script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="1c45a-119">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c45a-120">Notes</span><span class="sxs-lookup"><span data-stu-id="1c45a-120">Remarks</span></span>

<span data-ttu-id="1c45a-121">Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1c45a-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1c45a-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="1c45a-122">Example</span></span>

<span data-ttu-id="1c45a-123">Cet exemple montre un `WideItem` élément qui définit un script dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="1c45a-123">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="1c45a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c45a-124">See Also</span></span>

[<span data-ttu-id="1c45a-125">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="1c45a-125">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="1c45a-126">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="1c45a-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1c45a-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c45a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
