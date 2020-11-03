---
description: Les `Format.ps1xml` fichiers dans PowerShell définissent l’affichage par défaut des objets dans la console PowerShell. Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: be88007d23ab98b9c2f707b77f9c43578ba9887b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207666"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="b0725-105">À propos de Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="b0725-105">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="b0725-106">Description courte</span><span class="sxs-lookup"><span data-stu-id="b0725-106">Short description</span></span>

<span data-ttu-id="b0725-107">Les `Format.ps1xml` fichiers dans PowerShell définissent l’affichage par défaut des objets dans la console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0725-107">The `Format.ps1xml` files in PowerShell define the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="b0725-108">Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0725-108">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="b0725-109">Description longue</span><span class="sxs-lookup"><span data-stu-id="b0725-109">Long description</span></span>

<span data-ttu-id="b0725-110">`Format.ps1xml`Dans PowerShell, les fichiers définissent l’affichage par défaut des objets dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0725-110">The `Format.ps1xml` files in PowerShell define the default display of objects in PowerShell.</span></span> <span data-ttu-id="b0725-111">Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0725-111">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="b0725-112">Quand PowerShell affiche un objet, il utilise les données des fichiers de mise en forme structurés pour déterminer l’affichage par défaut de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b0725-112">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="b0725-113">Les données des fichiers de mise en forme déterminent si l’objet est affiché dans une table ou dans une liste, et détermine les propriétés qui sont affichées par défaut.</span><span class="sxs-lookup"><span data-stu-id="b0725-113">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="b0725-114">La mise en forme affecte uniquement l’affichage.</span><span class="sxs-lookup"><span data-stu-id="b0725-114">The formatting affects the display only.</span></span> <span data-ttu-id="b0725-115">Il n’affecte pas les propriétés d’objet qui sont passées dans le pipeline ou la manière dont elles sont passées.</span><span class="sxs-lookup"><span data-stu-id="b0725-115">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="b0725-116">`Format.ps1xml` les fichiers ne peuvent pas être utilisés pour personnaliser le format de sortie des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="b0725-116">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="b0725-117">PowerShell comprend sept fichiers de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b0725-117">PowerShell includes seven formatting files.</span></span> <span data-ttu-id="b0725-118">Ces fichiers se trouvent dans le répertoire d’installation ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="b0725-118">These files are located in the installation directory (`$PSHOME`).</span></span> <span data-ttu-id="b0725-119">Chaque fichier définit l’affichage d’un groupe d’objets Microsoft .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="b0725-119">Each file defines the display of a group of Microsoft .NET Framework objects:</span></span>

1. `Certificate.Format.ps1xml`

   <span data-ttu-id="b0725-120">Objets dans le magasin de certificats, tels que les certificats X. 509 et les magasins de certificats.</span><span class="sxs-lookup"><span data-stu-id="b0725-120">Objects in the Certificate store, such as X.509 certificates and certificate stores.</span></span>

1. `DotNetTypes.Format.ps1xml`

   <span data-ttu-id="b0725-121">Autres types de .NET Framework, tels que les objets CultureInfo, FileVersionInfo et EventLogEntry.</span><span class="sxs-lookup"><span data-stu-id="b0725-121">Other .NET Framework types, such as CultureInfo, FileVersionInfo, and EventLogEntry objects.</span></span>

1. `FileSystem.Format.ps1xml`

   <span data-ttu-id="b0725-122">Objets de système de fichiers, tels que les fichiers et les répertoires.</span><span class="sxs-lookup"><span data-stu-id="b0725-122">File system objects, such as files and directories.</span></span>

1. `Help.Format.ps1xml`

   <span data-ttu-id="b0725-123">Affichages de l’aide, tels que des affichages détaillés et complets, des paramètres et des exemples.</span><span class="sxs-lookup"><span data-stu-id="b0725-123">Help views, such as detailed and full views, parameters, and examples.</span></span>

1. `PowerShellCore.Format.ps1xml`

   <span data-ttu-id="b0725-124">Objets générés par les applets de commande PowerShell Core, tels que `Get-Member` et `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="b0725-124">Objects generated by PowerShell core cmdlets, such as `Get-Member` and `Get-History`.</span></span>

1. `PowerShellTrace.Format.ps1xml`

   <span data-ttu-id="b0725-125">Les objets de trace, tels que ceux générés par l’applet de commande `Trace-Command` .</span><span class="sxs-lookup"><span data-stu-id="b0725-125">Trace objects, such as those generated by the `Trace-Command` cmdlet.</span></span>

1. `Registry.Format.ps1xml`

   <span data-ttu-id="b0725-126">Des objets de Registre, tels que des clés et des entrées.</span><span class="sxs-lookup"><span data-stu-id="b0725-126">Registry objects, such as keys and entries.</span></span>

<span data-ttu-id="b0725-127">Un fichier de mise en forme peut définir quatre vues différentes de chaque objet :</span><span class="sxs-lookup"><span data-stu-id="b0725-127">A formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="b0725-128">Table de charge de travail</span><span class="sxs-lookup"><span data-stu-id="b0725-128">Table</span></span>
- <span data-ttu-id="b0725-129">List</span><span class="sxs-lookup"><span data-stu-id="b0725-129">List</span></span>
- <span data-ttu-id="b0725-130">Large</span><span class="sxs-lookup"><span data-stu-id="b0725-130">Wide</span></span>
- <span data-ttu-id="b0725-131">Custom</span><span class="sxs-lookup"><span data-stu-id="b0725-131">Custom</span></span>

<span data-ttu-id="b0725-132">Par exemple, quand la sortie d’une `Get-ChildItem` commande est dirigée vers une `Format-List` commande, `Format-List` utilise la vue dans le `FileSystem.Format.ps1xml` fichier pour déterminer comment afficher les objets fichier et dossier sous la forme d’une liste.</span><span class="sxs-lookup"><span data-stu-id="b0725-132">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the view in the `FileSystem.Format.ps1xml` file to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="b0725-133">Lorsqu’un fichier de mise en forme comprend plusieurs vues d’un objet, PowerShell applique la première vue qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="b0725-133">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="b0725-134">Dans un `Format.ps1xml` fichier, une vue est définie par un ensemble de balises XML qui décrivent le nom de la vue, le type d’objet auquel elle peut être appliquée, les en-têtes de colonne et les propriétés affichées dans le corps de la vue.</span><span class="sxs-lookup"><span data-stu-id="b0725-134">In a `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="b0725-135">Le format dans les `Format.ps1xml` fichiers est appliqué juste avant que les données ne soient présentées à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b0725-135">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="b0725-136">Création de fichiers XML Format.ps1</span><span class="sxs-lookup"><span data-stu-id="b0725-136">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="b0725-137">Les `.ps1xml` fichiers qui sont installés avec PowerShell sont signés numériquement pour empêcher la falsification, car la mise en forme peut inclure des blocs de script.</span><span class="sxs-lookup"><span data-stu-id="b0725-137">The `.ps1xml` files that are installed with PowerShell are digitally signed to prevent tampering because the formatting can include script blocks.</span></span> <span data-ttu-id="b0725-138">Pour modifier le format d’affichage d’une vue d’objet existante, ou pour ajouter des vues pour les nouveaux objets, créez vos propres `Format.ps1xml` fichiers, puis ajoutez-les à votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0725-138">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="b0725-139">Pour créer un fichier, copiez un `Format.ps1xml` fichier existant.</span><span class="sxs-lookup"><span data-stu-id="b0725-139">To create a new file, copy an existing `Format.ps1xml` file.</span></span> <span data-ttu-id="b0725-140">Le nouveau fichier peut avoir n’importe quel nom, mais il doit avoir une `.ps1xml` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="b0725-140">The new file can have any name, but it must have a `.ps1xml` file name extension.</span></span> <span data-ttu-id="b0725-141">Vous pouvez placer le nouveau fichier dans n’importe quel répertoire accessible à PowerShell, mais il est utile de placer les fichiers dans le répertoire d’installation de PowerShell ( `$PSHOME` ) ou dans un sous-répertoire du répertoire d’installation.</span><span class="sxs-lookup"><span data-stu-id="b0725-141">You can place the new file in any directory that is accessible to PowerShell, but it's useful to place the files in the PowerShell installation directory (`$PSHOME`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="b0725-142">Pour modifier la mise en forme d’une vue actuelle, localisez la vue dans le fichier de mise en forme, puis utilisez les balises pour modifier la vue.</span><span class="sxs-lookup"><span data-stu-id="b0725-142">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="b0725-143">Pour créer un affichage pour un nouveau type d’objet, créez un nouvel affichage ou utilisez une vue existante comme modèle.</span><span class="sxs-lookup"><span data-stu-id="b0725-143">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="b0725-144">Les balises sont décrites dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="b0725-144">The tags are described in the next section.</span></span> <span data-ttu-id="b0725-145">Vous pouvez ensuite supprimer toutes les autres vues du fichier afin que les modifications soient évidentes pour toute personne qui examine le fichier.</span><span class="sxs-lookup"><span data-stu-id="b0725-145">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="b0725-146">Une fois les modifications enregistrées, utilisez l' `Update-FormatData` applet de commande pour ajouter le nouveau fichier à votre session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0725-146">After you save the changes, use the `Update-FormatData` cmdlet to add the new file to your PowerShell session.</span></span> <span data-ttu-id="b0725-147">Si vous souhaitez que votre vue soit prioritaire sur une vue définie dans les fichiers intégrés, utilisez le paramètre **prependpath** .</span><span class="sxs-lookup"><span data-stu-id="b0725-147">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span>
<span data-ttu-id="b0725-148">`Update-FormatData` affecte uniquement la session active.</span><span class="sxs-lookup"><span data-stu-id="b0725-148">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="b0725-149">Pour apporter la modification à toutes les sessions ultérieures, ajoutez la `Update-FormatData` commande à votre profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0725-149">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-adding-calendar-data-to-culture-objects"></a><span data-ttu-id="b0725-150">Exemple : ajout de données de calendrier à des objets de culture</span><span class="sxs-lookup"><span data-stu-id="b0725-150">Example: Adding calendar data to culture objects</span></span>

<span data-ttu-id="b0725-151">Cet exemple montre comment modifier la mise en forme des objets culture **System. Globalization. CultureInfo** générés par l' `Get-Culture` applet de commande dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="b0725-151">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="b0725-152">Les commandes de l’exemple ajoutent la propriété **Calendar** à l’affichage de table par défaut d’objets culture.</span><span class="sxs-lookup"><span data-stu-id="b0725-152">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="b0725-153">La première étape consiste à trouver le `Format.ps1xml` fichier qui contient la vue actuelle des objets culture.</span><span class="sxs-lookup"><span data-stu-id="b0725-153">The first step is to find the `Format.ps1xml` file that contains the current view of the culture objects.</span></span> <span data-ttu-id="b0725-154">La `Select-String` commande suivante recherche le fichier :</span><span class="sxs-lookup"><span data-stu-id="b0725-154">The following `Select-String` command finds the file:</span></span>

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.Globalization.CultureInfo"
}

Select-String @Parms
```

```Output
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:113:
     <Name>System.Globalization.CultureInfo</Name>
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:115:
<TypeName>System.Globalization.CultureInfo</TypeName>
```

<span data-ttu-id="b0725-155">Cette commande révèle que la définition se trouve dans le `DotNetTypes.Format.ps1xml` fichier.</span><span class="sxs-lookup"><span data-stu-id="b0725-155">This command reveals that the definition is in the `DotNetTypes.Format.ps1xml` file.</span></span>

<span data-ttu-id="b0725-156">La commande suivante copie le contenu du fichier dans un nouveau fichier, `MyDotNetTypes.Format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="b0725-156">The next command copies the file contents to a new file, `MyDotNetTypes.Format.ps1xml`.</span></span>

```powershell
Copy-Item $PSHome\DotNetTypes.format.ps1xml MyDotNetTypes.Format.ps1xml
```

<span data-ttu-id="b0725-157">Ouvrez le `MyDotNetTypes.Format.ps1xml` fichier dans un éditeur XML ou de texte, tel que Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="b0725-157">Open the `MyDotNetTypes.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="b0725-158">Recherchez la section de l’objet **System. Globalization. CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="b0725-158">Find the **System.Globalization.CultureInfo** object section.</span></span> <span data-ttu-id="b0725-159">Le code XML suivant définit les vues de l’objet **CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="b0725-159">The following XML defines the views of the **CultureInfo** object.</span></span> <span data-ttu-id="b0725-160">L’objet n’a qu’une vue **table (** .</span><span class="sxs-lookup"><span data-stu-id="b0725-160">The object has only a **TableControl** view.</span></span>

```xml
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
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
```

<span data-ttu-id="b0725-161">Supprimez le reste du fichier, à l’exception des balises d’ouverture,, et, ainsi que des balises de `<?xml>` `<Configuration>` `<ViewDefinitions>` fermeture `<ViewDefinitions>` et `<Configuration>` .</span><span class="sxs-lookup"><span data-stu-id="b0725-161">Delete the remainder of the file, except for the opening `<?xml>`, `<Configuration>`, and `<ViewDefinitions>` tags and the closing `<ViewDefinitions>` and `<Configuration>` tags.</span></span> <span data-ttu-id="b0725-162">S’il existe une signature numérique, supprimez-la de votre `Format.ps1xml` fichier personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b0725-162">If there is a digital signature, delete it from your custom `Format.ps1xml`file.</span></span>

<span data-ttu-id="b0725-163">Le `MyDotNetTypes.Format.ps1xml` fichier doit maintenant ressembler à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b0725-163">The `MyDotNetTypes.Format.ps1xml` file should now look like the following sample:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
<ViewDefinitions>
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
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
      <TableColumnHeader/>
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

<span data-ttu-id="b0725-164">Créez une nouvelle colonne pour la propriété **Calendar** en ajoutant un nouvel ensemble de `<TableColumnHeader>` balises.</span><span class="sxs-lookup"><span data-stu-id="b0725-164">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="b0725-165">La valeur de la propriété **Calendar** peut être longue. vous devez donc spécifier une valeur de 45 caractères comme `<Width>` .</span><span class="sxs-lookup"><span data-stu-id="b0725-165">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

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

<span data-ttu-id="b0725-166">Ajoutez un nouvel élément de colonne pour **Calendar** dans les lignes de table à l’aide des `<TableColumnItem>` `<PropertyName` balises et :</span><span class="sxs-lookup"><span data-stu-id="b0725-166">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

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

<span data-ttu-id="b0725-167">Enregistrez et fermez le fichier.</span><span class="sxs-lookup"><span data-stu-id="b0725-167">Save and close the file.</span></span> <span data-ttu-id="b0725-168">Utilisez `Update-FormatData` pour ajouter le nouveau fichier de format à la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="b0725-168">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="b0725-169">Cet exemple utilise le paramètre **prependpath** pour placer le nouveau fichier dans un ordre de priorité plus élevé que celui du fichier d’origine.</span><span class="sxs-lookup"><span data-stu-id="b0725-169">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="b0725-170">Pour plus d’informations, voir [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span><span class="sxs-lookup"><span data-stu-id="b0725-170">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $PSHOME\MyDotNetTypes.Format.ps1xml
```

<span data-ttu-id="b0725-171">Pour tester la modification, tapez `Get-Culture` et passez en revue la sortie qui comprend la propriété **Calendar** .</span><span class="sxs-lookup"><span data-stu-id="b0725-171">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID Name  Calendar                               DisplayName
---- ----  --------                               -----------
1033 en-US System.Globalization.GregorianCalendar English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="b0725-172">XML dans Format.ps1fichiers XML</span><span class="sxs-lookup"><span data-stu-id="b0725-172">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="b0725-173">La définition de schéma complète se trouve dans [format. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) dans le référentiel de code source PowerShell sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="b0725-173">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="b0725-174">La section **ViewDefinitions** de chaque `Format.ps1xml` fichier contient les `<View>` balises qui définissent chaque vue.</span><span class="sxs-lookup"><span data-stu-id="b0725-174">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="b0725-175">Une `<View>` balise typique comprend les balises suivantes :</span><span class="sxs-lookup"><span data-stu-id="b0725-175">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="b0725-176">`<Name>` identifie le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="b0725-176">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="b0725-177">`<ViewSelectedBy>` Spécifie le ou les types d’objets auxquels la vue s’applique.</span><span class="sxs-lookup"><span data-stu-id="b0725-177">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="b0725-178">`<GroupBy>` spécifie la manière dont les éléments de la vue sont combinés dans des groupes.</span><span class="sxs-lookup"><span data-stu-id="b0725-178">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="b0725-179">`<TableControl>`, `<ListControl>` , `<WideControl>` et `<CustomControl>` contiennent les balises qui spécifient la façon dont chaque élément est affiché.</span><span class="sxs-lookup"><span data-stu-id="b0725-179">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="b0725-180">Balise ViewSelectedBy</span><span class="sxs-lookup"><span data-stu-id="b0725-180">ViewSelectedBy tag</span></span>

<span data-ttu-id="b0725-181">La `<ViewSelectedBy>` balise peut contenir une `<TypeName>` balise pour chaque type d’objet auquel s’applique la vue.</span><span class="sxs-lookup"><span data-stu-id="b0725-181">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="b0725-182">Ou peut contenir une `<SelectionSetName>` balise qui fait référence à un jeu de sélection défini ailleurs à l’aide d’une `<SelectionSet>` balise.</span><span class="sxs-lookup"><span data-stu-id="b0725-182">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="b0725-183">GroupBy (étiquette)</span><span class="sxs-lookup"><span data-stu-id="b0725-183">GroupBy tag</span></span>

<span data-ttu-id="b0725-184">La `<GroupBy>` balise contient une `<PropertyName>` balise qui spécifie la propriété d’objet par laquelle les éléments doivent être regroupés.</span><span class="sxs-lookup"><span data-stu-id="b0725-184">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="b0725-185">Elle contient également une `<Label>` balise qui spécifie une chaîne à utiliser comme étiquette pour chaque groupe ou une `<CustomControlName>` balise qui fait référence à un contrôle personnalisé défini ailleurs à l’aide d’une `<Control>` balise.</span><span class="sxs-lookup"><span data-stu-id="b0725-185">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="b0725-186">La `<Control>` balise contient une balise `<Name>` et une `<CustomControl>` balise.</span><span class="sxs-lookup"><span data-stu-id="b0725-186">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="b0725-187">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="b0725-187">TableControlTag</span></span>

<span data-ttu-id="b0725-188">La `<TableControl>` balise contient généralement `<TableHeaders>` des `<TableRowEntries>` balises et qui définissent la mise en forme des têtes et des lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="b0725-188">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="b0725-189">La `<TableHeaders>` balise contient généralement des `<TableColumnHeader>` balises qui contiennent des `<Label>` `<Width>` `<Alignment>` balises, et.</span><span class="sxs-lookup"><span data-stu-id="b0725-189">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="b0725-190">La `<TableRowEntries>` balise contient `<TableRowEntry>` des étiquettes pour chaque ligne de la table.</span><span class="sxs-lookup"><span data-stu-id="b0725-190">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="b0725-191">La `<TableRowEntry>` balise contient une balise `<TableColumnItems>` qui contient une `<TableColumnItem>` balise pour chaque colonne de la ligne.</span><span class="sxs-lookup"><span data-stu-id="b0725-191">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="b0725-192">En règle générale, la `<TableColumnItem>` balise contient une `<PropertyName>` balise qui identifie la propriété de l’objet à afficher dans l’emplacement défini, ou une `<ScriptBlock>` balise qui contient le code de script qui calcule un résultat à afficher à l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="b0725-192">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="b0725-193">Les blocs de script peuvent également être utilisés ailleurs dans des emplacements où les résultats calculés peuvent être utiles.</span><span class="sxs-lookup"><span data-stu-id="b0725-193">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="b0725-194">La `<TableColumnItem>` balise peut également contenir une `<FormatString>` balise qui spécifie la façon dont la propriété ou les résultats calculés sont affichés.</span><span class="sxs-lookup"><span data-stu-id="b0725-194">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="b0725-195">Balise ListControl</span><span class="sxs-lookup"><span data-stu-id="b0725-195">ListControl tag</span></span>

<span data-ttu-id="b0725-196">La `<ListControl>` balise contient généralement une `<ListEntries>` balise.</span><span class="sxs-lookup"><span data-stu-id="b0725-196">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="b0725-197">La `<ListEntries>` balise contient une `<ListEntry>` balise.</span><span class="sxs-lookup"><span data-stu-id="b0725-197">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="b0725-198">La `<ListEntry>` balise contient une `<ListItems>` balise.</span><span class="sxs-lookup"><span data-stu-id="b0725-198">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="b0725-199">La `<ListItems>` balise contient des `<ListItem>` balises qui contiennent des `<PropertyName>` balises.</span><span class="sxs-lookup"><span data-stu-id="b0725-199">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="b0725-200">Les `<PropertyName>` balises spécifient la propriété de l’objet à afficher à l’emplacement spécifié dans la liste.</span><span class="sxs-lookup"><span data-stu-id="b0725-200">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="b0725-201">Si la sélection de la vue est définie à l’aide d’un jeu de sélection, les `<ListControl>` `<ListEntry>` balises et peuvent également contenir une `<EntrySelectedBy>` balise qui contient une ou plusieurs `<TypeName>` balises.</span><span class="sxs-lookup"><span data-stu-id="b0725-201">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="b0725-202">Ces `<TypeName>` balises spécifient le type d’objet que la `<ListControl>` balise doit afficher.</span><span class="sxs-lookup"><span data-stu-id="b0725-202">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="b0725-203">Balise WideControl</span><span class="sxs-lookup"><span data-stu-id="b0725-203">WideControl tag</span></span>

<span data-ttu-id="b0725-204">La `<WideControl>` balise contient généralement une `<WideEntries>` balise.</span><span class="sxs-lookup"><span data-stu-id="b0725-204">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="b0725-205">La `<WideEntries>` balise contient une ou plusieurs `<WideEntry>` balises.</span><span class="sxs-lookup"><span data-stu-id="b0725-205">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="b0725-206">Une `<WideEntry>` balise contient généralement une `<PropertyName>` balise qui spécifie la propriété à afficher à l’emplacement spécifié dans la vue.</span><span class="sxs-lookup"><span data-stu-id="b0725-206">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="b0725-207">La `<PropertyName>` balise peut contenir une `<FormatString>` balise qui spécifie la manière dont la propriété doit être affichée.</span><span class="sxs-lookup"><span data-stu-id="b0725-207">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="b0725-208">CustomControl (balise)</span><span class="sxs-lookup"><span data-stu-id="b0725-208">CustomControl tag</span></span>

<span data-ttu-id="b0725-209">La `<CustomControl>` balise vous permet d’utiliser un bloc de script pour définir un format.</span><span class="sxs-lookup"><span data-stu-id="b0725-209">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="b0725-210">Une `<CustomControl>` balise contient généralement une `<CustomEntries>` balise qui contient plusieurs `<CustomEntry>` balises.</span><span class="sxs-lookup"><span data-stu-id="b0725-210">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="b0725-211">Chaque `<CustomEntry>` balise contient une `<CustomItem>` balise qui peut contenir diverses balises qui spécifient le contenu et la mise en forme de l’emplacement spécifié dans la vue, y compris les `<Text>` `<Indentation>` balises,, `<ExpressionBinding>` et `<NewLine>` .</span><span class="sxs-lookup"><span data-stu-id="b0725-211">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="default-displays-in-typesps1xml"></a><span data-ttu-id="b0725-212">Affichages par défaut dans Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="b0725-212">Default displays in Types.ps1xml</span></span>

<span data-ttu-id="b0725-213">Les affichages par défaut de certains types d’objets de base sont définis dans le `Types.ps1xml` fichier dans le `$PSHOME` répertoire.</span><span class="sxs-lookup"><span data-stu-id="b0725-213">The default displays of some basic object types are defined in the `Types.ps1xml` file in the `$PSHOME` directory.</span></span> <span data-ttu-id="b0725-214">Les nœuds sont nommés **PsStandardMembers** et les sous-nœuds utilisent l’une des balises suivantes :</span><span class="sxs-lookup"><span data-stu-id="b0725-214">The nodes are named **PsStandardMembers** , and the subnodes use one of the following tags:</span></span>

- `<DefaultDisplayProperty>`
- `<DefaultDisplayPropertySet>`
- `<DefaultKeyPropertySet>`

<span data-ttu-id="b0725-215">Pour plus d’informations, consultez [about_Types.ps1XML](about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="b0725-215">For more information, see [about_Types.ps1xml](about_Types.ps1xml.md).</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="b0725-216">Suivi de l’utilisation du fichier XML Format.ps1</span><span class="sxs-lookup"><span data-stu-id="b0725-216">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="b0725-217">Pour détecter les erreurs lors du chargement ou de l’application de `Format.ps1xml` fichiers, utilisez l' `Trace-Command` applet de commande avec l’un des composants de format suivants comme valeur du paramètre **Name** :</span><span class="sxs-lookup"><span data-stu-id="b0725-217">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="b0725-218">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="b0725-218">FormatFileLoading</span></span>
- <span data-ttu-id="b0725-219">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="b0725-219">FormatViewBinding</span></span>

<span data-ttu-id="b0725-220">Pour plus d’informations, consultez [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) et [obten-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span><span class="sxs-lookup"><span data-stu-id="b0725-220">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="b0725-221">Signature d’un fichier XML Format.ps1</span><span class="sxs-lookup"><span data-stu-id="b0725-221">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="b0725-222">Pour protéger les utilisateurs de votre `Format.ps1xml` fichier, signez le fichier à l’aide d’une signature numérique.</span><span class="sxs-lookup"><span data-stu-id="b0725-222">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="b0725-223">Pour plus d’informations, consultez [about_Signing](about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="b0725-223">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="b0725-224">Exemple de code XML pour une vue personnalisée Format-Table</span><span class="sxs-lookup"><span data-stu-id="b0725-224">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="b0725-225">L’exemple suivant crée une `Format-Table` vue personnalisée pour les objets **System. IO. DirectoryInfo** et **System. IO. FileInfo** créés par `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="b0725-225">The following sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="b0725-226">La vue personnalisée est nommée **mygciview** et ajoute la colonne **CreationTime** à la table.</span><span class="sxs-lookup"><span data-stu-id="b0725-226">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="b0725-227">La vue personnalisée est créée à partir d’une version modifiée du `FileSystem.Format.ps1xml` fichier qui est stocké dans `$PSHOME` sur PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="b0725-227">The custom view is created from an edited version of the `FileSystem.Format.ps1xml` file that's stored in `$PSHOME` on PowerShell 5.1.</span></span>

<span data-ttu-id="b0725-228">Une fois votre `.ps1xml` fichier personnalisé enregistré, utilisez `Update-FormatData` pour inclure la vue dans une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0725-228">After your custom `.ps1xml` file is saved, use `Update-FormatData` to include the view in a PowerShell session.</span></span> <span data-ttu-id="b0725-229">Pour cet exemple, la vue personnalisée doit utiliser le format de table ; sinon, `Format-Table` échoue.</span><span class="sxs-lookup"><span data-stu-id="b0725-229">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="b0725-230">Utilisez `Format-Table` avec le paramètre **View** pour spécifier le nom de la vue personnalisée et mettre en forme la sortie de la table.</span><span class="sxs-lookup"><span data-stu-id="b0725-230">Use `Format-Table` with the **View** parameter to specify the custom view's name and format the table's output.</span></span> <span data-ttu-id="b0725-231">Pour obtenir un exemple de la façon dont la commande est exécutée, consultez [format-table](xref:Microsoft.PowerShell.Utility.Format-Table).</span><span class="sxs-lookup"><span data-stu-id="b0725-231">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.IO.DirectoryInfo"
}
Select-String @Parms
Copy-Item $PSHome\FileSystem.format.ps1xml .\MyFileSystem.Format.ps1xml
Update-FormatData -PrependPath $PSHOME\Format\MyFileSystem.Format.ps1xml
```

> [!NOTE]
> <span data-ttu-id="b0725-232">Pour faire tenir l’exemple XML dans les limites de largeur de ligne, il était nécessaire de compresser une mise en retrait et d’utiliser des sauts de ligne dans le code.</span><span class="sxs-lookup"><span data-stu-id="b0725-232">To fit the XML sample within line width limitations, it was necessary to compress some indentation and use line breaks within the code.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
    <SelectionSets>
        <SelectionSet>
            <Name>FileSystemTypes</Name>
            <Types>
                <TypeName>System.IO.DirectoryInfo</TypeName>
                <TypeName>System.IO.FileInfo</TypeName>
            </Types>
        </SelectionSet>
    </SelectionSets>
<Controls>
<Control>
<Name>FileSystemTypes-GroupingFormat</Name>
<CustomControl>
 <CustomEntries>
  <CustomEntry>
    <CustomItem>
    <Frame>
    <LeftIndent>4</LeftIndent>
    <CustomItem>
    <Text AssemblyName="System.Management.Automation"
    BaseName="FileSystemProviderStrings"
    ResourceId="DirectoryDisplayGrouping"/>
    <ExpressionBinding>
     <ScriptBlock>
      $_.PSParentPath.Replace("Microsoft.PowerShell.Core\FileSystem::", "")
     </ScriptBlock>
    </ExpressionBinding>
    <NewLine/>
    </CustomItem>
    </Frame>
    </CustomItem>
    </CustomEntry>
 </CustomEntries>
</CustomControl>
</Control>
</Controls>
<ViewDefinitions>
    <View>
    <Name>mygciview</Name>
    <ViewSelectedBy>
        <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <GroupBy>
      <PropertyName>PSParentPath</PropertyName>
      <CustomControlName>FileSystemTypes-GroupingFormat</CustomControlName>
    </GroupBy>
        <TableControl>
            <TableHeaders>
                <TableColumnHeader>
                    <Label>Mode</Label>
                    <Width>7</Width>
                    <Alignment>left</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>LastWriteTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>CreationTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>Length</Label>
                    <Width>14</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader/>
            </TableHeaders>
            <TableRowEntries>
                <TableRowEntry>
                    <Wrap/>
                    <TableColumnItems>
                        <TableColumnItem>
                            <PropertyName>Mode</PropertyName>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.LastWriteTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.CreationTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
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

## <a name="see-also"></a><span data-ttu-id="b0725-233">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0725-233">See also</span></span>

[<span data-ttu-id="b0725-234">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="b0725-234">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="b0725-235">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="b0725-235">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="b0725-236">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="b0725-236">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="b0725-237">Informations de référence sur le XML des schémas de format</span><span class="sxs-lookup"><span data-stu-id="b0725-237">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="b0725-238">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="b0725-238">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="b0725-239">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="b0725-239">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="b0725-240">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0725-240">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
