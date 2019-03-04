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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856145"
---
# <a name="view-element-format"></a><span data-ttu-id="e3bd2-102">View, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-102">View Element (Format)</span></span>

<span data-ttu-id="e3bd2-103">Définit une vue qui affiche un ou plusieurs objets .NET.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="e3bd2-104">Il n’existe aucune limite au nombre de vues qui peuvent être définies dans un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="e3bd2-105">Élément d’affichage de configuration (Format) d’élément ViewDefinitions, élément (Format) (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3bd2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3bd2-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e3bd2-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e3bd2-107">Attributes and Elements</span></span>

<span data-ttu-id="e3bd2-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `View` élément.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="e3bd2-109">Vous devez spécifier un seul et unique les enfants d’éléments de contrôle, et vous devez spécifier le nom de la vue et les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="e3bd2-110">Définition des contrôles personnalisés, comment regrouper des objets et en spécifiant si la vue est hors-bande sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3bd2-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="e3bd2-111">Attributes</span></span>

<span data-ttu-id="e3bd2-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3bd2-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e3bd2-113">Child Elements</span></span>

|<span data-ttu-id="e3bd2-114">Élément</span><span class="sxs-lookup"><span data-stu-id="e3bd2-114">Element</span></span>|<span data-ttu-id="e3bd2-115">Description</span><span class="sxs-lookup"><span data-stu-id="e3bd2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3bd2-116">Élément de Controls pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="e3bd2-117">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e3bd2-118">Définit un ensemble de contrôles qui peuvent être référencés par leur nom à partir de la vue.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="e3bd2-119">Élément CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="e3bd2-120">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e3bd2-121">Définit un format de contrôle personnalisé pour la vue.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="e3bd2-122">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="e3bd2-123">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e3bd2-124">Définit comment les membres des objets .NET sont regroupés.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="e3bd2-125">Élément objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="e3bd2-126">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-126">Optional element.</span></span><br /><br /> <span data-ttu-id="e3bd2-127">Définit un format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="e3bd2-128">Name, élément pour afficher (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="e3bd2-129">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-129">Required element.</span></span><br /><br /> <span data-ttu-id="e3bd2-130">Spécifie le nom utilisé pour référencer la vue.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="e3bd2-131">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="e3bd2-132">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-132">Optional element.</span></span><br /><br /> <span data-ttu-id="e3bd2-133">Définit un format de table pour la vue.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="e3bd2-134">Élément ViewSelectedBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="e3bd2-135">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-135">Required element.</span></span><br /><br /> <span data-ttu-id="e3bd2-136">Définit les objets .NET qui affiche cette vue.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="e3bd2-137">Élément WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="e3bd2-138">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-138">Optional element.</span></span><br /><br /> <span data-ttu-id="e3bd2-139">Définit un (valeur unique) à l’échelle du format de liste pour la vue.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e3bd2-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e3bd2-140">Parent Elements</span></span>

|<span data-ttu-id="e3bd2-141">Élément</span><span class="sxs-lookup"><span data-stu-id="e3bd2-141">Element</span></span>|<span data-ttu-id="e3bd2-142">Description</span><span class="sxs-lookup"><span data-stu-id="e3bd2-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3bd2-143">Élément ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="e3bd2-144">Définit les vues utilisées pour afficher les objets.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e3bd2-145">Remarques</span><span class="sxs-lookup"><span data-stu-id="e3bd2-145">Remarks</span></span>

<span data-ttu-id="e3bd2-146">Pour plus d’informations sur les composants de différentes vues et des contrôles personnalisés, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="e3bd2-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="e3bd2-147">Composants de vue de table</span><span class="sxs-lookup"><span data-stu-id="e3bd2-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="e3bd2-148">Composants de vue de liste</span><span class="sxs-lookup"><span data-stu-id="e3bd2-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="e3bd2-149">Composants d’affichage plus large</span><span class="sxs-lookup"><span data-stu-id="e3bd2-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="e3bd2-150">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="e3bd2-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="e3bd2-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3bd2-151">Example</span></span>

<span data-ttu-id="e3bd2-152">Cet exemple montre un `View` élément qui définit un mode d’affichage pour le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet.</span><span class="sxs-lookup"><span data-stu-id="e3bd2-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e3bd2-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3bd2-153">See Also</span></span>

[<span data-ttu-id="e3bd2-154">Élément ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="e3bd2-155">Name, élément pour afficher (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="e3bd2-156">Élément ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="e3bd2-157">Élément de Controls pour la vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="e3bd2-158">Élément GroupBy de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="e3bd2-159">Élément de table (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="e3bd2-160">Élément objet ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="e3bd2-161">Élément WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="e3bd2-162">Élément CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3bd2-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="e3bd2-163">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3bd2-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
