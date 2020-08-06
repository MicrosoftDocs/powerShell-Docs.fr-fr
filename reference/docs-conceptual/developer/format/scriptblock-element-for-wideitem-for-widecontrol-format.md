---
title: Élément ScriptBlock pour WideItem pour WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: be649d6de0d2dfa6bad14f2d7476cced9cd6cb6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787595"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="f57ec-102">ScriptBlock, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f57ec-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="f57ec-103">Spécifie le script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="f57ec-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="f57ec-104">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément WideControl (format) élément WideEntries (format) WideEntry élément (format) WideItem élément (format) élément ScriptBlock pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="f57ec-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f57ec-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f57ec-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f57ec-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f57ec-106">Attributes and Elements</span></span>

<span data-ttu-id="f57ec-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="f57ec-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f57ec-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="f57ec-108">Attributes</span></span>

<span data-ttu-id="f57ec-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f57ec-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f57ec-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f57ec-110">Child Elements</span></span>

<span data-ttu-id="f57ec-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f57ec-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f57ec-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f57ec-112">Parent Elements</span></span>

|<span data-ttu-id="f57ec-113">Élément</span><span class="sxs-lookup"><span data-stu-id="f57ec-113">Element</span></span>|<span data-ttu-id="f57ec-114">Description</span><span class="sxs-lookup"><span data-stu-id="f57ec-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f57ec-115">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="f57ec-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="f57ec-116">Définit la propriété ou le bloc de script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="f57ec-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f57ec-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="f57ec-117">Text Value</span></span>

<span data-ttu-id="f57ec-118">Spécifiez le script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="f57ec-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f57ec-119">Notes</span><span class="sxs-lookup"><span data-stu-id="f57ec-119">Remarks</span></span>

<span data-ttu-id="f57ec-120">Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f57ec-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f57ec-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="f57ec-121">Example</span></span>

<span data-ttu-id="f57ec-122">Cet exemple montre un `WideItem` élément qui définit un script dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="f57ec-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="f57ec-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f57ec-123">See Also</span></span>

[<span data-ttu-id="f57ec-124">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="f57ec-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="f57ec-125">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="f57ec-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f57ec-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="f57ec-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
