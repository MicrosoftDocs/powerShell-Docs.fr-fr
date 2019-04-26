---
title: Élément ScriptBlock pour WideItem pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064201"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="0f960-102">ScriptBlock, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0f960-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="0f960-103">Spécifie le script dont la valeur est affichée dans l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="0f960-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="0f960-104">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément WideControl (Format) élément WideEntries (Format) WideEntry, élément (Format) WideItem, élément (Format) ScriptBlock élément de configuration pour WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="0f960-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f960-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f960-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f960-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="0f960-106">Attributes and Elements</span></span>

<span data-ttu-id="0f960-107">Les sections suivantes décrivent les attributs, éléments enfants et élément parent de la `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="0f960-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f960-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="0f960-108">Attributes</span></span>

<span data-ttu-id="0f960-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0f960-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f960-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0f960-110">Child Elements</span></span>

<span data-ttu-id="0f960-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="0f960-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0f960-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0f960-112">Parent Elements</span></span>

|<span data-ttu-id="0f960-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0f960-113">Element</span></span>|<span data-ttu-id="0f960-114">Description</span><span class="sxs-lookup"><span data-stu-id="0f960-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f960-115">Élément WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="0f960-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="0f960-116">Définit le bloc de script ou de la propriété dont la valeur est affichée dans l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="0f960-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0f960-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="0f960-117">Text Value</span></span>

<span data-ttu-id="0f960-118">Spécifiez le script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="0f960-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f960-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="0f960-119">Remarks</span></span>

<span data-ttu-id="0f960-120">Pour plus d’informations sur les composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0f960-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f960-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="0f960-121">Example</span></span>

<span data-ttu-id="0f960-122">Cet exemple montre un `WideItem` élément qui définit un script dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="0f960-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="0f960-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f960-123">See Also</span></span>

[<span data-ttu-id="0f960-124">Élément WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="0f960-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="0f960-125">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="0f960-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0f960-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f960-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
