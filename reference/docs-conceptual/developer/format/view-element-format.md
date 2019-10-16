---
title: View, élément (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361458"
---
# <a name="view-element-format"></a><span data-ttu-id="d3bf0-102">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-102">View Element (Format)</span></span>

<span data-ttu-id="d3bf0-103">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="d3bf0-104">Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="d3bf0-105">Élément de configuration (format) élément ViewDefinitions (format), élément de vue (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d3bf0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3bf0-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3bf0-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="d3bf0-107">Attributes and Elements</span></span>

<span data-ttu-id="d3bf0-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `View`.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="d3bf0-109">Vous devez spécifier un et un seul des éléments enfants du contrôle, et vous devez spécifier le nom de la vue et les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="d3bf0-110">La définition de contrôles personnalisés, la façon de regrouper des objets et la spécification de si la vue est hors bande sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3bf0-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="d3bf0-111">Attributes</span></span>

<span data-ttu-id="d3bf0-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d3bf0-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d3bf0-113">Child Elements</span></span>

|<span data-ttu-id="d3bf0-114">Élément</span><span class="sxs-lookup"><span data-stu-id="d3bf0-114">Element</span></span>|<span data-ttu-id="d3bf0-115">Description</span><span class="sxs-lookup"><span data-stu-id="d3bf0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3bf0-116">Controls, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="d3bf0-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d3bf0-118">Définit un ensemble de contrôles qui peuvent être référencés par leur nom à partir de la vue.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="d3bf0-119">CustomControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="d3bf0-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d3bf0-121">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="d3bf0-122">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="d3bf0-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-123">Optional element.</span></span><br /><br /> <span data-ttu-id="d3bf0-124">Définit le mode de regroupement des membres des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="d3bf0-125">Élément ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="d3bf0-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-126">Optional element.</span></span><br /><br /> <span data-ttu-id="d3bf0-127">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="d3bf0-128">Élément Name pour View (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="d3bf0-129">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-129">Required element.</span></span><br /><br /> <span data-ttu-id="d3bf0-130">Spécifie le nom utilisé pour référencer la vue.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="d3bf0-131">Élément table ((format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="d3bf0-132">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-132">Optional element.</span></span><br /><br /> <span data-ttu-id="d3bf0-133">Définit un format de tableau pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="d3bf0-134">Élément ViewSelectedBy pour View (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="d3bf0-135">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-135">Required element.</span></span><br /><br /> <span data-ttu-id="d3bf0-136">Définit les objets .NET que cet affichage affiche.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="d3bf0-137">Élément WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="d3bf0-138">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-138">Optional element.</span></span><br /><br /> <span data-ttu-id="d3bf0-139">Définit un format de liste larges (à valeur unique) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d3bf0-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d3bf0-140">Parent Elements</span></span>

|<span data-ttu-id="d3bf0-141">Élément</span><span class="sxs-lookup"><span data-stu-id="d3bf0-141">Element</span></span>|<span data-ttu-id="d3bf0-142">Description</span><span class="sxs-lookup"><span data-stu-id="d3bf0-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3bf0-143">Élément ViewDefinitions (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="d3bf0-144">Définit les vues utilisées pour afficher des objets.</span><span class="sxs-lookup"><span data-stu-id="d3bf0-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d3bf0-145">Remarks</span><span class="sxs-lookup"><span data-stu-id="d3bf0-145">Remarks</span></span>

<span data-ttu-id="d3bf0-146">Pour plus d’informations sur les composants de différents affichages et contrôles personnalisés, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3bf0-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="d3bf0-147">Composants de la vue table</span><span class="sxs-lookup"><span data-stu-id="d3bf0-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="d3bf0-148">Composants de la vue Liste</span><span class="sxs-lookup"><span data-stu-id="d3bf0-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="d3bf0-149">Composants de vue larges</span><span class="sxs-lookup"><span data-stu-id="d3bf0-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="d3bf0-150">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="d3bf0-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="d3bf0-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3bf0-151">Example</span></span>

<span data-ttu-id="d3bf0-152">Cet exemple montre un élément `View` qui définit une vue de table pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="d3bf0-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="d3bf0-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3bf0-153">See Also</span></span>

[<span data-ttu-id="d3bf0-154">Élément ViewDefinitions (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="d3bf0-155">Élément Name pour View (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="d3bf0-156">Élément ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="d3bf0-157">Controls, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="d3bf0-158">GroupBy, élément de View (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="d3bf0-159">Élément table ((format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="d3bf0-160">Élément ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="d3bf0-161">Élément WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="d3bf0-162">CustomControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="d3bf0-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="d3bf0-163">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3bf0-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
