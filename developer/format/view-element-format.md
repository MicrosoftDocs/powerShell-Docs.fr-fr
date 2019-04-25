---
title: Afficher l’élément (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083720"
---
# <a name="view-element-format"></a><span data-ttu-id="4d5eb-102">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-102">View Element (Format)</span></span>

<span data-ttu-id="4d5eb-103">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="4d5eb-104">Il n’existe aucune limite au nombre de vues qui peuvent être définies dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="4d5eb-105">Élément d’affichage de configuration (Format) d’élément ViewDefinitions, élément (Format) (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4d5eb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d5eb-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="4d5eb-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="4d5eb-107">Attributes and Elements</span></span>

<span data-ttu-id="4d5eb-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `View` élément.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="4d5eb-109">Vous devez spécifier un seul et unique les enfants d’éléments de contrôle, et vous devez spécifier le nom de la vue et les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="4d5eb-110">Définition des contrôles personnalisés, comment regrouper des objets et en spécifiant si la vue est hors-bande sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="4d5eb-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="4d5eb-111">Attributes</span></span>

<span data-ttu-id="4d5eb-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4d5eb-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4d5eb-113">Child Elements</span></span>

|<span data-ttu-id="4d5eb-114">Élément</span><span class="sxs-lookup"><span data-stu-id="4d5eb-114">Element</span></span>|<span data-ttu-id="4d5eb-115">Description</span><span class="sxs-lookup"><span data-stu-id="4d5eb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d5eb-116">Élément de Controls pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="4d5eb-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-117">Optional element.</span></span><br /><br /> <span data-ttu-id="4d5eb-118">Définit un ensemble de contrôles qui peuvent être référencés par leur nom à partir de la vue.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="4d5eb-119">Élément CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="4d5eb-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-120">Optional element.</span></span><br /><br /> <span data-ttu-id="4d5eb-121">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="4d5eb-122">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="4d5eb-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-123">Optional element.</span></span><br /><br /> <span data-ttu-id="4d5eb-124">Définit comment les membres des objets .NET sont regroupés.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="4d5eb-125">Élément objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="4d5eb-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-126">Optional element.</span></span><br /><br /> <span data-ttu-id="4d5eb-127">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="4d5eb-128">Name, élément pour afficher (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="4d5eb-129">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-129">Required element.</span></span><br /><br /> <span data-ttu-id="4d5eb-130">Spécifie le nom utilisé pour référencer la vue.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="4d5eb-131">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="4d5eb-132">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-132">Optional element.</span></span><br /><br /> <span data-ttu-id="4d5eb-133">Définit un format de table pour la vue.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="4d5eb-134">Élément ViewSelectedBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="4d5eb-135">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-135">Required element.</span></span><br /><br /> <span data-ttu-id="4d5eb-136">Définit les objets .NET qui affiche cette vue.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="4d5eb-137">Élément WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="4d5eb-138">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-138">Optional element.</span></span><br /><br /> <span data-ttu-id="4d5eb-139">Définit un (valeur unique) à l’échelle du format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4d5eb-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4d5eb-140">Parent Elements</span></span>

|<span data-ttu-id="4d5eb-141">Élément</span><span class="sxs-lookup"><span data-stu-id="4d5eb-141">Element</span></span>|<span data-ttu-id="4d5eb-142">Description</span><span class="sxs-lookup"><span data-stu-id="4d5eb-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d5eb-143">Élément ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="4d5eb-144">Définit les vues utilisées pour afficher les objets.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4d5eb-145">Remarques</span><span class="sxs-lookup"><span data-stu-id="4d5eb-145">Remarks</span></span>

<span data-ttu-id="4d5eb-146">Pour plus d’informations sur les composants de différentes vues et des contrôles personnalisés, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="4d5eb-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="4d5eb-147">Composants de vue de table</span><span class="sxs-lookup"><span data-stu-id="4d5eb-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="4d5eb-148">Composants de vue de liste</span><span class="sxs-lookup"><span data-stu-id="4d5eb-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="4d5eb-149">Composants d’affichage plus large</span><span class="sxs-lookup"><span data-stu-id="4d5eb-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="4d5eb-150">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="4d5eb-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="4d5eb-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d5eb-151">Example</span></span>

<span data-ttu-id="4d5eb-152">Cet exemple montre un `View` élément qui définit un mode d’affichage pour le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet.</span><span class="sxs-lookup"><span data-stu-id="4d5eb-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4d5eb-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d5eb-153">See Also</span></span>

[<span data-ttu-id="4d5eb-154">Élément ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="4d5eb-155">Name, élément pour afficher (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="4d5eb-156">Élément ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="4d5eb-157">Élément de Controls pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="4d5eb-158">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="4d5eb-159">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="4d5eb-160">Élément objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="4d5eb-161">Élément WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="4d5eb-162">Élément CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4d5eb-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="4d5eb-163">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d5eb-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
