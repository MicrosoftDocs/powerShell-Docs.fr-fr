---
description: À compter de PowerShell 6, les vues par défaut des objets sont définies dans le code source PowerShell.  Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: 56bac204e33c39aa6192da9e6a899f00b0a4a743
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603662"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="a9073-104">À propos de Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="a9073-104">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="a9073-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="a9073-105">Short description</span></span>

<span data-ttu-id="a9073-106">À compter de PowerShell 6, les vues par défaut des objets sont définies dans le code source PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9073-106">Beginning in PowerShell 6, the default views for objects are defined in PowerShell source code.</span></span>

<span data-ttu-id="a9073-107">Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9073-107">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="a9073-108">Description longue</span><span class="sxs-lookup"><span data-stu-id="a9073-108">Long description</span></span>

<span data-ttu-id="a9073-109">À compter de PowerShell 6, les vues par défaut sont définies dans le code source PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9073-109">Beginning in PowerShell 6, the default views are defined in PowerShell source code.</span></span> <span data-ttu-id="a9073-110">Les `Format.ps1xml` fichiers de powershell 5,1 et versions antérieures n’existent pas dans PowerShell 6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="a9073-110">The `Format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="a9073-111">Le code source PowerShell définit l’affichage par défaut des objets dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9073-111">The PowerShell source code defines the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="a9073-112">Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9073-112">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="a9073-113">Quand PowerShell affiche un objet, il utilise les données des fichiers de mise en forme structurés pour déterminer l’affichage par défaut de l’objet.</span><span class="sxs-lookup"><span data-stu-id="a9073-113">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="a9073-114">Les données des fichiers de mise en forme déterminent si l’objet est affiché dans une table ou dans une liste, et détermine les propriétés qui sont affichées par défaut.</span><span class="sxs-lookup"><span data-stu-id="a9073-114">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="a9073-115">La mise en forme affecte uniquement l’affichage.</span><span class="sxs-lookup"><span data-stu-id="a9073-115">The formatting affects the display only.</span></span> <span data-ttu-id="a9073-116">Il n’affecte pas les propriétés d’objet qui sont passées dans le pipeline ou la manière dont elles sont passées.</span><span class="sxs-lookup"><span data-stu-id="a9073-116">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="a9073-117">`Format.ps1xml` les fichiers ne peuvent pas être utilisés pour personnaliser le format de sortie des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="a9073-117">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="a9073-118">Un `.ps1xml` fichier de mise en forme peut définir quatre vues différentes de chaque objet :</span><span class="sxs-lookup"><span data-stu-id="a9073-118">A `.ps1xml` formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="a9073-119">Table</span><span class="sxs-lookup"><span data-stu-id="a9073-119">Table</span></span>
- <span data-ttu-id="a9073-120">List</span><span class="sxs-lookup"><span data-stu-id="a9073-120">List</span></span>
- <span data-ttu-id="a9073-121">Large</span><span class="sxs-lookup"><span data-stu-id="a9073-121">Wide</span></span>
- <span data-ttu-id="a9073-122">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="a9073-122">Custom</span></span>

<span data-ttu-id="a9073-123">Par exemple, quand la sortie d’une `Get-ChildItem` commande est dirigée vers une `Format-List` commande, `Format-List` utilise la vue liste définie dans le code source pour déterminer comment afficher les objets fichier et dossier sous la forme d’une liste.</span><span class="sxs-lookup"><span data-stu-id="a9073-123">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the list view defined in the source code to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="a9073-124">Lorsqu’un fichier de mise en forme comprend plusieurs vues d’un objet, PowerShell applique la première vue qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="a9073-124">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="a9073-125">Dans un `Format.ps1xml` fichier personnalisé, une vue est définie par un ensemble de balises XML qui décrivent le nom de la vue, le type d’objet auquel elle peut être appliquée, les en-têtes de colonne et les propriétés affichées dans le corps de la vue.</span><span class="sxs-lookup"><span data-stu-id="a9073-125">In a custom `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="a9073-126">Le format dans les `Format.ps1xml` fichiers est appliqué juste avant que les données ne soient présentées à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a9073-126">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="a9073-127">Création de fichiers XML Format.ps1</span><span class="sxs-lookup"><span data-stu-id="a9073-127">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="a9073-128">Pour modifier le format d’affichage d’une vue d’objet existante, ou pour ajouter des vues pour les nouveaux objets, créez vos propres `Format.ps1xml` fichiers, puis ajoutez-les à votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9073-128">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="a9073-129">Pour créer un `Format.ps1xml` fichier afin de définir une vue personnalisée, utilisez les applets de commande [FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) et [Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) .</span><span class="sxs-lookup"><span data-stu-id="a9073-129">To create a `Format.ps1xml` file to define a custom view, use the [Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) and [Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) cmdlets.</span></span> <span data-ttu-id="a9073-130">Utilisez un éditeur de texte pour modifier le fichier.</span><span class="sxs-lookup"><span data-stu-id="a9073-130">Use a text editor to edit the file.</span></span> <span data-ttu-id="a9073-131">Le fichier peut être enregistré dans n’importe quel répertoire auquel PowerShell peut accéder, tel qu’un sous-répertoire de `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="a9073-131">The file can be saved to any directory that PowerShell can access, such as a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="a9073-132">Pour modifier la mise en forme d’une vue actuelle, localisez la vue dans le fichier de mise en forme, puis utilisez les balises pour modifier la vue.</span><span class="sxs-lookup"><span data-stu-id="a9073-132">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="a9073-133">Pour créer un affichage pour un nouveau type d’objet, créez un nouvel affichage ou utilisez une vue existante comme modèle.</span><span class="sxs-lookup"><span data-stu-id="a9073-133">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="a9073-134">Les balises sont décrites dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="a9073-134">The tags are described in the next section.</span></span> <span data-ttu-id="a9073-135">Vous pouvez ensuite supprimer toutes les autres vues du fichier afin que les modifications soient évidentes pour toute personne qui examine le fichier.</span><span class="sxs-lookup"><span data-stu-id="a9073-135">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="a9073-136">Une fois les modifications enregistrées, utilisez [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) pour ajouter le nouveau fichier à votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9073-136">After you save the changes, use the [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) to add the new file to your PowerShell session.</span></span> <span data-ttu-id="a9073-137">Si vous souhaitez que votre vue soit prioritaire sur une vue définie dans les fichiers intégrés, utilisez le paramètre **prependpath** .</span><span class="sxs-lookup"><span data-stu-id="a9073-137">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span> <span data-ttu-id="a9073-138">`Update-FormatData` affecte uniquement la session active.</span><span class="sxs-lookup"><span data-stu-id="a9073-138">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="a9073-139">Pour apporter la modification à toutes les sessions ultérieures, ajoutez la `Update-FormatData` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9073-139">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-add-calendar-data-to-culture-objects"></a><span data-ttu-id="a9073-140">Exemple : ajouter des données de calendrier à des objets de culture</span><span class="sxs-lookup"><span data-stu-id="a9073-140">Example: Add calendar data to culture objects</span></span>

<span data-ttu-id="a9073-141">Cet exemple montre comment modifier la mise en forme des objets culture **System. Globalization. CultureInfo** générés par l' `Get-Culture` applet de commande dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="a9073-141">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="a9073-142">Les commandes de l’exemple ajoutent la propriété **Calendar** à l’affichage de table par défaut d’objets culture.</span><span class="sxs-lookup"><span data-stu-id="a9073-142">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="a9073-143">Pour commencer, récupérez les données de format à partir du fichier de code source et créez un `Format.ps1xml` fichier qui contient la vue actuelle des objets de culture.</span><span class="sxs-lookup"><span data-stu-id="a9073-143">To begin, get the format data from the source code file and create a `Format.ps1xml` file that contains the current view of the culture objects.</span></span>

```powershell
Get-FormatData -TypeName System.Globalization.CultureInfo |
  Export-FormatData -Path $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="a9073-144">Ouvrez le `CultureInfo.Format.ps1xml` fichier dans un éditeur XML ou de texte, tel que Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="a9073-144">Open the `CultureInfo.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="a9073-145">Le code XML suivant définit les vues de l’objet **CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="a9073-145">The following XML defines the views of the **CultureInfo** object.</span></span>

<span data-ttu-id="a9073-146">Le `CultureInfo.Format.ps1xml` fichier doit ressembler à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a9073-146">The `CultureInfo.Format.ps1xml` file should look like the following sample:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.Globalization.CultureInfo</Name>
      <ViewSelectedBy>
        <TypeName>System.Globalization.CultureInfo</TypeName>
      </ViewSelectedBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Width>16</Width>
          </TableColumnHeader>
          <TableColumnHeader>
            <Width>16</Width>
          </TableColumnHeader>
          <TableColumnHeader />
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>LCID</PropertyName>
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
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="a9073-147">Créez une nouvelle colonne pour la propriété **Calendar** en ajoutant un nouvel ensemble de `<TableColumnHeader>` balises.</span><span class="sxs-lookup"><span data-stu-id="a9073-147">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="a9073-148">La valeur de la propriété **Calendar** peut être longue. vous devez donc spécifier une valeur de 45 caractères comme `<Width>` .</span><span class="sxs-lookup"><span data-stu-id="a9073-148">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>45</Width>
  </TableColumnHeader>
  <TableColumnHeader/>
</TableHeaders>
```

<span data-ttu-id="a9073-149">Ajoutez un nouvel élément de colonne pour **Calendar** dans les lignes de table à l’aide des `<TableColumnItem>` `<PropertyName` balises et :</span><span class="sxs-lookup"><span data-stu-id="a9073-149">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName>LCID</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Name</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Calendar</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>DisplayName</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>
```

<span data-ttu-id="a9073-150">Enregistrez et fermez le fichier.</span><span class="sxs-lookup"><span data-stu-id="a9073-150">Save and close the file.</span></span> <span data-ttu-id="a9073-151">Utilisez `Update-FormatData` pour ajouter le nouveau fichier de format à la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="a9073-151">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="a9073-152">Cet exemple utilise le paramètre **prependpath** pour placer le nouveau fichier dans un ordre de priorité plus élevé que celui du fichier d’origine.</span><span class="sxs-lookup"><span data-stu-id="a9073-152">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="a9073-153">Pour plus d’informations, voir [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span><span class="sxs-lookup"><span data-stu-id="a9073-153">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="a9073-154">Pour tester la modification, tapez `Get-Culture` et passez en revue la sortie qui comprend la propriété **Calendar** .</span><span class="sxs-lookup"><span data-stu-id="a9073-154">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID  Name   Calendar                                DisplayName
----  ----   --------                                -----------
1033  en-US  System.Globalization.GregorianCalendar  English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="a9073-155">XML dans Format.ps1fichiers XML</span><span class="sxs-lookup"><span data-stu-id="a9073-155">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="a9073-156">La définition de schéma complète se trouve dans [format. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) dans le référentiel de code source PowerShell sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="a9073-156">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="a9073-157">La section **ViewDefinitions** de chaque `Format.ps1xml` fichier contient les `<View>` balises qui définissent chaque vue.</span><span class="sxs-lookup"><span data-stu-id="a9073-157">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="a9073-158">Une `<View>` balise typique comprend les balises suivantes :</span><span class="sxs-lookup"><span data-stu-id="a9073-158">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="a9073-159">`<Name>` identifie le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="a9073-159">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="a9073-160">`<ViewSelectedBy>` Spécifie le ou les types d’objets auxquels la vue s’applique.</span><span class="sxs-lookup"><span data-stu-id="a9073-160">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="a9073-161">`<GroupBy>` spécifie la manière dont les éléments de la vue sont combinés dans des groupes.</span><span class="sxs-lookup"><span data-stu-id="a9073-161">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="a9073-162">`<TableControl>`, `<ListControl>` , `<WideControl>` et `<CustomControl>` contiennent les balises qui spécifient la façon dont chaque élément est affiché.</span><span class="sxs-lookup"><span data-stu-id="a9073-162">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="a9073-163">Balise ViewSelectedBy</span><span class="sxs-lookup"><span data-stu-id="a9073-163">ViewSelectedBy tag</span></span>

<span data-ttu-id="a9073-164">La `<ViewSelectedBy>` balise peut contenir une `<TypeName>` balise pour chaque type d’objet auquel s’applique la vue.</span><span class="sxs-lookup"><span data-stu-id="a9073-164">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="a9073-165">Ou peut contenir une `<SelectionSetName>` balise qui fait référence à un jeu de sélection défini ailleurs à l’aide d’une `<SelectionSet>` balise.</span><span class="sxs-lookup"><span data-stu-id="a9073-165">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="a9073-166">GroupBy (étiquette)</span><span class="sxs-lookup"><span data-stu-id="a9073-166">GroupBy tag</span></span>

<span data-ttu-id="a9073-167">La `<GroupBy>` balise contient une `<PropertyName>` balise qui spécifie la propriété d’objet par laquelle les éléments doivent être regroupés.</span><span class="sxs-lookup"><span data-stu-id="a9073-167">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="a9073-168">Elle contient également une `<Label>` balise qui spécifie une chaîne à utiliser comme étiquette pour chaque groupe ou une `<CustomControlName>` balise qui fait référence à un contrôle personnalisé défini ailleurs à l’aide d’une `<Control>` balise.</span><span class="sxs-lookup"><span data-stu-id="a9073-168">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="a9073-169">La `<Control>` balise contient une balise `<Name>` et une `<CustomControl>` balise.</span><span class="sxs-lookup"><span data-stu-id="a9073-169">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="a9073-170">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="a9073-170">TableControlTag</span></span>

<span data-ttu-id="a9073-171">La `<TableControl>` balise contient généralement `<TableHeaders>` des `<TableRowEntries>` balises et qui définissent la mise en forme des têtes et des lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="a9073-171">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="a9073-172">La `<TableHeaders>` balise contient généralement des `<TableColumnHeader>` balises qui contiennent des `<Label>` `<Width>` `<Alignment>` balises, et.</span><span class="sxs-lookup"><span data-stu-id="a9073-172">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="a9073-173">La `<TableRowEntries>` balise contient `<TableRowEntry>` des étiquettes pour chaque ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="a9073-173">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="a9073-174">La `<TableRowEntry>` balise contient une balise `<TableColumnItems>` qui contient une `<TableColumnItem>` balise pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="a9073-174">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="a9073-175">En règle générale, la `<TableColumnItem>` balise contient une `<PropertyName>` balise qui identifie la propriété de l’objet à afficher dans l’emplacement défini, ou une `<ScriptBlock>` balise qui contient le code de script qui calcule un résultat à afficher à l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="a9073-175">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="a9073-176">Les blocs de script peuvent également être utilisés ailleurs dans des emplacements où les résultats calculés peuvent être utiles.</span><span class="sxs-lookup"><span data-stu-id="a9073-176">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="a9073-177">La `<TableColumnItem>` balise peut également contenir une `<FormatString>` balise qui spécifie la façon dont la propriété ou les résultats calculés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="a9073-177">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="a9073-178">Balise ListControl</span><span class="sxs-lookup"><span data-stu-id="a9073-178">ListControl tag</span></span>

<span data-ttu-id="a9073-179">La `<ListControl>` balise contient généralement une `<ListEntries>` balise.</span><span class="sxs-lookup"><span data-stu-id="a9073-179">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="a9073-180">La `<ListEntries>` balise contient une `<ListEntry>` balise.</span><span class="sxs-lookup"><span data-stu-id="a9073-180">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="a9073-181">La `<ListEntry>` balise contient une `<ListItems>` balise.</span><span class="sxs-lookup"><span data-stu-id="a9073-181">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="a9073-182">La `<ListItems>` balise contient des `<ListItem>` balises qui contiennent des `<PropertyName>` balises.</span><span class="sxs-lookup"><span data-stu-id="a9073-182">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="a9073-183">Les `<PropertyName>` balises spécifient la propriété de l’objet à afficher à l’emplacement spécifié dans la liste.</span><span class="sxs-lookup"><span data-stu-id="a9073-183">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="a9073-184">Si la sélection de la vue est définie à l’aide d’un jeu de sélection, les `<ListControl>` `<ListEntry>` balises et peuvent également contenir une `<EntrySelectedBy>` balise qui contient une ou plusieurs `<TypeName>` balises.</span><span class="sxs-lookup"><span data-stu-id="a9073-184">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="a9073-185">Ces `<TypeName>` balises spécifient le type d’objet que la `<ListControl>` balise doit afficher.</span><span class="sxs-lookup"><span data-stu-id="a9073-185">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="a9073-186">Balise WideControl</span><span class="sxs-lookup"><span data-stu-id="a9073-186">WideControl tag</span></span>

<span data-ttu-id="a9073-187">La `<WideControl>` balise contient généralement une `<WideEntries>` balise.</span><span class="sxs-lookup"><span data-stu-id="a9073-187">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="a9073-188">La `<WideEntries>` balise contient une ou plusieurs `<WideEntry>` balises.</span><span class="sxs-lookup"><span data-stu-id="a9073-188">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="a9073-189">Une `<WideEntry>` balise contient généralement une `<PropertyName>` balise qui spécifie la propriété à afficher à l’emplacement spécifié dans la vue.</span><span class="sxs-lookup"><span data-stu-id="a9073-189">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="a9073-190">La `<PropertyName>` balise peut contenir une `<FormatString>` balise qui spécifie la manière dont la propriété doit être affichée.</span><span class="sxs-lookup"><span data-stu-id="a9073-190">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="a9073-191">CustomControl (balise)</span><span class="sxs-lookup"><span data-stu-id="a9073-191">CustomControl tag</span></span>

<span data-ttu-id="a9073-192">La `<CustomControl>` balise vous permet d’utiliser un bloc de script pour définir un format.</span><span class="sxs-lookup"><span data-stu-id="a9073-192">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="a9073-193">Une `<CustomControl>` balise contient généralement une `<CustomEntries>` balise qui contient plusieurs `<CustomEntry>` balises.</span><span class="sxs-lookup"><span data-stu-id="a9073-193">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="a9073-194">Chaque `<CustomEntry>` balise contient une `<CustomItem>` balise qui peut contenir diverses balises qui spécifient le contenu et la mise en forme de l’emplacement spécifié dans la vue, y compris les `<Text>` `<Indentation>` balises,, `<ExpressionBinding>` et `<NewLine>` .</span><span class="sxs-lookup"><span data-stu-id="a9073-194">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="a9073-195">Suivi de l’utilisation du fichier XML Format.ps1</span><span class="sxs-lookup"><span data-stu-id="a9073-195">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="a9073-196">Pour détecter les erreurs lors du chargement ou de l’application de `Format.ps1xml` fichiers, utilisez l' `Trace-Command` applet de commande avec l’un des composants de format suivants comme valeur du paramètre **Name** :</span><span class="sxs-lookup"><span data-stu-id="a9073-196">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="a9073-197">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="a9073-197">FormatFileLoading</span></span>
- <span data-ttu-id="a9073-198">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="a9073-198">FormatViewBinding</span></span>

<span data-ttu-id="a9073-199">Pour plus d’informations, consultez [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) et [obten-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span><span class="sxs-lookup"><span data-stu-id="a9073-199">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="a9073-200">Signature d’un fichier XML Format.ps1</span><span class="sxs-lookup"><span data-stu-id="a9073-200">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="a9073-201">Pour protéger les utilisateurs de votre `Format.ps1xml` fichier, signez le fichier à l’aide d’une signature numérique.</span><span class="sxs-lookup"><span data-stu-id="a9073-201">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="a9073-202">Pour plus d’informations, consultez [about_Signing](about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="a9073-202">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="a9073-203">Exemple de code XML pour une vue personnalisée Format-Table</span><span class="sxs-lookup"><span data-stu-id="a9073-203">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="a9073-204">L’exemple de code XML suivant crée une `Format-Table` vue personnalisée pour les objets **System. IO. DirectoryInfo** et **System. IO. FileInfo** créés par `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="a9073-204">The following XML sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="a9073-205">La vue personnalisée est nommée **mygciview** et ajoute la colonne **CreationTime** à la table.</span><span class="sxs-lookup"><span data-stu-id="a9073-205">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="a9073-206">Pour créer la vue personnalisée, utilisez les `Get-FormatData` applets de commande et `Export-FormatData` pour générer un `.ps1xml` fichier.</span><span class="sxs-lookup"><span data-stu-id="a9073-206">To create the custom view, use the `Get-FormatData` and `Export-FormatData` cmdlets to generate a `.ps1xml` file.</span></span> <span data-ttu-id="a9073-207">Modifiez ensuite votre `.ps1xml` fichier pour créer le code de votre vue personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a9073-207">Then, edit your `.ps1xml` file to create the code for your custom view.</span></span> <span data-ttu-id="a9073-208">Le `.ps1xml` fichier peut être stocké dans n’importe quel répertoire auquel PowerShell peut accéder.</span><span class="sxs-lookup"><span data-stu-id="a9073-208">The `.ps1xml` file can be stored in any directory that PowerShell can access.</span></span> <span data-ttu-id="a9073-209">Par exemple, un sous-répertoire de `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="a9073-209">For example, a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="a9073-210">Une fois le `.ps1xml` fichier créé, utilisez l' `Update-FormatData` applet de commande pour inclure la vue dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="a9073-210">After the `.ps1xml` file is created, use the `Update-FormatData` cmdlet to include the view in the current PowerShell session.</span></span> <span data-ttu-id="a9073-211">Vous pouvez aussi ajouter la commande de mise à jour à votre profil PowerShell Si vous avez besoin de la vue disponible dans toutes les sessions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9073-211">Or, add the update command to your PowerShell profile if you need the view available in all PowerShell sessions.</span></span>

<span data-ttu-id="a9073-212">Pour cet exemple, la vue personnalisée doit utiliser le format de table ; sinon, `Format-Table` échoue.</span><span class="sxs-lookup"><span data-stu-id="a9073-212">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="a9073-213">Utilisez `Format-Table` avec le paramètre **View** pour spécifier le nom de la vue personnalisée, **mygciview**, et mettez en forme la sortie de la table avec la colonne **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="a9073-213">Use `Format-Table` with the **View** parameter to specify the custom view's name, **mygciview**, and format the table's output with the **CreationTime** column.</span></span> <span data-ttu-id="a9073-214">Pour obtenir un exemple de la façon dont la commande est exécutée, consultez [format-table](xref:Microsoft.PowerShell.Utility.Format-Table).</span><span class="sxs-lookup"><span data-stu-id="a9073-214">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

> [!NOTE]
> <span data-ttu-id="a9073-215">Bien que vous puissiez obtenir le code XML de mise en forme du code source pour créer une vue personnalisée, un développement plus grand peut être nécessaire pour obtenir le résultat souhaité.</span><span class="sxs-lookup"><span data-stu-id="a9073-215">Although you can get the formatting XML from the source code to create a custom view, more development might be needed to get the desired result.</span></span>

<span data-ttu-id="a9073-216">Dans la `Get-FormatData` commande suivante, vous pouvez utiliser le paramètre **PowerShellVersion** pour vous assurer que toutes les informations de mise en forme locale sont retournées.</span><span class="sxs-lookup"><span data-stu-id="a9073-216">In the following `Get-FormatData` command, there's an alternative for the **PowerShellVersion** parameter to ensure that all local formatting information is returned.</span></span> <span data-ttu-id="a9073-217">Utilisez `-PowerShellVersion $PSVersionTable.PSVersion` plutôt qu’une version spécifique de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9073-217">Use `-PowerShellVersion $PSVersionTable.PSVersion` rather than a specific PowerShell version.</span></span>

```powershell
Get-FormatData -PowerShellVersion 5.1 -TypeName System.IO.DirectoryInfo |
   Export-FormatData -Path ./Mygciview.Format.ps1xml
Update-FormatData -AppendPath ./Mygciview.Format.ps1xml
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>mygciview</Name>
      <ViewSelectedBy>
        <TypeName>System.IO.DirectoryInfo</TypeName>
        <TypeName>System.IO.FileInfo</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>PSParentPath</PropertyName>
      </GroupBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Label>Mode</Label>
            <Width>7</Width>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>LastWriteTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>CreationTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Length</Label>
            <Width>14</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Name</Label>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <Wrap />
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>ModeWithoutHardLink</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>LastWriteTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>CreationTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Length</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Name</PropertyName>
              </TableColumnItem>
            </TableColumnItems>
          </TableRowEntry>
        </TableRowEntries>
      </TableControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="a9073-218">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9073-218">See also</span></span>

[<span data-ttu-id="a9073-219">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="a9073-219">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="a9073-220">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="a9073-220">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="a9073-221">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="a9073-221">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="a9073-222">Informations de référence sur le XML des schémas de format</span><span class="sxs-lookup"><span data-stu-id="a9073-222">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="a9073-223">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="a9073-223">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="a9073-224">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="a9073-224">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="a9073-225">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="a9073-225">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
