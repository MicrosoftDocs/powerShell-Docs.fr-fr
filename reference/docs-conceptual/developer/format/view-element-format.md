---
title: View, élément (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c0c6fa373cfca3a55a62f201e1eabc6a1e308ef7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785028"
---
# <a name="view-element-format"></a><span data-ttu-id="a8426-102">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-102">View Element (Format)</span></span>

<span data-ttu-id="a8426-103">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="a8426-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="a8426-104">Il n’existe aucune limite quant au nombre d’affichages pouvant être définis dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="a8426-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="a8426-105">Élément de configuration (format) élément ViewDefinitions (format), élément de vue (format)</span><span class="sxs-lookup"><span data-stu-id="a8426-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8426-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8426-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="a8426-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a8426-107">Attributes and Elements</span></span>

<span data-ttu-id="a8426-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `View` élément.</span><span class="sxs-lookup"><span data-stu-id="a8426-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="a8426-109">Vous devez spécifier un et un seul des éléments enfants du contrôle, et vous devez spécifier le nom de la vue et les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="a8426-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="a8426-110">La définition de contrôles personnalisés, la façon de regrouper des objets et la spécification de si la vue est hors bande sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="a8426-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8426-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a8426-111">Attributes</span></span>

<span data-ttu-id="a8426-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a8426-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a8426-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a8426-113">Child Elements</span></span>

|<span data-ttu-id="a8426-114">Élément</span><span class="sxs-lookup"><span data-stu-id="a8426-114">Element</span></span>|<span data-ttu-id="a8426-115">Description</span><span class="sxs-lookup"><span data-stu-id="a8426-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8426-116">Controls, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="a8426-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a8426-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a8426-118">Définit un ensemble de contrôles qui peuvent être référencés par leur nom à partir de la vue.</span><span class="sxs-lookup"><span data-stu-id="a8426-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="a8426-119">CustomControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="a8426-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="a8426-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a8426-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a8426-121">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="a8426-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="a8426-122">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="a8426-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a8426-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a8426-124">Définit le mode de regroupement des membres des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="a8426-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="a8426-125">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="a8426-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a8426-126">Optional element.</span></span><br /><br /> <span data-ttu-id="a8426-127">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="a8426-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="a8426-128">Name, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="a8426-129">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="a8426-129">Required element.</span></span><br /><br /> <span data-ttu-id="a8426-130">Spécifie le nom utilisé pour référencer la vue.</span><span class="sxs-lookup"><span data-stu-id="a8426-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="a8426-131">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="a8426-132">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a8426-132">Optional element.</span></span><br /><br /> <span data-ttu-id="a8426-133">Définit un format de tableau pour la vue.</span><span class="sxs-lookup"><span data-stu-id="a8426-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="a8426-134">Élément ViewSelectedBy pour View (format)</span><span class="sxs-lookup"><span data-stu-id="a8426-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="a8426-135">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="a8426-135">Required element.</span></span><br /><br /> <span data-ttu-id="a8426-136">Définit les objets .NET que cet affichage affiche.</span><span class="sxs-lookup"><span data-stu-id="a8426-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="a8426-137">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="a8426-138">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="a8426-138">Optional element.</span></span><br /><br /> <span data-ttu-id="a8426-139">Définit un format de liste larges (à valeur unique) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="a8426-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a8426-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a8426-140">Parent Elements</span></span>

|<span data-ttu-id="a8426-141">Élément</span><span class="sxs-lookup"><span data-stu-id="a8426-141">Element</span></span>|<span data-ttu-id="a8426-142">Description</span><span class="sxs-lookup"><span data-stu-id="a8426-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8426-143">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="a8426-144">Définit les vues utilisées pour afficher des objets.</span><span class="sxs-lookup"><span data-stu-id="a8426-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a8426-145">Notes</span><span class="sxs-lookup"><span data-stu-id="a8426-145">Remarks</span></span>

<span data-ttu-id="a8426-146">Pour plus d’informations sur les composants de différents affichages et contrôles personnalisés, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="a8426-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="a8426-147">Composants de la vue table</span><span class="sxs-lookup"><span data-stu-id="a8426-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="a8426-148">Composants de la vue Liste</span><span class="sxs-lookup"><span data-stu-id="a8426-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="a8426-149">Composants de vue larges</span><span class="sxs-lookup"><span data-stu-id="a8426-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="a8426-150">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="a8426-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="a8426-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="a8426-151">Example</span></span>

<span data-ttu-id="a8426-152">Cet exemple montre un `View` élément qui définit un affichage de table pour l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="a8426-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a8426-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8426-153">See Also</span></span>

[<span data-ttu-id="a8426-154">ViewDefinitions, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="a8426-155">Name, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="a8426-156">ViewSelectedBy, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="a8426-157">Controls, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="a8426-158">GroupBy, élément pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a8426-159">TableControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="a8426-160">ListControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="a8426-161">WideControl, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="a8426-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="a8426-162">CustomControl, élément (format)</span><span class="sxs-lookup"><span data-stu-id="a8426-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="a8426-163">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8426-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
