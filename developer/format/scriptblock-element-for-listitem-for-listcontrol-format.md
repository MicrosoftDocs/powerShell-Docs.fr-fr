---
title: Élément ScriptBlock pour ListItem pour un objet ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855555"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="6b231-102">ScriptBlock, élément pour ListItem pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6b231-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="6b231-103">Spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="6b231-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="6b231-104">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) élément ListControl (Format) situés élément d’élément de ListEntry ListControl (Format) pour situés d’élément de ListItems ListControl (Format) pour ListEntry élément de ListItem ListControl (Format) pour ListItems pour ListControl (Format), élément ScriptBlock pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6b231-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6b231-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b231-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b231-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="6b231-106">Attributes and Elements</span></span>

<span data-ttu-id="6b231-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="6b231-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b231-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="6b231-108">Attributes</span></span>

<span data-ttu-id="6b231-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6b231-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b231-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6b231-110">Child Elements</span></span>

<span data-ttu-id="6b231-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6b231-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6b231-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6b231-112">Parent Elements</span></span>

|<span data-ttu-id="6b231-113">Élément</span><span class="sxs-lookup"><span data-stu-id="6b231-113">Element</span></span>|<span data-ttu-id="6b231-114">Description</span><span class="sxs-lookup"><span data-stu-id="6b231-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b231-115">Élément ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="6b231-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="6b231-116">Définit la propriété ou un script dont la valeur est affichée dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="6b231-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6b231-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="6b231-117">Text Value</span></span>

<span data-ttu-id="6b231-118">Spécifiez le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="6b231-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="6b231-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="6b231-119">Remarks</span></span>

<span data-ttu-id="6b231-120">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="6b231-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="6b231-121">Pour plus d’informations sur la spécification des scripts dans un affichage de liste, consultez [mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6b231-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6b231-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b231-122">Example</span></span>

<span data-ttu-id="6b231-123">L’exemple suivant montre comment spécifier la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="6b231-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="6b231-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b231-124">See Also</span></span>

[<span data-ttu-id="6b231-125">Élément PropertyName pour ListItem pour un objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6b231-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="6b231-126">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="6b231-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6b231-127">Élément ListItem pour ListItems pour ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6b231-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="6b231-128">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b231-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
