---
title: Élément label pour GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07b4d037472a9dd2329e94576ec10f5b82f46b34
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785776"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="86b49-102">Label, élément pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86b49-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="86b49-103">Spécifie une étiquette qui s’affiche lorsqu’un nouveau groupe est rencontré.</span><span class="sxs-lookup"><span data-stu-id="86b49-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="86b49-104">Élément de configuration (format) élément ViewDefinitions (format) élément d’affichage (format) élément GroupBy pour l’élément label View (format) pour GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="86b49-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86b49-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86b49-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86b49-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="86b49-106">Attributes and Elements</span></span>

<span data-ttu-id="86b49-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Label` élément.</span><span class="sxs-lookup"><span data-stu-id="86b49-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86b49-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="86b49-108">Attributes</span></span>

<span data-ttu-id="86b49-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="86b49-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86b49-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="86b49-110">Child Elements</span></span>

<span data-ttu-id="86b49-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="86b49-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="86b49-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="86b49-112">Parent Elements</span></span>

|<span data-ttu-id="86b49-113">Élément</span><span class="sxs-lookup"><span data-stu-id="86b49-113">Element</span></span>|<span data-ttu-id="86b49-114">Description</span><span class="sxs-lookup"><span data-stu-id="86b49-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86b49-115">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="86b49-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="86b49-116">Définit le mode d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="86b49-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="86b49-117">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="86b49-117">Text Value</span></span>

<span data-ttu-id="86b49-118">Spécifiez le texte qui s’affiche chaque fois que Windows PowerShell rencontre une nouvelle propriété ou une nouvelle valeur de script.</span><span class="sxs-lookup"><span data-stu-id="86b49-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="86b49-119">Notes</span><span class="sxs-lookup"><span data-stu-id="86b49-119">Remarks</span></span>

<span data-ttu-id="86b49-120">En plus du texte spécifié par cet élément, Windows PowerShell affiche la nouvelle valeur qui démarre le groupe et ajoute une ligne vide avant et après le groupe.</span><span class="sxs-lookup"><span data-stu-id="86b49-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="86b49-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="86b49-121">Example</span></span>

<span data-ttu-id="86b49-122">L’exemple suivant montre l’étiquette d’un nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="86b49-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="86b49-123">L’étiquette affichée devrait ressembler à ceci :`Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="86b49-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="86b49-124">Pour obtenir un exemple de fichier de mise en forme complet qui comprend cet élément, consultez [vue étendue (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="86b49-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86b49-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86b49-125">See Also</span></span>

[<span data-ttu-id="86b49-126">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="86b49-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="86b49-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="86b49-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
