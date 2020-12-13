---
ms.date: 09/13/2016
ms.topic: reference
title: Vue d’ensemble des fichiers de mise en forme
description: Vue d’ensemble des fichiers de mise en forme
ms.openlocfilehash: b86119c304c895ec08ac67de693b3a052bc7a2a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667825"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="effd1-103">Vue d’ensemble des fichiers de mise en forme</span><span class="sxs-lookup"><span data-stu-id="effd1-103">Formatting File Overview</span></span>

<span data-ttu-id="effd1-104">Le format d’affichage des objets retournés par les commandes (applets de commande, fonctions et scripts) est défini à l’aide de fichiers de mise en forme (format.ps1fichiers XML).</span><span class="sxs-lookup"><span data-stu-id="effd1-104">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="effd1-105">Plusieurs de ces fichiers sont fournis par PowerShell pour définir le format d’affichage des objets retournés par les commandes fournies par PowerShell, telles que l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) retourné par l’applet de commande `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="effd1-105">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="effd1-106">Toutefois, vous pouvez également créer vos propres fichiers de mise en forme personnalisés pour remplacer les formats d’affichage par défaut ou vous pouvez écrire un fichier de mise en forme personnalisé pour définir l’affichage des objets retournés par vos propres commandes.</span><span class="sxs-lookup"><span data-stu-id="effd1-106">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="effd1-107">La mise en forme des fichiers ne détermine pas les éléments d’un objet qui sont retournés au pipeline.</span><span class="sxs-lookup"><span data-stu-id="effd1-107">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="effd1-108">Lorsqu’un objet est retourné au pipeline, tous les membres de cet objet sont disponibles, même si certains ne sont pas affichés.</span><span class="sxs-lookup"><span data-stu-id="effd1-108">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="effd1-109">PowerShell utilise les données de ces fichiers de mise en forme pour déterminer ce qui est affiché et comment les données affichées sont mises en forme.</span><span class="sxs-lookup"><span data-stu-id="effd1-109">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="effd1-110">Les données affichées peuvent inclure les propriétés d’un objet ou la valeur d’un script.</span><span class="sxs-lookup"><span data-stu-id="effd1-110">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="effd1-111">Les scripts sont utilisés si vous souhaitez afficher une valeur qui n’est pas directement disponible à partir des propriétés d’un objet, telles que l’ajout de la valeur de deux propriétés d’un objet, puis l’affichage de la somme sous la forme d’un élément de données.</span><span class="sxs-lookup"><span data-stu-id="effd1-111">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="effd1-112">La mise en forme des données affichées s’effectue en définissant des vues pour les objets que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="effd1-112">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="effd1-113">Vous pouvez définir une vue unique pour chaque objet, vous pouvez définir une vue unique pour plusieurs objets, ou vous pouvez définir plusieurs vues pour le même objet.</span><span class="sxs-lookup"><span data-stu-id="effd1-113">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="effd1-114">Il n’existe aucune limite quant au nombre d’affichages que vous pouvez définir.</span><span class="sxs-lookup"><span data-stu-id="effd1-114">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="effd1-115">Fonctionnalités courantes de mise en forme des fichiers</span><span class="sxs-lookup"><span data-stu-id="effd1-115">Common Features of Formatting Files</span></span>

<span data-ttu-id="effd1-116">Chaque fichier de mise en forme peut définir les composants suivants qui peuvent être partagés entre toutes les vues définies par le fichier :</span><span class="sxs-lookup"><span data-stu-id="effd1-116">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="effd1-117">Paramètre de configuration par défaut, par exemple si les données affichées dans les lignes des tables seront affichées sur la ligne suivante si les données sont plus longues que la largeur de la colonne.</span><span class="sxs-lookup"><span data-stu-id="effd1-117">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="effd1-118">Pour plus d’informations sur ces paramètres, consultez [définition des paramètres de configuration communs](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="effd1-118">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="effd1-119">Ensembles d’objets qui peuvent être affichés par l’une des vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="effd1-119">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="effd1-120">Pour plus d’informations sur ces jeux (appelés *jeux de sélection*), consultez [définition de jeux d’objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="effd1-120">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="effd1-121">Contrôles communs qui peuvent être utilisés par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="effd1-121">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="effd1-122">Les contrôles vous permettent de mieux contrôler la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="effd1-122">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="effd1-123">Pour plus d’informations sur les contrôles, consultez [définition de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="effd1-123">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="effd1-124">Mise en forme des vues</span><span class="sxs-lookup"><span data-stu-id="effd1-124">Formatting Views</span></span>

<span data-ttu-id="effd1-125">Les vues de mise en forme peuvent afficher des objets dans un format de tableau, un format de liste, un format étendu et un format personnalisé.</span><span class="sxs-lookup"><span data-stu-id="effd1-125">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="effd1-126">Pour l’essentiel, chaque définition de mise en forme est décrite par un ensemble de balises XML qui décrivent la vue.</span><span class="sxs-lookup"><span data-stu-id="effd1-126">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="effd1-127">Chaque vue contient le nom de la vue, les objets qui utilisent la vue et les éléments de la vue, tels que les informations de colonne et de ligne pour une vue de table.</span><span class="sxs-lookup"><span data-stu-id="effd1-127">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="effd1-128">La vue table répertorie les propriétés d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="effd1-128">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="effd1-129">Chaque colonne représente une propriété unique de l’objet ou une valeur de script.</span><span class="sxs-lookup"><span data-stu-id="effd1-129">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="effd1-130">Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet, un sous-ensemble des propriétés d’un objet, ou une combinaison de propriétés et de valeurs de script.</span><span class="sxs-lookup"><span data-stu-id="effd1-130">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="effd1-131">Chaque ligne de la table représente un objet retourné.</span><span class="sxs-lookup"><span data-stu-id="effd1-131">Each row of the table represents a returned object.</span></span> <span data-ttu-id="effd1-132">La création d’un affichage de table est très similaire à l’acheminement d’un objet vers l’applet de commande `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="effd1-132">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="effd1-133">Pour plus d’informations sur cette vue, consultez [vue table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="effd1-133">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="effd1-134">Le mode liste répertorie les propriétés d’un objet ou une valeur de script dans une seule colonne.</span><span class="sxs-lookup"><span data-stu-id="effd1-134">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="effd1-135">Chaque ligne de la liste affiche une étiquette facultative ou le nom de la propriété, suivi de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="effd1-135">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="effd1-136">La création d’un affichage de liste est très similaire à la conduite d’un objet à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="effd1-136">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="effd1-137">Pour plus d’informations sur cette vue, consultez [affichage de liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="effd1-137">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="effd1-138">Vue larges répertorie une seule propriété d’un objet ou une valeur de script dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="effd1-138">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="effd1-139">Il n’y a pas d’étiquette ou d’en-tête pour cette vue.</span><span class="sxs-lookup"><span data-stu-id="effd1-139">There is no label or header for this view.</span></span> <span data-ttu-id="effd1-140">La création d’un affichage étendu est très similaire à la conduite d’un objet à l’applet de commande `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="effd1-140">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="effd1-141">Pour plus d’informations sur cette vue, consultez [vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="effd1-141">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="effd1-142">Affichage personnalisé affiche une vue personnalisable des propriétés de l’objet ou des valeurs de script qui n’adhère pas à la structure rigide des vues de table, des affichages de liste ou des vues larges.</span><span class="sxs-lookup"><span data-stu-id="effd1-142">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="effd1-143">Vous pouvez définir une vue personnalisée autonome, ou vous pouvez définir une vue personnalisée qui est utilisée par une autre vue, telle qu’une vue de table ou une vue de liste.</span><span class="sxs-lookup"><span data-stu-id="effd1-143">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="effd1-144">La création d’un affichage personnalisé est très similaire à la conduite d’un objet à l’applet de commande `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="effd1-144">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="effd1-145">Pour plus d’informations sur cette vue, consultez [vue personnalisée](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="effd1-145">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="effd1-146">Composants d’une vue</span><span class="sxs-lookup"><span data-stu-id="effd1-146">Components of a View</span></span>

<span data-ttu-id="effd1-147">Les exemples XML suivants illustrent les composants XML de base d’une vue.</span><span class="sxs-lookup"><span data-stu-id="effd1-147">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="effd1-148">Les éléments XML individuels varient en fonction de la vue que vous souhaitez créer, mais les composants de base des vues sont les mêmes.</span><span class="sxs-lookup"><span data-stu-id="effd1-148">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="effd1-149">Pour commencer, chaque vue a un `Name` élément qui spécifie un nom convivial utilisé pour référencer la vue.</span><span class="sxs-lookup"><span data-stu-id="effd1-149">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="effd1-150">`ViewSelectedBy`élément qui définit les objets .net affichés par la vue et un élément de *contrôle* qui définit la vue.</span><span class="sxs-lookup"><span data-stu-id="effd1-150">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="effd1-151">Dans l’élément de contrôle, vous pouvez définir un ou plusieurs éléments d' *entrée* .</span><span class="sxs-lookup"><span data-stu-id="effd1-151">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="effd1-152">Si vous utilisez plusieurs définitions, vous devez spécifier les objets .NET qui utilisent chaque définition.</span><span class="sxs-lookup"><span data-stu-id="effd1-152">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="effd1-153">En général, une seule entrée, avec une seule définition, est nécessaire pour chaque contrôle.</span><span class="sxs-lookup"><span data-stu-id="effd1-153">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="effd1-154">Dans chaque élément d’entrée d’une vue, vous spécifiez les éléments *Item* qui définissent les propriétés .net ou les scripts affichés par cette vue.</span><span class="sxs-lookup"><span data-stu-id="effd1-154">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="effd1-155">Comme indiqué dans les exemples précédents, le fichier de mise en forme peut contenir plusieurs vues, une vue peut contenir plusieurs définitions et chaque définition peut contenir plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="effd1-155">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="effd1-156">Exemple d’affichage de table</span><span class="sxs-lookup"><span data-stu-id="effd1-156">Example of a Table View</span></span>

<span data-ttu-id="effd1-157">L’exemple suivant montre les balises XML utilisées pour définir une vue de table qui contient deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="effd1-157">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="effd1-158">L’élément [ViewDefinitions](./viewdefinitions-element-format.md) est l’élément conteneur pour toutes les vues définies dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="effd1-158">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="effd1-159">L’élément [View](./view-element-format.md) définit la table, la liste, la largeur ou la vue personnalisée spécifique.</span><span class="sxs-lookup"><span data-stu-id="effd1-159">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="effd1-160">Dans chaque élément de [vue](./view-element-format.md) , l’élément [Name](./name-element-for-view-format.md) spécifie le nom de la vue, l’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui utilisent la vue, et les différents éléments de contrôle (tels que l' `TableControl` élément illustré dans l’exemple suivant) définissent le type de la vue.</span><span class="sxs-lookup"><span data-stu-id="effd1-160">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="effd1-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="effd1-161">See Also</span></span>

[<span data-ttu-id="effd1-162">Création d’une vue de liste</span><span class="sxs-lookup"><span data-stu-id="effd1-162">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="effd1-163">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="effd1-163">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="effd1-164">Création d’une vue large</span><span class="sxs-lookup"><span data-stu-id="effd1-164">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="effd1-165">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="effd1-165">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="effd1-166">Écriture d’un fichier de mise en forme et de types PowerShell</span><span class="sxs-lookup"><span data-stu-id="effd1-166">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
