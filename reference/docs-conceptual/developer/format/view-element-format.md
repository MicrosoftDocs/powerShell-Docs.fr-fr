---
ms.date: 09/13/2016
ms.topic: reference
title: View, élément (Format)
description: View, élément (Format)
ms.openlocfilehash: 6fed1304d94339cc90b6ae53e06483c08d937c12
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649732"
---
# <a name="view-element-format"></a><span data-ttu-id="ad97d-103">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-103">View Element (Format)</span></span>

<span data-ttu-id="ad97d-104">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="ad97d-104">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="ad97d-105">Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="ad97d-105">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="ad97d-106">Élément de configuration (format) élément ViewDefinitions (format), élément de vue (format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad97d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad97d-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="ad97d-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ad97d-108">Attributes and Elements</span></span>

<span data-ttu-id="ad97d-109">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `View` élément.</span><span class="sxs-lookup"><span data-stu-id="ad97d-109">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="ad97d-110">Vous devez spécifier un et un seul des éléments enfants du contrôle, et vous devez spécifier le nom de la vue et les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="ad97d-110">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="ad97d-111">La définition de contrôles personnalisés, la façon de regrouper des objets et la spécification de si la vue est hors bande sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="ad97d-111">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad97d-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="ad97d-112">Attributes</span></span>

<span data-ttu-id="ad97d-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ad97d-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad97d-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ad97d-114">Child Elements</span></span>

|<span data-ttu-id="ad97d-115">Élément</span><span class="sxs-lookup"><span data-stu-id="ad97d-115">Element</span></span>|<span data-ttu-id="ad97d-116">Description</span><span class="sxs-lookup"><span data-stu-id="ad97d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad97d-117">Controls, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-117">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="ad97d-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ad97d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ad97d-119">Définit un ensemble de contrôles qui peuvent être référencés par leur nom à partir de la vue.</span><span class="sxs-lookup"><span data-stu-id="ad97d-119">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="ad97d-120">CustomControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-120">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="ad97d-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ad97d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ad97d-122">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="ad97d-122">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="ad97d-123">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-123">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="ad97d-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ad97d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="ad97d-125">Définit le mode de regroupement des membres des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="ad97d-125">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="ad97d-126">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-126">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="ad97d-127">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ad97d-127">Optional element.</span></span><br /><br /> <span data-ttu-id="ad97d-128">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="ad97d-128">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="ad97d-129">Name, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-129">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="ad97d-130">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="ad97d-130">Required element.</span></span><br /><br /> <span data-ttu-id="ad97d-131">Spécifie le nom utilisé pour référencer la vue.</span><span class="sxs-lookup"><span data-stu-id="ad97d-131">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="ad97d-132">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-132">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="ad97d-133">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ad97d-133">Optional element.</span></span><br /><br /> <span data-ttu-id="ad97d-134">Définit un format de tableau pour la vue.</span><span class="sxs-lookup"><span data-stu-id="ad97d-134">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="ad97d-135">Élément ViewSelectedBy pour View (format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-135">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="ad97d-136">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="ad97d-136">Required element.</span></span><br /><br /> <span data-ttu-id="ad97d-137">Définit les objets .NET que cet affichage affiche.</span><span class="sxs-lookup"><span data-stu-id="ad97d-137">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="ad97d-138">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-138">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="ad97d-139">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="ad97d-139">Optional element.</span></span><br /><br /> <span data-ttu-id="ad97d-140">Définit un format de liste larges (à valeur unique) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="ad97d-140">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ad97d-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ad97d-141">Parent Elements</span></span>

|<span data-ttu-id="ad97d-142">Élément</span><span class="sxs-lookup"><span data-stu-id="ad97d-142">Element</span></span>|<span data-ttu-id="ad97d-143">Description</span><span class="sxs-lookup"><span data-stu-id="ad97d-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad97d-144">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-144">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="ad97d-145">Définit les vues utilisées pour afficher des objets.</span><span class="sxs-lookup"><span data-stu-id="ad97d-145">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ad97d-146">Notes</span><span class="sxs-lookup"><span data-stu-id="ad97d-146">Remarks</span></span>

<span data-ttu-id="ad97d-147">Pour plus d’informations sur les composants de différents affichages et contrôles personnalisés, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad97d-147">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="ad97d-148">Composants de la vue table</span><span class="sxs-lookup"><span data-stu-id="ad97d-148">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="ad97d-149">Composants de la vue Liste</span><span class="sxs-lookup"><span data-stu-id="ad97d-149">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="ad97d-150">Composants de vue larges</span><span class="sxs-lookup"><span data-stu-id="ad97d-150">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="ad97d-151">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="ad97d-151">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="ad97d-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="ad97d-152">Example</span></span>

<span data-ttu-id="ad97d-153">Cet exemple montre un `View` élément qui définit un affichage de table pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="ad97d-153">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ad97d-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad97d-154">See Also</span></span>

[<span data-ttu-id="ad97d-155">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-155">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="ad97d-156">Name, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-156">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="ad97d-157">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-157">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="ad97d-158">Controls, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-158">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="ad97d-159">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-159">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="ad97d-160">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-160">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="ad97d-161">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-161">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="ad97d-162">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-162">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="ad97d-163">CustomControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="ad97d-163">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="ad97d-164">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad97d-164">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
