---
title: Vue d’ensemble du fichier de mise en forme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065731"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="e2bcc-102">Vue d’ensemble des fichiers de mise en forme</span><span class="sxs-lookup"><span data-stu-id="e2bcc-102">Formatting File Overview</span></span>

<span data-ttu-id="e2bcc-103">Le format d’affichage pour les objets qui sont retournés par les commandes (applets de commande, fonctions et des scripts) sont définis à l’aide de fichiers de mise en forme (fichiers format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="e2bcc-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="e2bcc-104">Plusieurs de ces fichiers sont fournis par PowerShell pour définir le format d’affichage pour les objets retournés par les commandes PowerShell fourni, comme le [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet retourné par la `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="e2bcc-105">Toutefois, vous pouvez également créer vos propres fichiers de mise en forme personnalisées pour remplacer les formats d’affichage par défaut, ou vous pouvez écrire un fichier de mise en forme personnalisé pour définir l’affichage des objets retournés par vos propres commandes.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e2bcc-106">Fichiers de mise en forme ne déterminent pas les éléments d’un objet qui sont retournés au pipeline.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="e2bcc-107">Lorsqu’un objet est retourné au pipeline, tous les membres de cet objet sont disponibles même si certaines ne sont pas affichés.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="e2bcc-108">PowerShell utilise les données dans ces fichiers de mise en forme pour déterminer ce qui est affiché et la mise en forme les données affichées.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="e2bcc-109">Les données affichées peuvent inclure les propriétés d’un objet ou la valeur d’un script.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="e2bcc-110">Les scripts sont utilisés si vous souhaitez afficher une valeur qui n’est pas disponible directement à partir des propriétés d’un objet, telles que l’ajout de la valeur des deux propriétés d’un objet, puis en affichant la somme en tant qu’un élément de données.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="e2bcc-111">Mise en forme des données affichées est effectuée en définissant des vues pour les objets que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="e2bcc-112">Vous pouvez définir une vue unique pour chaque objet, vous pouvez définir une vue unique pour plusieurs objets, ou vous pouvez définir plusieurs vues pour le même objet.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="e2bcc-113">Il n’existe aucune limite au nombre de vues que vous pouvez définir.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="e2bcc-114">Fonctionnalités communes de la mise en forme de fichiers</span><span class="sxs-lookup"><span data-stu-id="e2bcc-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="e2bcc-115">Chaque fichier de mise en forme peut définir les composants suivants qui peuvent être partagées entre toutes les vues définies par le fichier :</span><span class="sxs-lookup"><span data-stu-id="e2bcc-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="e2bcc-116">Paramètre de configuration, tels que si les données affichées dans les lignes de tables seront affichera sur la ligne suivante si les données sont supérieure à la largeur de la colonne par défaut.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="e2bcc-117">Pour plus d’informations sur ces paramètres, consultez [définissant les paramètres de Configuration courants](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="e2bcc-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="e2bcc-118">Ensembles d’objets qui peuvent être affichées par tous les affichages du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="e2bcc-119">Pour plus d’informations sur ces ensembles (appelé *des jeux de sélection*), consultez [définition définit des objets](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e2bcc-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="e2bcc-120">Contrôles communs qui peuvent être utilisées par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="e2bcc-121">Contrôles vous donnent un contrôle plus précis sur la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="e2bcc-122">Pour plus d’informations sur les contrôles, consultez [définition des contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e2bcc-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="e2bcc-123">Mise en forme de vues</span><span class="sxs-lookup"><span data-stu-id="e2bcc-123">Formatting Views</span></span>

<span data-ttu-id="e2bcc-124">Vues de mise en forme peuvent afficher des objets dans un format de table, format de liste, format large et format personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="e2bcc-125">La plupart du temps, chaque définition de mise en forme est décrite par un ensemble de balises XML qui décrivent la vue.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="e2bcc-126">Chaque vue contient le nom de la vue, les objets qui utilisent la vue et les éléments de la vue, telles que les informations de ligne et de colonne pour une vue de table.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="e2bcc-127">Affichage de tableau répertorie les propriétés d’un objet ou une valeur de bloc de script dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="e2bcc-128">Chaque colonne représente une propriété unique de l’objet ou une valeur de script.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="e2bcc-129">Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet, un sous-ensemble des propriétés d’un objet ou une combinaison de propriétés et valeurs de script.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="e2bcc-130">Chaque ligne de la table représente un objet retourné.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="e2bcc-131">Création d’une vue de table est très similaire à quand vous dirigez un objet à le `Format-Table` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="e2bcc-132">Pour plus d’informations sur cette vue, consultez [Table vue](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e2bcc-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="e2bcc-133">Liste de la vue répertorie les propriétés d’un objet ou une valeur de script dans une seule colonne.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="e2bcc-134">Chaque ligne de la liste affiche une étiquette facultative ou le nom de la propriété suivie de la valeur de la propriété ou un script.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="e2bcc-135">Création d’un affichage de liste est très similaire à la canalisation d’un objet à le `Format-List` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="e2bcc-136">Pour plus d’informations sur cette vue, consultez [mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e2bcc-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="e2bcc-137">Affichage large répertorie une seule propriété d’un objet ou une valeur de script dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="e2bcc-138">Il n’existe aucune étiquette ou un en-tête pour cette vue.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-138">There is no label or header for this view.</span></span> <span data-ttu-id="e2bcc-139">Création d’un affichage plus large est très similaire à la canalisation d’un objet à le `Format-Wide` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="e2bcc-140">Pour plus d’informations sur cette vue, consultez [Affichage large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e2bcc-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="e2bcc-141">Vue personnalisée affiche une vue personnalisable de propriétés de l’objet ou valeurs de script qui n’est pas conforme à la structure rigide de vues des tables, des affichages de listes ou des vues de larges.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="e2bcc-142">Vous pouvez définir une vue personnalisée autonome, ou vous pouvez définir une vue personnalisée qui est utilisée par un autre affichage, comme une liste ou un affichage de la table.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="e2bcc-143">Création d’une vue personnalisée est très similaire à la canalisation d’un objet à le `Format-Custom` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="e2bcc-144">Pour plus d’informations sur cette vue, consultez [vue personnalisée](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e2bcc-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="e2bcc-145">Composants d’une vue</span><span class="sxs-lookup"><span data-stu-id="e2bcc-145">Components of a View</span></span>

<span data-ttu-id="e2bcc-146">Les exemples XML suivants indiquent les composants de base XML d’une vue.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="e2bcc-147">Les éléments XML individuels varient selon le mode dans lequel vous souhaitez créer, mais les composants de base des vues sont identiques.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="e2bcc-148">Pour commencer, chaque vue a un `Name` élément qui spécifie un nom convivial qui est utilisé pour référencer la vue.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="e2bcc-149">un `ViewSelectedBy` élément qui définit les objets .NET sont affichés par la vue, et un *contrôle* élément qui définit la vue.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

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

<span data-ttu-id="e2bcc-150">Dans l’élément de contrôle, vous pouvez définir un ou plusieurs *entrée* éléments.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="e2bcc-151">Si vous utilisez plusieurs définitions, vous devez spécifier les objets .NET utilisent chaque définition.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="e2bcc-152">En général qu’une seule entrée, avec une seule définition, est nécessaire pour chaque contrôle.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

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

<span data-ttu-id="e2bcc-153">Au sein de chaque élément d’entrée d’une vue, vous spécifiez le *élément* éléments qui définissent les propriétés .NET ou les scripts qui sont affichés par cette vue.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="e2bcc-154">Comme indiqué dans les exemples précédents, le fichier de mise en forme peut contenir plusieurs vues, une vue peut contenir plusieurs définitions, et chaque définition peut contenir plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="e2bcc-155">Exemple d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="e2bcc-155">Example of a Table View</span></span>

<span data-ttu-id="e2bcc-156">L’exemple suivant montre les balises XML utilisés pour définir une vue de table qui contient deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="e2bcc-157">Le [ViewDefinitions](./viewdefinitions-element-format.md) élément est l’élément conteneur pour toutes les vues définies dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="e2bcc-158">Le [vue](./view-element-format.md) élément définit la table spécifique, la liste, l’affichage large ou personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="e2bcc-159">Dans chacun d’eux [vue](./view-element-format.md) élément, le [nom](./name-element-for-view-format.md) élément spécifie le nom de la vue, le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui utilisent la vue et les différentes contrôler les éléments (tels que le `TableControl` élément présenté dans l’exemple suivant) définissent le type de la vue.</span><span class="sxs-lookup"><span data-stu-id="e2bcc-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e2bcc-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2bcc-160">See Also</span></span>

[<span data-ttu-id="e2bcc-161">Création d’une vue liste</span><span class="sxs-lookup"><span data-stu-id="e2bcc-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e2bcc-162">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="e2bcc-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e2bcc-163">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="e2bcc-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e2bcc-164">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="e2bcc-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e2bcc-165">Écriture d’une mise en forme de PowerShell et le fichier de Types</span><span class="sxs-lookup"><span data-stu-id="e2bcc-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
