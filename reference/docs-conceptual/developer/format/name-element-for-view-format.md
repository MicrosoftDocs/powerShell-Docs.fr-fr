---
title: Élément Name pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362638"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="5c706-102">Name, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="5c706-102">Name Element for View (Format)</span></span>

<span data-ttu-id="5c706-103">Spécifie le nom utilisé pour identifier la vue.</span><span class="sxs-lookup"><span data-stu-id="5c706-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="5c706-104">Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément Name (format)</span><span class="sxs-lookup"><span data-stu-id="5c706-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5c706-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c706-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c706-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5c706-106">Attributes and Elements</span></span>

<span data-ttu-id="5c706-107">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `Name`.</span><span class="sxs-lookup"><span data-stu-id="5c706-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="5c706-108">Un seul élément `Name` est autorisé pour chaque vue.</span><span class="sxs-lookup"><span data-stu-id="5c706-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c706-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="5c706-109">Attributes</span></span>

<span data-ttu-id="5c706-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5c706-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5c706-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5c706-111">Child Elements</span></span>

<span data-ttu-id="5c706-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5c706-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5c706-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5c706-113">Parent Elements</span></span>

|<span data-ttu-id="5c706-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5c706-114">Element</span></span>|<span data-ttu-id="5c706-115">Description</span><span class="sxs-lookup"><span data-stu-id="5c706-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c706-116">View, élément (format)</span><span class="sxs-lookup"><span data-stu-id="5c706-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="5c706-117">Définit une vue qui est utilisée pour afficher les membres d’un ou de plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="5c706-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5c706-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="5c706-118">Text Value</span></span>

<span data-ttu-id="5c706-119">Spécifiez un nom convivial unique pour la vue.</span><span class="sxs-lookup"><span data-stu-id="5c706-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="5c706-120">Ce nom peut inclure une référence au type de la vue (par exemple, une vue de table ou une vue Liste), l’objet ou l’ensemble d’objets qui utilisent la vue, la commande qui retourne les objets ou une combinaison de ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="5c706-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c706-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="5c706-121">Remarks</span></span>

<span data-ttu-id="5c706-122">Pour plus d’informations sur les différents types d’affichages, consultez les rubriques suivantes : [vue table](./creating-a-table-view.md), [mode liste](./creating-a-list-view.md), [vue étendue](./creating-a-wide-view.md)et [vue personnalisée](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5c706-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="5c706-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="5c706-123">Example</span></span>

<span data-ttu-id="5c706-124">L’exemple suivant montre un élément `View` qui définit une vue table pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="5c706-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="5c706-125">Le nom de la vue est « service ».</span><span class="sxs-lookup"><span data-stu-id="5c706-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="5c706-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c706-126">See Also</span></span>

[<span data-ttu-id="5c706-127">Création d’un affichage de liste</span><span class="sxs-lookup"><span data-stu-id="5c706-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5c706-128">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="5c706-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5c706-129">Création d’un affichage étendu</span><span class="sxs-lookup"><span data-stu-id="5c706-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5c706-130">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="5c706-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="5c706-131">View, élément (format)</span><span class="sxs-lookup"><span data-stu-id="5c706-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="5c706-132">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c706-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
