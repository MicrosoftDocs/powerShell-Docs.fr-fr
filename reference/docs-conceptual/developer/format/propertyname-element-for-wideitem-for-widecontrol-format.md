---
title: PropertyName, élément de WideItem pour WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364938"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="3dcf2-102">PropertyName, élément pour WideItem pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3dcf2-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="3dcf2-103">Spécifie la propriété de l’objet dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="3dcf2-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="3dcf2-104">Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) élément WideControl (format) WideEntries, élément (format) WideEntry, élément (format) WideItem élément (format) NomPropriété, élément pour WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="3dcf2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3dcf2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dcf2-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3dcf2-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="3dcf2-106">Attributes and Elements</span></span>

<span data-ttu-id="3dcf2-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="3dcf2-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3dcf2-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="3dcf2-108">Attributes</span></span>

<span data-ttu-id="3dcf2-109">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3dcf2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3dcf2-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3dcf2-110">Child Elements</span></span>

<span data-ttu-id="3dcf2-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="3dcf2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3dcf2-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3dcf2-112">Parent Elements</span></span>

|<span data-ttu-id="3dcf2-113">Élément</span><span class="sxs-lookup"><span data-stu-id="3dcf2-113">Element</span></span>|<span data-ttu-id="3dcf2-114">Description</span><span class="sxs-lookup"><span data-stu-id="3dcf2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3dcf2-115">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="3dcf2-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="3dcf2-116">Définit la propriété ou le script dont la valeur est affichée dans la vue étendue.</span><span class="sxs-lookup"><span data-stu-id="3dcf2-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3dcf2-117">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="3dcf2-117">Text Value</span></span>

<span data-ttu-id="3dcf2-118">Spécifiez le nom de la propriété dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="3dcf2-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3dcf2-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="3dcf2-119">Remarks</span></span>

<span data-ttu-id="3dcf2-120">Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3dcf2-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3dcf2-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="3dcf2-121">Example</span></span>

<span data-ttu-id="3dcf2-122">Cet exemple montre une vue étendue qui affiche la valeur de la propriété ProcessName de l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="3dcf2-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3dcf2-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dcf2-123">See Also</span></span>

[<span data-ttu-id="3dcf2-124">Élément WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="3dcf2-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="3dcf2-125">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="3dcf2-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3dcf2-126">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="3dcf2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
