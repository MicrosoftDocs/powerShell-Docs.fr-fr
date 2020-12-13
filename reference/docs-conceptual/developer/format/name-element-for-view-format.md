---
ms.date: 09/13/2016
ms.topic: reference
title: Name, élément pour View (Format)
description: Name, élément pour View (Format)
ms.openlocfilehash: 5781bcdf7a0e1eb5e9c7e97bb6acc0a383dc0262
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666453"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="a6db9-103">Name, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a6db9-103">Name Element for View (Format)</span></span>

<span data-ttu-id="a6db9-104">Spécifie le nom utilisé pour identifier la vue.</span><span class="sxs-lookup"><span data-stu-id="a6db9-104">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="a6db9-105">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément Name (format)</span><span class="sxs-lookup"><span data-stu-id="a6db9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6db9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6db9-106">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6db9-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a6db9-107">Attributes and Elements</span></span>

<span data-ttu-id="a6db9-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `Name` élément.</span><span class="sxs-lookup"><span data-stu-id="a6db9-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="a6db9-109">Un seul `Name` élément est autorisé pour chaque vue.</span><span class="sxs-lookup"><span data-stu-id="a6db9-109">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6db9-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="a6db9-110">Attributes</span></span>

<span data-ttu-id="a6db9-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a6db9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6db9-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a6db9-112">Child Elements</span></span>

<span data-ttu-id="a6db9-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a6db9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6db9-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a6db9-114">Parent Elements</span></span>

|<span data-ttu-id="a6db9-115">Élément</span><span class="sxs-lookup"><span data-stu-id="a6db9-115">Element</span></span>|<span data-ttu-id="a6db9-116">Description</span><span class="sxs-lookup"><span data-stu-id="a6db9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6db9-117">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a6db9-117">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="a6db9-118">Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="a6db9-118">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a6db9-119">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="a6db9-119">Text Value</span></span>

<span data-ttu-id="a6db9-120">Spécifiez un nom convivial unique pour la vue.</span><span class="sxs-lookup"><span data-stu-id="a6db9-120">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="a6db9-121">Ce nom peut inclure une référence au type de la vue (par exemple, une vue de table ou une vue Liste), l’objet ou l’ensemble d’objets qui utilisent la vue, la commande qui retourne les objets ou une combinaison de ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="a6db9-121">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6db9-122">Notes</span><span class="sxs-lookup"><span data-stu-id="a6db9-122">Remarks</span></span>

<span data-ttu-id="a6db9-123">Pour plus d’informations sur les différents types d’affichages, consultez les rubriques suivantes : [vue table](./creating-a-table-view.md), [mode liste](./creating-a-list-view.md), [vue étendue](./creating-a-wide-view.md)et [vue personnalisée](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a6db9-123">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="a6db9-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="a6db9-124">Example</span></span>

<span data-ttu-id="a6db9-125">L’exemple suivant montre un `View` élément qui définit un affichage de table pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="a6db9-125">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="a6db9-126">Le nom de la vue est « service ».</span><span class="sxs-lookup"><span data-stu-id="a6db9-126">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="a6db9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6db9-127">See Also</span></span>

[<span data-ttu-id="a6db9-128">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="a6db9-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a6db9-129">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="a6db9-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a6db9-130">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="a6db9-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a6db9-131">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="a6db9-131">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="a6db9-132">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a6db9-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="a6db9-133">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6db9-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
