---
title: Création d’une vue table | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: cbe81962a0f68d64506062898a8f21a1596cc29a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786150"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="bf595-102">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="bf595-102">Creating a Table View</span></span>

<span data-ttu-id="bf595-103">Un affichage de table affiche les données dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="bf595-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="bf595-104">Chaque ligne de la table représente un objet .NET, et chaque colonne de la table représente une propriété de l’objet ou une valeur de script.</span><span class="sxs-lookup"><span data-stu-id="bf595-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="bf595-105">Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet ou un sous-ensemble des propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="bf595-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="bf595-106">Affichage d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="bf595-106">A Table View Display</span></span>

<span data-ttu-id="bf595-107">L’exemple suivant montre comment Windows PowerShell affiche l’objet [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) qui est retourné par l’applet de commande [« obtient-service »](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="bf595-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="bf595-108">Pour cet objet, Windows PowerShell a défini une vue de table qui affiche la `Status` propriété, la `Name` propriété (cette propriété est une propriété d’alias pour la `ServiceName` propriété) et la `DisplayName` propriété.</span><span class="sxs-lookup"><span data-stu-id="bf595-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="bf595-109">Chaque ligne de la table représente un objet retourné par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bf595-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="bf595-110">Définition de la vue table</span><span class="sxs-lookup"><span data-stu-id="bf595-110">Defining the Table View</span></span>

<span data-ttu-id="bf595-111">Le code XML suivant montre le schéma de la vue table pour afficher [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) , objet.</span><span class="sxs-lookup"><span data-stu-id="bf595-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="bf595-112">Vous devez spécifier chaque propriété que vous souhaitez afficher dans la vue table.</span><span class="sxs-lookup"><span data-stu-id="bf595-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="bf595-113">Les éléments XML suivants sont utilisés pour définir un mode liste :</span><span class="sxs-lookup"><span data-stu-id="bf595-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="bf595-114">L’élément [View](./view-element-format.md) est l’élément parent de la vue table.</span><span class="sxs-lookup"><span data-stu-id="bf595-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="bf595-115">(Il s’agit du même élément parent pour les vues de contrôle de liste, larges et personnalisées.)</span><span class="sxs-lookup"><span data-stu-id="bf595-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="bf595-116">L’élément [Name](./name-element-for-view-format.md) spécifie le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="bf595-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="bf595-117">Cet élément est requis pour toutes les vues.</span><span class="sxs-lookup"><span data-stu-id="bf595-117">This element is required for all views.</span></span>

- <span data-ttu-id="bf595-118">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="bf595-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="bf595-119">Cet élément est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bf595-119">This element is required.</span></span>

- <span data-ttu-id="bf595-120">L’élément [GroupBy](./groupby-element-for-view-format.md) (non illustré dans cet exemple) définit le moment où un nouveau groupe d’objets est affiché.</span><span class="sxs-lookup"><span data-stu-id="bf595-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="bf595-121">Un nouveau groupe est démarré chaque fois que la valeur d’une propriété ou d’un script spécifique change.</span><span class="sxs-lookup"><span data-stu-id="bf595-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="bf595-122">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf595-122">This element is optional.</span></span>

- <span data-ttu-id="bf595-123">L’élément [Controls](./controls-element-for-view-format.md) (non illustré dans cet exemple) définit les contrôles personnalisés qui sont définis par la vue table.</span><span class="sxs-lookup"><span data-stu-id="bf595-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="bf595-124">Les contrôles vous permettent de spécifier davantage la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="bf595-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="bf595-125">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf595-125">This element is optional.</span></span> <span data-ttu-id="bf595-126">Une vue peut définir ses propres contrôles personnalisés, ou elle peut utiliser des contrôles communs qui peuvent être utilisés par n’importe quelle vue dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="bf595-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="bf595-127">Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="bf595-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="bf595-128">L’élément [HideTableHeaders](./hidetableheaders-element-format.md) (pas dans cet exemple) spécifie que la table n’affichera aucune étiquette en haut de la table.</span><span class="sxs-lookup"><span data-stu-id="bf595-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="bf595-129">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf595-129">This element is optional.</span></span>

- <span data-ttu-id="bf595-130">Élément [table (](./tablecontrol-element-format.md) qui définit les informations d’en-tête et de ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="bf595-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="bf595-131">Comme pour toutes les autres vues, une vue de table peut afficher les valeurs des propriétés ou valeurs d’objet générées par les scripts.</span><span class="sxs-lookup"><span data-stu-id="bf595-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="bf595-132">Définition des en-têtes de colonnes</span><span class="sxs-lookup"><span data-stu-id="bf595-132">Defining Column Headers</span></span>

1. <span data-ttu-id="bf595-133">L’élément [TableHeaders](./tableheaders-element-format.md) et ses éléments enfants définissent ce qui est affiché en haut de la table.</span><span class="sxs-lookup"><span data-stu-id="bf595-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="bf595-134">L’élément [TableColumnHeader](./tablecolumnheader-element-format.md) définit ce qui est affiché en haut d’une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="bf595-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="bf595-135">Spécifiez ces éléments dans l’ordre d’affichage des en-têtes.</span><span class="sxs-lookup"><span data-stu-id="bf595-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="bf595-136">Il n’y a pas de limite au nombre de ces éléments que vous pouvez utiliser, mais le nombre d’éléments [TableColumnHeader](./tablecolumnheader-element-format.md) dans votre vue de table doit être égal au nombre d’éléments [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="bf595-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="bf595-137">L’élément [label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) spécifie le texte qui est affiché.</span><span class="sxs-lookup"><span data-stu-id="bf595-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="bf595-138">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf595-138">This element is optional.</span></span>

4. <span data-ttu-id="bf595-139">L’élément [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) spécifie la largeur (en caractères) de la colonne.</span><span class="sxs-lookup"><span data-stu-id="bf595-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="bf595-140">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf595-140">This element is optional.</span></span>

5. <span data-ttu-id="bf595-141">L’élément [alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) spécifie le mode d’affichage de l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="bf595-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="bf595-142">L’étiquette peut être alignée à gauche, à droite ou centrée.</span><span class="sxs-lookup"><span data-stu-id="bf595-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="bf595-143">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf595-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="bf595-144">Définition des lignes de la table</span><span class="sxs-lookup"><span data-stu-id="bf595-144">Defining the Table Rows</span></span>

<span data-ttu-id="bf595-145">Les vues de table peuvent fournir une ou plusieurs définitions qui spécifient les données affichées dans les lignes de la table à l’aide des éléments enfants de l’élément [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="bf595-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="bf595-146">Notez que vous pouvez spécifier plusieurs définitions pour les lignes de la table, mais que les en-têtes pour les lignes restent les mêmes, quelle que soit la définition de ligne utilisée.</span><span class="sxs-lookup"><span data-stu-id="bf595-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="bf595-147">En règle générale, une table n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="bf595-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="bf595-148">Dans l’exemple suivant, la vue fournit une définition unique qui affiche les valeurs de plusieurs propriétés de [System. Diagnostics. Process ? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) , objet.</span><span class="sxs-lookup"><span data-stu-id="bf595-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="bf595-149">Une vue de table peut afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple) dans ses lignes.</span><span class="sxs-lookup"><span data-stu-id="bf595-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="bf595-150">Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour une ligne :</span><span class="sxs-lookup"><span data-stu-id="bf595-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="bf595-151">L’élément [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) et ses éléments enfants définissent ce qui est affiché dans les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="bf595-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="bf595-152">L’élément [TableRowEntry](./listentry-element-for-listcontrol-format.md) fournit une définition de la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="bf595-153">Au moins un [TableRowEntry](./listentry-element-for-listcontrol-format.md) est requis ; Toutefois, il n’existe pas de limite maximale pour le nombre d’éléments que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="bf595-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="bf595-154">Dans la plupart des cas, une vue n’a qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="bf595-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="bf595-155">L’élément [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) spécifie les objets qui sont affichés par une définition spécifique.</span><span class="sxs-lookup"><span data-stu-id="bf595-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="bf595-156">Cet élément est facultatif et n’est nécessaire que lorsque vous définissez plusieurs éléments [TableRowEntry](./listentry-element-for-listcontrol-format.md) qui affichent des objets différents.</span><span class="sxs-lookup"><span data-stu-id="bf595-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="bf595-157">L’élément [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) spécifie que le texte qui dépasse la largeur de colonne est affiché sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="bf595-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="bf595-158">Par défaut, le texte qui dépasse de la largeur de colonne est tronqué.</span><span class="sxs-lookup"><span data-stu-id="bf595-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="bf595-159">L’élément [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="bf595-160">L’élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="bf595-161">Un élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="bf595-162">La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="bf595-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="bf595-163">L’élément [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie la propriété dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="bf595-164">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="bf595-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="bf595-165">L’élément [scriptblock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="bf595-166">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="bf595-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="bf595-167">L’élément [FormatString](./label-element-for-listitem-for-listcontrol-format.md) spécifie un modèle de format qui définit le mode d’affichage de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="bf595-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="bf595-168">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf595-168">This element is optional.</span></span>

- <span data-ttu-id="bf595-169">L’élément [alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie la manière dont la valeur de la propriété ou du script est affichée.</span><span class="sxs-lookup"><span data-stu-id="bf595-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="bf595-170">La valeur peut être alignée à gauche, à droite ou centrée.</span><span class="sxs-lookup"><span data-stu-id="bf595-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="bf595-171">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="bf595-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="bf595-172">Définition des objets qui utilisent la vue table</span><span class="sxs-lookup"><span data-stu-id="bf595-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="bf595-173">Il existe deux façons de définir les objets .NET qui utilisent la vue table.</span><span class="sxs-lookup"><span data-stu-id="bf595-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="bf595-174">Vous pouvez utiliser l’élément [ViewSelectedBy](./viewselectedby-element-format.md) pour définir les objets qui peuvent être affichés par toutes les définitions de la vue, ou vous pouvez utiliser l’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) pour définir les objets qui sont affichés par une définition spécifique de la vue.</span><span class="sxs-lookup"><span data-stu-id="bf595-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="bf595-175">Dans la plupart des cas, une vue n’a qu’une seule définition, de sorte que les objets sont généralement définis par l’élément [ViewSelectedBy](./viewselectedby-element-format.md) .</span><span class="sxs-lookup"><span data-stu-id="bf595-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="bf595-176">L’exemple suivant montre comment définir les objets affichés par la vue table à l’aide des éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="bf595-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="bf595-177">Il n’existe aucune limite quant au nombre d’éléments [TypeName](./typename-element-for-viewselectedby-format.md) que vous pouvez spécifier, et leur ordre n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="bf595-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="bf595-178">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par la vue table :</span><span class="sxs-lookup"><span data-stu-id="bf595-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="bf595-179">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par le mode liste.</span><span class="sxs-lookup"><span data-stu-id="bf595-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="bf595-180">L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie l’objet .net qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="bf595-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="bf595-181">Le nom complet du type .NET est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bf595-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="bf595-182">Vous devez spécifier au moins un type ou un jeu de sélection pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bf595-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="bf595-183">L’exemple suivant utilise les éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="bf595-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="bf595-184">Utilisez des jeux de sélection dans lesquels vous avez un ensemble d’objets associés qui sont affichés à l’aide de plusieurs vues, par exemple lorsque vous définissez un affichage de liste et une vue de table pour les mêmes objets.</span><span class="sxs-lookup"><span data-stu-id="bf595-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="bf595-185">Pour plus d’informations sur la création d’un jeu de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="bf595-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="bf595-186">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage de liste :</span><span class="sxs-lookup"><span data-stu-id="bf595-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="bf595-187">L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par le mode liste.</span><span class="sxs-lookup"><span data-stu-id="bf595-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="bf595-188">L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) spécifie un ensemble d’objets qui peuvent être affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="bf595-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="bf595-189">Vous devez spécifier au moins un jeu de sélection ou un type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bf595-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="bf595-190">L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue de table à l’aide de l’élément [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="bf595-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="bf595-191">À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un jeu de sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="bf595-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="bf595-192">Pour plus d’informations sur la création de conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bf595-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="bf595-193">Lors de la création de plusieurs définitions de la vue table, vous ne pouvez pas spécifier d’en-têtes de colonnes différents.</span><span class="sxs-lookup"><span data-stu-id="bf595-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="bf595-194">Vous pouvez spécifier uniquement ce qui est affiché dans les lignes de la table, telles que les objets affichés.</span><span class="sxs-lookup"><span data-stu-id="bf595-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="bf595-195">Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par une définition spécifique de la vue Liste :</span><span class="sxs-lookup"><span data-stu-id="bf595-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="bf595-196">L’élément [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) définit les objets qui sont affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="bf595-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="bf595-197">L’élément [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) spécifie l’objet .net qui est affiché par la définition.</span><span class="sxs-lookup"><span data-stu-id="bf595-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="bf595-198">Lors de l’utilisation de cet élément, le nom complet du type .NET est requis.</span><span class="sxs-lookup"><span data-stu-id="bf595-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="bf595-199">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bf595-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="bf595-200">L’élément [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (non affiché) spécifie un ensemble d’objets qui peuvent être affichés par cette définition.</span><span class="sxs-lookup"><span data-stu-id="bf595-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="bf595-201">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bf595-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="bf595-202">L’élément [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (non affiché) spécifie une condition qui doit exister pour que cette définition soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="bf595-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="bf595-203">Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bf595-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="bf595-204">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bf595-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="bf595-205">Utilisation de chaînes de format</span><span class="sxs-lookup"><span data-stu-id="bf595-205">Using Format Strings</span></span>

<span data-ttu-id="bf595-206">La mise en forme des chaînes peut être ajoutée à une vue pour définir davantage la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="bf595-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="bf595-207">L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="bf595-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="bf595-208">Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :</span><span class="sxs-lookup"><span data-stu-id="bf595-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="bf595-209">L’élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="bf595-210">Un élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="bf595-211">La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="bf595-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="bf595-212">L’élément [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie la propriété dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="bf595-213">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="bf595-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="bf595-214">L’élément [FormatString](./label-element-for-listitem-for-listcontrol-format.md) spécifie un modèle de format qui définit le mode d’affichage de la valeur de la propriété ou du script.</span><span class="sxs-lookup"><span data-stu-id="bf595-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="bf595-215">Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script.</span><span class="sxs-lookup"><span data-stu-id="bf595-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="bf595-216">Les scripts peuvent appeler n’importe quelle méthode d’un objet.</span><span class="sxs-lookup"><span data-stu-id="bf595-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="bf595-217">Par conséquent, si un objet a une méthode, telle que `ToString` , qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.</span><span class="sxs-lookup"><span data-stu-id="bf595-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="bf595-218">L’élément XML suivant peut être utilisé pour appeler la `ToString` méthode :</span><span class="sxs-lookup"><span data-stu-id="bf595-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="bf595-219">L’élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) définit la propriété ou le script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="bf595-220">Un élément [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="bf595-221">La première entrée est affichée dans la première colonne, la deuxième entrée de la deuxième colonne, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="bf595-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="bf595-222">L’élément [scriptblock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="bf595-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="bf595-223">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="bf595-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf595-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf595-224">See Also</span></span>

[<span data-ttu-id="bf595-225">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf595-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
