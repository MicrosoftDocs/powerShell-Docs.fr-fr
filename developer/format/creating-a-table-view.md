---
title: Création d’une vue de Table | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 832527ea4b042812c39934cd7e124201c6dc2ea4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861495"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="d1dd5-102">Création d’une vue de table</span><span class="sxs-lookup"><span data-stu-id="d1dd5-102">Creating a Table View</span></span>

<span data-ttu-id="d1dd5-103">Une vue de table affiche les données dans une ou plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="d1dd5-104">Chaque ligne dans la table représente un objet .NET, et chaque colonne de la table représente une propriété de l’objet ou une valeur de script.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="d1dd5-105">Vous pouvez définir une vue de table qui affiche toutes les propriétés d’un objet ou un sous-ensemble des propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="d1dd5-106">Un affichage de la vue Table</span><span class="sxs-lookup"><span data-stu-id="d1dd5-106">A Table View Display</span></span>

<span data-ttu-id="d1dd5-107">L’exemple suivant montre comment Windows PowerShell affiche le [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objet qui est retourné par la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="d1dd5-108">Pour cet objet, Windows PowerShell a défini une vue de table qui affiche le `Status` propriété, le `Name` propriété (cette propriété est une propriété d’alias pour le `ServiceName` propriété) et le `DisplayName` propriété.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="d1dd5-109">Chaque ligne dans la table représente un objet retourné par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="d1dd5-110">Définition de la vue de Table</span><span class="sxs-lookup"><span data-stu-id="d1dd5-110">Defining the Table View</span></span>

<span data-ttu-id="d1dd5-111">Le code XML suivant montre le schéma de vue de table pour afficher la [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objet.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="d1dd5-112">Vous devez spécifier chaque propriété que vous souhaitez afficher dans la vue de table.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="d1dd5-113">Les éléments XML suivants sont utilisés pour définir une vue de liste :</span><span class="sxs-lookup"><span data-stu-id="d1dd5-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="d1dd5-114">Le [vue](./view-element-format.md) élément est l’élément parent de la vue de table.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="d1dd5-115">(Ceci est le même élément parent pour obtenir la liste des vues de contrôle de large et personnalisées).</span><span class="sxs-lookup"><span data-stu-id="d1dd5-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="d1dd5-116">Le [nom](./name-element-for-view-format.md) élément spécifie le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="d1dd5-117">Cet élément est requis pour toutes les vues.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-117">This element is required for all views.</span></span>

- <span data-ttu-id="d1dd5-118">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui utilisent la vue.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="d1dd5-119">Cet élément est requis.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-119">This element is required.</span></span>

- <span data-ttu-id="d1dd5-120">Le [GroupBy](./groupby-element-for-view-format.md) élément (non affiché dans cet exemple) définit quand un nouveau groupe d’objets s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="d1dd5-121">Un nouveau groupe est démarré à chaque modification de la valeur d’une propriété spécifique ou d’un script.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="d1dd5-122">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-122">This element is optional.</span></span>

- <span data-ttu-id="d1dd5-123">Le [contrôles](./controls-element-for-view-format.md) élément (non affiché dans cet exemple) définit les contrôles personnalisés qui sont définies par la vue de table.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="d1dd5-124">Contrôles vous permettent de préciser la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="d1dd5-125">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-125">This element is optional.</span></span> <span data-ttu-id="d1dd5-126">Une vue peut définir ses propres contrôles personnalisés, ou il peut utiliser des contrôles communs qui peuvent être utilisées par n’importe quelle vue dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="d1dd5-127">Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d1dd5-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="d1dd5-128">Le [HideTableHeaders](./hidetableheaders-element-format.md) élément (pas montrer dans cet exemple) Spécifie que la table n’affiche pas toutes les étiquettes en haut de la table.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="d1dd5-129">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-129">This element is optional.</span></span>

- <span data-ttu-id="d1dd5-130">Le [table](./tablecontrol-element-format.md) élément qui définit les informations d’en-tête et de ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="d1dd5-131">Comme pour toutes les autres vues, une vue de table peut afficher les valeurs des propriétés de l’objet ou valeurs générées par des scripts.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="d1dd5-132">Définition d’en-têtes de colonne</span><span class="sxs-lookup"><span data-stu-id="d1dd5-132">Defining Column Headers</span></span>

1. <span data-ttu-id="d1dd5-133">Le [TableHeaders](./tableheaders-element-format.md) élément et ses éléments enfants définissent ce qui est affiché en haut de la table.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="d1dd5-134">Le [TableColumnHeader](./tablecolumnheader-element-format.md) élément définit ce qui est affiché en haut d’une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="d1dd5-135">Spécifiez ces éléments dans l’ordre que vous souhaitez les en-têtes affichés.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="d1dd5-136">Il n’existe aucune limite le nombre de ces élément que vous pouvez utiliser, mais le nombre de [TableColumnHeader](./tablecolumnheader-element-format.md) éléments dans votre affichage de la table doivent égal au nombre de [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) éléments que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="d1dd5-137">Le [étiquette](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) élément spécifie le texte qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="d1dd5-138">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-138">This element is optional.</span></span>

4. <span data-ttu-id="d1dd5-139">Le [largeur](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) élément spécifie la largeur (en caractères) de la colonne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="d1dd5-140">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-140">This element is optional.</span></span>

5. <span data-ttu-id="d1dd5-141">Le [alignement](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) élément spécifie la façon dont l’étiquette est affichée.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="d1dd5-142">L’étiquette peut être aligné à gauche, à droite, ou centré.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="d1dd5-143">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="d1dd5-144">Définir les lignes de Table</span><span class="sxs-lookup"><span data-stu-id="d1dd5-144">Defining the Table Rows</span></span>

<span data-ttu-id="d1dd5-145">Vues de table peuvent fournir une ou plusieurs définitions qui spécifient les données affichées dans les lignes de la table en utilisant les éléments enfants de la [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="d1dd5-146">Notez que vous pouvez spécifier plusieurs définitions pour les lignes de la table, mais les en-têtes de lignes reste la même, quel que soit la définition de ligne est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="d1dd5-147">En règle générale, une table aura qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="d1dd5-148">Dans l’exemple suivant, la vue fournit une définition unique qui affiche les valeurs de plusieurs propriétés de la [System.Diagnostics.Process ? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objet.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="d1dd5-149">Une vue de table peut afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple) dans ses lignes.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="d1dd5-150">Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour une ligne :</span><span class="sxs-lookup"><span data-stu-id="d1dd5-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="d1dd5-151">Le [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) élément et ses éléments enfants définissent ce qui est affiché dans les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="d1dd5-152">Le [TableRowEntry](./listentry-element-for-listcontrol-format.md) élément fournit une définition de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="d1dd5-153">Au moins un [TableRowEntry](./listentry-element-for-listcontrol-format.md) est requis ; Toutefois, il n’existe aucune limite maximale pour le nombre d’éléments que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="d1dd5-154">Dans la plupart des cas, une vue aura qu’une seule définition.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="d1dd5-155">Le [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) élément spécifie les objets qui sont affichés par une définition spécifique.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="d1dd5-156">Cet élément est facultatif et est nécessaire uniquement lorsque vous définissez plusieurs [TableRowEntry](./listentry-element-for-listcontrol-format.md) éléments qui affichent des objets différents.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="d1dd5-157">Le [encapsuler](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) élément spécifie que le texte qui dépasse la largeur de colonne s’affiche sur la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="d1dd5-158">Par défaut, le texte qui dépasse de la largeur de colonne est tronqué.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="d1dd5-159">Le [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) élément définit les propriétés ou les scripts dont les valeurs sont affichées dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="d1dd5-160">Le [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="d1dd5-161">Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="d1dd5-162">La première entrée s’affiche dans la première colonne, la deuxième entrée dans la deuxième colonne et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="d1dd5-163">Le [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) élément spécifie la propriété dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="d1dd5-164">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d1dd5-165">Le [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) élément spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="d1dd5-166">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="d1dd5-167">Le [FormatString](./label-element-for-listitem-for-listcontrol-format.md) élément spécifie un modèle de format qui définit comment la valeur de propriété ou un script s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="d1dd5-168">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-168">This element is optional.</span></span>

- <span data-ttu-id="d1dd5-169">Le [alignement](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) élément spécifie la façon dont la valeur de la propriété ou le script s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="d1dd5-170">La valeur peut être alignée à gauche, à droite, ou centrée.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="d1dd5-171">Cet élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="d1dd5-172">Définition des objets qui utilisent la vue de Table</span><span class="sxs-lookup"><span data-stu-id="d1dd5-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="d1dd5-173">Il existe deux façons de définir les objets .NET utilisent la vue de table.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="d1dd5-174">Vous pouvez utiliser la [ViewSelectedBy](./viewselectedby-element-format.md) élément pour définir les objets qui peuvent être affichées par toutes les définitions de la vue, ou vous pouvez utiliser la [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) élément pour définir quels objets sont affichés par un définition spécifique de la vue.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="d1dd5-175">Dans la plupart des cas, une vue n'a qu’une seule définition, donc les objets sont généralement définies par le [ViewSelectedBy](./viewselectedby-element-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="d1dd5-176">L’exemple suivant montre comment définir les objets qui sont affichés par la vue de table en utilisant le [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d1dd5-177">Il n’existe aucune limite au nombre de [TypeName](./typename-element-for-viewselectedby-format.md) éléments que vous pouvez spécifier, et leur ordre n’est pas significatif.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="d1dd5-178">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par la vue de table :</span><span class="sxs-lookup"><span data-stu-id="d1dd5-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="d1dd5-179">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par la vue de liste.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="d1dd5-180">Le [TypeName](./typename-element-for-viewselectedby-format.md) élément spécifie l’objet .NET qui est affiché par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="d1dd5-181">Le nom de type .NET complet est requis.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="d1dd5-182">Vous devez spécifier au moins un type ou la sélection définie pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d1dd5-183">L’exemple suivant utilise le [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d1dd5-184">Utiliser des jeux de sélection où vous avez un ensemble d’objets qui sont affichés à l’aide de plusieurs vues, comme lorsque vous définissez un affichage de liste et une vue de table pour les mêmes objets liés.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="d1dd5-185">Pour plus d’informations sur la création d’un jeu de sélection, consultez [définissant des ensembles de sélection](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d1dd5-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="d1dd5-186">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par la vue de liste :</span><span class="sxs-lookup"><span data-stu-id="d1dd5-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="d1dd5-187">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par la vue de liste.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="d1dd5-188">Le [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) élément spécifie un ensemble d’objets qui peuvent être affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="d1dd5-189">Vous devez spécifier au moins un jeu de sélection ou de type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d1dd5-190">L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue de table en utilisant le [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="d1dd5-191">À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un ensemble de la sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="d1dd5-192">Pour plus d’informations sur la façon de créer une sélection des conditions, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d1dd5-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d1dd5-193">Lorsque vous créez plusieurs définitions de la vue de table que vous ne pouvez pas spécifier des en-têtes de colonnes différentes.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="d1dd5-194">Vous pouvez spécifier uniquement ce qui est affiché dans les lignes de la table, telles que les objets sont affichés.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="d1dd5-195">Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par une définition spécifique de la vue de liste :</span><span class="sxs-lookup"><span data-stu-id="d1dd5-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="d1dd5-196">Le [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) élément définit les objets qui sont affichés par la définition.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="d1dd5-197">Le [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) élément spécifie l’objet .NET qui est affiché par la définition.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="d1dd5-198">Lorsque vous utilisez cet élément, le nom de type .NET complet est requis.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="d1dd5-199">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d1dd5-200">Le [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) élément (non illustré) spécifie un ensemble d’objets qui peuvent être affichées par cette définition.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="d1dd5-201">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d1dd5-202">Le [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) élément (non illustré) spécifie une condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="d1dd5-203">Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="d1dd5-204">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d1dd5-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="d1dd5-205">À l’aide de chaînes de Format</span><span class="sxs-lookup"><span data-stu-id="d1dd5-205">Using Format Strings</span></span>

<span data-ttu-id="d1dd5-206">Mise en forme de chaînes peuvent être ajoutés à une vue pour définir plus précisément la façon dont les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="d1dd5-207">L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="d1dd5-208">Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :</span><span class="sxs-lookup"><span data-stu-id="d1dd5-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="d1dd5-209">Le [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="d1dd5-210">Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="d1dd5-211">La première entrée s’affiche dans la première colonne, la deuxième entrée dans la deuxième colonne et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="d1dd5-212">Le [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) élément spécifie la propriété dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="d1dd5-213">Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d1dd5-214">Le [FormatString](./label-element-for-listitem-for-listcontrol-format.md) élément spécifie un modèle de format qui définit comment la valeur de propriété ou un script s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="d1dd5-215">Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="d1dd5-216">Scripts peuvent appeler n’importe quelle méthode d’un objet.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="d1dd5-217">Par conséquent, si un objet possède une méthode, tel que `ToString`, qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="d1dd5-218">L’élément XML suivant peut être utilisé pour appeler le `ToString` méthode :</span><span class="sxs-lookup"><span data-stu-id="d1dd5-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="d1dd5-219">Le [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément définit la propriété ou un script dont la valeur est affichée dans la colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="d1dd5-220">Un [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) élément est requis pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="d1dd5-221">La première entrée s’affiche dans la première colonne, la deuxième entrée dans la deuxième colonne et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="d1dd5-222">Le [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) élément spécifie le script dont la valeur est affichée dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="d1dd5-223">Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="d1dd5-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1dd5-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1dd5-224">See Also</span></span>

[<span data-ttu-id="d1dd5-225">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1dd5-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
