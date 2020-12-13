---
ms.date: 09/13/2016
ms.topic: reference
title: Création d’une vue de table
description: Création d’une vue de table
ms.openlocfilehash: 035d42f7968a9e8babec692a7a5873e24b36cd97
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660295"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="b3361-103">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="b3361-103">Creating a Table View</span></span>

<span data-ttu-id="b3361-104">Un affichage de table affiche les données dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="b3361-104">A table view displays data in one or more columns.</span></span> <span data-ttu-id="b3361-105">Chaque ligne de la table représente un objet .NET, et chaque colonne de la table représente une propriété de l’objet ou une valeur de script.</span><span class="sxs-lookup"><span data-stu-id="b3361-105">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="b3361-106">Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet ou un sous-ensemble des propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="b3361-106">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="b3361-107">Affichage d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="b3361-107">A Table View Display</span></span>

<span data-ttu-id="b3361-108">L’exemple suivant montre comment Windows PowerShell affiche l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) qui est retourné par l’applet de commande [« obtient-service »](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="b3361-108">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="b3361-109">Pour cet objet, Windows PowerShell a défini une vue de table qui affiche la `Status` propriété, la `Name` propriété (cette propriété est une propriété d’alias pour la `ServiceName` propriété) et la `DisplayName` propriété.</span><span class="sxs-lookup"><span data-stu-id="b3361-109">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="b3361-110">Chaque ligne de la table représente un objet retourné par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b3361-110">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="b3361-111">Définition de la vue table</span><span class="sxs-lookup"><span data-stu-id="b3361-111">Defining the Table View</span></span>

<span data-ttu-id="b3361-112">Le code XML suivant montre le schéma de la vue table pour afficher [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) , objet.</span><span class="sxs-lookup"><span data-stu-id="b3361-112">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="b3361-113">Vous devez spécifier chaque propriété que vous souhaitez afficher dans la vue table.</span><span class="sxs-lookup"><span data-stu-id="b3361-113">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="b3361-114">Les éléments XML suivants sont utilisés pour définir un mode liste :</span><span class="sxs-lookup"><span data-stu-id="b3361-114">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="b3361-115">L’élément [View](./view-element-format.md) est l’élément parent de la vue table.</span><span class="sxs-lookup"><span data-stu-id="b3361-115">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="b3361-116">(Il s’agit du même élément parent pour les vues de contrôle de liste, larges et personnalisées.)</span><span class="sxs-lookup"><span data-stu-id="b3361-116">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="b3361-117">L’élément [Name](./name-element-for-view-format.md) spécifie le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="b3361-117">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="b3361-118">Cet élément est requis pour toutes les vues.</span><span class="sxs-lookup"><span data-stu-id="b3361-118">This element is required for all views.</span></span>

- <span data-ttu-id="b3361-119">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="b3361-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="b3361-120">Cet élément est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b3361-120">This element is required.</span></span>

- <span data-ttu-id="b3361-121">L’élément [GroupBy](./groupby-element-for-view-format.md) (non illustré dans cet exemple) définit le moment où un nouveau groupe d’objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="b3361-121">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="b3361-122">Un nouveau groupe est démarré chaque fois que la valeur d’une propriété ou d’un script spécifique change.</span><span class="sxs-lookup"><span data-stu-id="b3361-122">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="b3361-123">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b3361-123">This element is optional.</span></span>

- <span data-ttu-id="b3361-124">L’élément [Controls](./controls-element-for-view-format.md) (non illustré dans cet exemple) définit les contrôles personnalisés qui sont définis par la vue table.</span><span class="sxs-lookup"><span data-stu-id="b3361-124">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="b3361-125">Les contrôles vous permettent de spécifier davantage la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="b3361-125">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="b3361-126">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b3361-126">This element is optional.</span></span> <span data-ttu-id="b3361-127">Une vue peut définir ses propres contrôles personnalisés, ou elle peut utiliser des contrôles communs qui peuvent être utilisés par n’importe quelle vue dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b3361-127">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="b3361-128">Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b3361-128">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="b3361-129">L’élément [HideTableHeaders](./hidetableheaders-element-format.md) (pas dans cet exemple) spécifie que la table n’affichera aucune étiquette en haut de la table.</span><span class="sxs-lookup"><span data-stu-id="b3361-129">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="b3361-130">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b3361-130">This element is optional.</span></span>

- <span data-ttu-id="b3361-131">Élément [table (](./tablecontrol-element-format.md) qui définit les informations d’en-tête et de ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="b3361-131">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="b3361-132">Comme pour toutes les autres vues, une vue de table peut afficher les valeurs des propriétés ou valeurs d’objet générées par les scripts.</span><span class="sxs-lookup"><span data-stu-id="b3361-132">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="b3361-133">Définition des en-têtes de colonnes</span><span class="sxs-lookup"><span data-stu-id="b3361-133">Defining Column Headers</span></span>

1. <span data-ttu-id="b3361-134">L’élément [TableHeaders](./tableheaders-element-format.md) et ses éléments enfants définissent ce qui est affiché en haut de la table.</span><span class="sxs-lookup"><span data-stu-id="b3361-134">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="b3361-135">L’élément [TableColumnHeader](./tablecolumnheader-element-format.md) définit ce qui est affiché en haut d’une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="b3361-135">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="b3361-136">Spécifiez ces éléments dans l’ordre d’affichage des en-têtes.</span><span class="sxs-lookup"><span data-stu-id="b3361-136">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="b3361-137">Il n’y a pas de limite au nombre de ces éléments que vous pouvez utiliser, mais le nombre d’éléments [TableColumnHeader](./tablecolumnheader-element-format.md) dans votre vue de table doit être égal au nombre d’éléments [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="b3361-137">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="b3361-138">L’élément [label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) spécifie le texte qui est affiché.</span><span class="sxs-lookup"><span data-stu-id="b3361-138">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="b3361-139">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b3361-139">This element is optional.</span></span>

4. <span data-ttu-id="b3361-140">L’élément [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) spécifie la largeur (en caractères) de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b3361-140">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="b3361-141">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b3361-141">This element is optional.</span></span>

5. <span data-ttu-id="b3361-142">L’élément [alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) spécifie le mode d’affichage de l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="b3361-142">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="b3361-143">L’étiquette peut être alignée à gauche, à droite ou centrée.</span><span class="sxs-lookup"><span data-stu-id="b3361-143">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="b3361-144">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b3361-144">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="b3361-145">Définition des lignes de la table</span><span class="sxs-lookup"><span data-stu-id="b3361-145">Defining the Table Rows</span></span>

<span data-ttu-id="b3361-146">Les vues de table peuvent fournir une ou plusieurs définitions qui spécifient les données affichées dans les lignes de la table à l’aide des éléments enfants de l’élément [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="b3361-146">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="b3361-147">Notez que vous pouvez spécifier plusieurs définitions pour les lignes de la table, mais que les en-têtes pour les lignes restent les mêmes, quelle que soit la définition de ligne utilisée.</span><span class="sxs-lookup"><span data-stu-id="b3361-147">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="b3361-148">En règle générale, une table n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="b3361-148">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="b3361-149">Dans l’exemple suivant, la vue fournit une définition unique qui affiche les valeurs de plusieurs propriétés de [System. Diagnostics. Process ? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) , objet.</span><span class="sxs-lookup"><span data-stu-id="b3361-149">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="b3361-150">Une vue de table peut afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple) dans ses lignes.</span><span class="sxs-lookup"><span data-stu-id="b3361-150">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="b3361-151">Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour une ligne :</span><span class="sxs-lookup"><span data-stu-id="b3361-151">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="b3361-152">L’élément [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) et ses éléments enfants définissent ce qui est affiché dans les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="b3361-152">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="b3361-153">L’élément [TableRowEntry](./listentry-element-for-listcontrol-format.md) fournit une définition de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-153">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="b3361-154">Au moins un [TableRowEntry](./listentry-element-for-listcontrol-format.md) est requis ; Toutefois, il n’existe pas de limite maximale pour le nombre d’éléments que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="b3361-154">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="b3361-155">Dans la plupart des cas, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="b3361-155">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="b3361-156">L’élément [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) spécifie les objets qui sont affichés par une définition spécifique.</span><span class="sxs-lookup"><span data-stu-id="b3361-156">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="b3361-157">Cet élément est facultatif et n’est nécessaire que lorsque vous définissez plusieurs éléments [TableRowEntry](./listentry-element-for-listcontrol-format.md) qui affichent des objets différents.</span><span class="sxs-lookup"><span data-stu-id="b3361-157">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="b3361-158">L’élément [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) spécifie que le texte qui dépasse la largeur de colonne est affiché sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="b3361-158">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="b3361-159">Par défaut, le texte qui dépasse de la largeur de colonne est tronqué.</span><span class="sxs-lookup"><span data-stu-id="b3361-159">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="b3361-160">L’élément [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-160">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="b3361-161">L’élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-161">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="b3361-162">Un élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-162">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="b3361-163">La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="b3361-163">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="b3361-164">L’élément [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie la propriété dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-164">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="b3361-165">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="b3361-165">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="b3361-166">L’élément [scriptblock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-166">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="b3361-167">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="b3361-167">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="b3361-168">L’élément [FormatString](./label-element-for-listitem-for-listcontrol-format.md) spécifie un modèle de format qui définit le mode d’affichage de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="b3361-168">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="b3361-169">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b3361-169">This element is optional.</span></span>

- <span data-ttu-id="b3361-170">L’élément [alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie la manière dont la valeur de la propriété ou du script est affichée.</span><span class="sxs-lookup"><span data-stu-id="b3361-170">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="b3361-171">La valeur peut être alignée à gauche, à droite ou centrée.</span><span class="sxs-lookup"><span data-stu-id="b3361-171">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="b3361-172">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b3361-172">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="b3361-173">Définition des objets qui utilisent la vue table</span><span class="sxs-lookup"><span data-stu-id="b3361-173">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="b3361-174">Il existe deux façons de définir les objets .NET qui utilisent la vue table.</span><span class="sxs-lookup"><span data-stu-id="b3361-174">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="b3361-175">Vous pouvez utiliser l’élément [ViewSelectedBy](./viewselectedby-element-format.md) pour définir les objets qui peuvent être affichés par toutes les définitions de la vue, ou vous pouvez utiliser l’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) pour définir les objets qui sont affichés par une définition spécifique de la vue.</span><span class="sxs-lookup"><span data-stu-id="b3361-175">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="b3361-176">Dans la plupart des cas, une vue n’a qu’une seule définition, de sorte que les objets sont généralement définis par l’élément [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="b3361-176">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="b3361-177">L’exemple suivant montre comment définir les objets affichés par la vue table à l’aide des éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="b3361-177">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="b3361-178">Il n’existe aucune limite quant au nombre d’éléments [TypeName](./typename-element-for-viewselectedby-format.md) que vous pouvez spécifier, et leur ordre n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="b3361-178">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="b3361-179">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par la vue table :</span><span class="sxs-lookup"><span data-stu-id="b3361-179">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="b3361-180">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par le mode liste.</span><span class="sxs-lookup"><span data-stu-id="b3361-180">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="b3361-181">L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie l’objet .net qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="b3361-181">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="b3361-182">Le nom complet du type .NET est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b3361-182">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="b3361-183">Vous devez spécifier au moins un type ou un jeu de sélection pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b3361-183">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="b3361-184">L’exemple suivant utilise les éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="b3361-184">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="b3361-185">Utilisez des jeux de sélection dans lesquels vous avez un ensemble d’objets associés qui sont affichés à l’aide de plusieurs vues, par exemple lorsque vous définissez un affichage de liste et une vue de table pour les mêmes objets.</span><span class="sxs-lookup"><span data-stu-id="b3361-185">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="b3361-186">Pour plus d’informations sur la création d’un jeu de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b3361-186">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="b3361-187">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage de liste :</span><span class="sxs-lookup"><span data-stu-id="b3361-187">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="b3361-188">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par le mode liste.</span><span class="sxs-lookup"><span data-stu-id="b3361-188">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="b3361-189">L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) spécifie un ensemble d’objets qui peuvent être affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="b3361-189">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="b3361-190">Vous devez spécifier au moins un jeu de sélection ou un type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b3361-190">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="b3361-191">L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue de table à l’aide de l’élément [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="b3361-191">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="b3361-192">À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un jeu de sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b3361-192">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="b3361-193">Pour plus d’informations sur la création de conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b3361-193">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b3361-194">Lors de la création de plusieurs définitions de la vue table, vous ne pouvez pas spécifier d’en-têtes de colonnes différents.</span><span class="sxs-lookup"><span data-stu-id="b3361-194">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="b3361-195">Vous pouvez spécifier uniquement ce qui est affiché dans les lignes de la table, telles que les objets affichés.</span><span class="sxs-lookup"><span data-stu-id="b3361-195">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="b3361-196">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par une définition spécifique de la vue Liste :</span><span class="sxs-lookup"><span data-stu-id="b3361-196">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="b3361-197">L’élément [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) définit les objets qui sont affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="b3361-197">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="b3361-198">L’élément [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) spécifie l’objet .net qui est affiché par la définition.</span><span class="sxs-lookup"><span data-stu-id="b3361-198">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="b3361-199">Lors de l’utilisation de cet élément, le nom complet du type .NET est requis.</span><span class="sxs-lookup"><span data-stu-id="b3361-199">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="b3361-200">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b3361-200">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="b3361-201">L’élément [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (non affiché) spécifie un ensemble d’objets qui peuvent être affichés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="b3361-201">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="b3361-202">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b3361-202">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="b3361-203">L’élément [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (non affiché) spécifie une condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="b3361-203">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="b3361-204">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b3361-204">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="b3361-205">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b3361-205">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="b3361-206">Utilisation de chaînes de format</span><span class="sxs-lookup"><span data-stu-id="b3361-206">Using Format Strings</span></span>

<span data-ttu-id="b3361-207">La mise en forme des chaînes peut être ajoutée à une vue pour définir davantage la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="b3361-207">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="b3361-208">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="b3361-208">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="b3361-209">Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :</span><span class="sxs-lookup"><span data-stu-id="b3361-209">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="b3361-210">L’élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-210">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="b3361-211">Un élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-211">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="b3361-212">La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="b3361-212">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="b3361-213">L’élément [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie la propriété dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-213">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="b3361-214">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="b3361-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="b3361-215">L’élément [FormatString](./label-element-for-listitem-for-listcontrol-format.md) spécifie un modèle de format qui définit le mode d’affichage de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="b3361-215">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="b3361-216">Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script.</span><span class="sxs-lookup"><span data-stu-id="b3361-216">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="b3361-217">Les scripts peuvent appeler n’importe quelle méthode d’un objet.</span><span class="sxs-lookup"><span data-stu-id="b3361-217">Scripts can call any method of an object.</span></span> <span data-ttu-id="b3361-218">Par conséquent, si un objet a une méthode, telle que `ToString` , qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.</span><span class="sxs-lookup"><span data-stu-id="b3361-218">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="b3361-219">L’élément XML suivant peut être utilisé pour appeler la `ToString` méthode :</span><span class="sxs-lookup"><span data-stu-id="b3361-219">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="b3361-220">L’élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-220">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="b3361-221">Un élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-221">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="b3361-222">La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="b3361-222">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="b3361-223">L’élément [scriptblock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="b3361-223">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="b3361-224">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="b3361-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3361-225">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3361-225">See Also</span></span>

[<span data-ttu-id="b3361-226">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3361-226">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
