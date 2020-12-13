---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName, élément pour WideItem pour WideControl (Format)
description: PropertyName, élément pour WideItem pour WideControl (Format)
ms.openlocfilehash: 1d4d5eaf7708dfbd7997122fac156a36487538ea
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665615"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="0cc22-103">PropertyName, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0cc22-103">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="0cc22-104">Spécifie la propriété de l’objet dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="0cc22-104">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="0cc22-105">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry, élément (format) WideItem élément (format) NomPropriété, élément pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="0cc22-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0cc22-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cc22-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0cc22-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0cc22-107">Attributes and Elements</span></span>

<span data-ttu-id="0cc22-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="0cc22-108">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0cc22-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="0cc22-109">Attributes</span></span>

<span data-ttu-id="0cc22-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0cc22-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0cc22-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0cc22-111">Child Elements</span></span>

<span data-ttu-id="0cc22-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0cc22-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0cc22-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0cc22-113">Parent Elements</span></span>

|<span data-ttu-id="0cc22-114">Élément</span><span class="sxs-lookup"><span data-stu-id="0cc22-114">Element</span></span>|<span data-ttu-id="0cc22-115">Description</span><span class="sxs-lookup"><span data-stu-id="0cc22-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0cc22-116">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="0cc22-116">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="0cc22-117">Définit la propriété ou le script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="0cc22-117">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0cc22-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="0cc22-118">Text Value</span></span>

<span data-ttu-id="0cc22-119">Spécifiez le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="0cc22-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cc22-120">Notes</span><span class="sxs-lookup"><span data-stu-id="0cc22-120">Remarks</span></span>

<span data-ttu-id="0cc22-121">Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0cc22-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0cc22-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="0cc22-122">Example</span></span>

<span data-ttu-id="0cc22-123">Cet exemple montre une vue étendue qui affiche la valeur de la propriété ProcessName de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="0cc22-123">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="0cc22-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cc22-124">See Also</span></span>

[<span data-ttu-id="0cc22-125">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="0cc22-125">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="0cc22-126">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="0cc22-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0cc22-127">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="0cc22-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
