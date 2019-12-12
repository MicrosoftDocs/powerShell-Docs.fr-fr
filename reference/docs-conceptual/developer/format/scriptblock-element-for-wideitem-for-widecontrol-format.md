---
title: Élément ScriptBlock pour WideItem pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362028"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="059b9-102">ScriptBlock, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="059b9-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="059b9-103">Spécifie le script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="059b9-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="059b9-104">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément WideControl (format) élément WideEntries (format) WideEntry élément (format) WideItem élément (format) élément ScriptBlock pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="059b9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="059b9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="059b9-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="059b9-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="059b9-106">Attributes and Elements</span></span>

<span data-ttu-id="059b9-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="059b9-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="059b9-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="059b9-108">Attributes</span></span>

<span data-ttu-id="059b9-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="059b9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="059b9-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="059b9-110">Child Elements</span></span>

<span data-ttu-id="059b9-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="059b9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="059b9-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="059b9-112">Parent Elements</span></span>

|<span data-ttu-id="059b9-113">Élément</span><span class="sxs-lookup"><span data-stu-id="059b9-113">Element</span></span>|<span data-ttu-id="059b9-114">Description</span><span class="sxs-lookup"><span data-stu-id="059b9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="059b9-115">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="059b9-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="059b9-116">Définit la propriété ou le bloc de script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="059b9-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="059b9-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="059b9-117">Text Value</span></span>

<span data-ttu-id="059b9-118">Spécifiez le script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="059b9-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="059b9-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="059b9-119">Remarks</span></span>

<span data-ttu-id="059b9-120">Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="059b9-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="059b9-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="059b9-121">Example</span></span>

<span data-ttu-id="059b9-122">Cet exemple montre un élément `WideItem` qui définit un script dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="059b9-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="059b9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="059b9-123">See Also</span></span>

[<span data-ttu-id="059b9-124">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="059b9-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="059b9-125">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="059b9-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="059b9-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="059b9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
