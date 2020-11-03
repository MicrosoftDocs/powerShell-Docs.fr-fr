---
description: À compter de PowerShell 6, les vues par défaut des objets sont définies dans le code source PowerShell.  Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: c638001c8442284224c0cb554513ef988ba59f3d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208089"
---
# <a name="about-formatps1xml"></a>À propos de Format.ps1XML

## <a name="short-description"></a>Description courte

À compter de PowerShell 6, les vues par défaut des objets sont définies dans le code source PowerShell.

Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.

## <a name="long-description"></a>Description longue

À compter de PowerShell 6, les vues par défaut sont définies dans le code source PowerShell. Les `Format.ps1xml` fichiers de powershell 5,1 et versions antérieures n’existent pas dans PowerShell 6 et versions ultérieures.

Le code source PowerShell définit l’affichage par défaut des objets dans la console PowerShell. Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.

Quand PowerShell affiche un objet, il utilise les données des fichiers de mise en forme structurés pour déterminer l’affichage par défaut de l’objet. Les données des fichiers de mise en forme déterminent si l’objet est affiché dans une table ou dans une liste, et détermine les propriétés qui sont affichées par défaut.

La mise en forme affecte uniquement l’affichage. Il n’affecte pas les propriétés d’objet qui sont passées dans le pipeline ou la manière dont elles sont passées. `Format.ps1xml` les fichiers ne peuvent pas être utilisés pour personnaliser le format de sortie des tables de hachage.

Un `.ps1xml` fichier de mise en forme peut définir quatre vues différentes de chaque objet :

- Table de charge de travail
- List
- Large
- Custom

Par exemple, quand la sortie d’une `Get-ChildItem` commande est dirigée vers une `Format-List` commande, `Format-List` utilise la vue liste définie dans le code source pour déterminer comment afficher les objets fichier et dossier sous la forme d’une liste.

Lorsqu’un fichier de mise en forme comprend plusieurs vues d’un objet, PowerShell applique la première vue qu’il trouve.

Dans un `Format.ps1xml` fichier personnalisé, une vue est définie par un ensemble de balises XML qui décrivent le nom de la vue, le type d’objet auquel elle peut être appliquée, les en-têtes de colonne et les propriétés affichées dans le corps de la vue. Le format dans les `Format.ps1xml` fichiers est appliqué juste avant que les données ne soient présentées à l’utilisateur.

## <a name="creating-new-formatps1xml-files"></a>Création de fichiers XML Format.ps1

Pour modifier le format d’affichage d’une vue d’objet existante, ou pour ajouter des vues pour les nouveaux objets, créez vos propres `Format.ps1xml` fichiers, puis ajoutez-les à votre session PowerShell.

Pour créer un `Format.ps1xml` fichier afin de définir une vue personnalisée, utilisez les applets de commande [FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) et [Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) . Utilisez un éditeur de texte pour modifier le fichier. Le fichier peut être enregistré dans n’importe quel répertoire auquel PowerShell peut accéder, tel qu’un sous-répertoire de `$HOME` .

Pour modifier la mise en forme d’une vue actuelle, localisez la vue dans le fichier de mise en forme, puis utilisez les balises pour modifier la vue. Pour créer un affichage pour un nouveau type d’objet, créez un nouvel affichage ou utilisez une vue existante comme modèle. Les balises sont décrites dans la section suivante. Vous pouvez ensuite supprimer toutes les autres vues du fichier afin que les modifications soient évidentes pour toute personne qui examine le fichier.

Une fois les modifications enregistrées, utilisez [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) pour ajouter le nouveau fichier à votre session PowerShell. Si vous souhaitez que votre vue soit prioritaire sur une vue définie dans les fichiers intégrés, utilisez le paramètre **prependpath** . `Update-FormatData` affecte uniquement la session active. Pour apporter la modification à toutes les sessions ultérieures, ajoutez la `Update-FormatData` commande à votre profil PowerShell.

### <a name="example-add-calendar-data-to-culture-objects"></a>Exemple : ajouter des données de calendrier à des objets de culture

Cet exemple montre comment modifier la mise en forme des objets culture **System. Globalization. CultureInfo** générés par l' `Get-Culture` applet de commande dans la session PowerShell active. Les commandes de l’exemple ajoutent la propriété **Calendar** à l’affichage de table par défaut d’objets culture.

Pour commencer, récupérez les données de format à partir du fichier de code source et créez un `Format.ps1xml` fichier qui contient la vue actuelle des objets de culture.

```powershell
Get-FormatData -TypeName System.Globalization.CultureInfo |
  Export-FormatData -Path $HOME\Format\CultureInfo.Format.ps1xml
```

Ouvrez le `CultureInfo.Format.ps1xml` fichier dans un éditeur XML ou de texte, tel que Visual Studio code. Le code XML suivant définit les vues de l’objet **CultureInfo** .

Le `CultureInfo.Format.ps1xml` fichier doit ressembler à l’exemple suivant :

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

Créez une nouvelle colonne pour la propriété **Calendar** en ajoutant un nouvel ensemble de `<TableColumnHeader>` balises. La valeur de la propriété **Calendar** peut être longue. vous devez donc spécifier une valeur de 45 caractères comme `<Width>` .

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

Ajoutez un nouvel élément de colonne pour **Calendar** dans les lignes de table à l’aide des `<TableColumnItem>` `<PropertyName` balises et :

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

Enregistrez et fermez le fichier. Utilisez `Update-FormatData` pour ajouter le nouveau fichier de format à la session PowerShell active.

Cet exemple utilise le paramètre **prependpath** pour placer le nouveau fichier dans un ordre de priorité plus élevé que celui du fichier d’origine. Pour plus d’informations, voir [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).

```powershell
Update-FormatData -PrependPath $HOME\Format\CultureInfo.Format.ps1xml
```

Pour tester la modification, tapez `Get-Culture` et passez en revue la sortie qui comprend la propriété **Calendar** .

```powershell
Get-Culture
```

```Output
LCID  Name   Calendar                                DisplayName
----  ----   --------                                -----------
1033  en-US  System.Globalization.GregorianCalendar  English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a>XML dans Format.ps1fichiers XML

La définition de schéma complète se trouve dans [format. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) dans le référentiel de code source PowerShell sur GitHub.

La section **ViewDefinitions** de chaque `Format.ps1xml` fichier contient les `<View>` balises qui définissent chaque vue. Une `<View>` balise typique comprend les balises suivantes :

- `<Name>` identifie le nom de la vue.
- `<ViewSelectedBy>` Spécifie le ou les types d’objets auxquels la vue s’applique.
- `<GroupBy>` spécifie la manière dont les éléments de la vue sont combinés dans des groupes.
- `<TableControl>`, `<ListControl>` , `<WideControl>` et `<CustomControl>` contiennent les balises qui spécifient la façon dont chaque élément est affiché.

### <a name="viewselectedby-tag"></a>Balise ViewSelectedBy

La `<ViewSelectedBy>` balise peut contenir une `<TypeName>` balise pour chaque type d’objet auquel s’applique la vue. Ou peut contenir une `<SelectionSetName>` balise qui fait référence à un jeu de sélection défini ailleurs à l’aide d’une `<SelectionSet>` balise.

### <a name="groupby-tag"></a>GroupBy (étiquette)

La `<GroupBy>` balise contient une `<PropertyName>` balise qui spécifie la propriété d’objet par laquelle les éléments doivent être regroupés. Elle contient également une `<Label>` balise qui spécifie une chaîne à utiliser comme étiquette pour chaque groupe ou une `<CustomControlName>` balise qui fait référence à un contrôle personnalisé défini ailleurs à l’aide d’une `<Control>` balise. La `<Control>` balise contient une balise `<Name>` et une `<CustomControl>` balise.

### <a name="tablecontroltag"></a>TableControlTag

La `<TableControl>` balise contient généralement `<TableHeaders>` des `<TableRowEntries>` balises et qui définissent la mise en forme des têtes et des lignes de la table. La `<TableHeaders>` balise contient généralement des `<TableColumnHeader>` balises qui contiennent des `<Label>` `<Width>` `<Alignment>` balises, et. La `<TableRowEntries>` balise contient `<TableRowEntry>` des étiquettes pour chaque ligne de la table. La `<TableRowEntry>` balise contient une balise `<TableColumnItems>` qui contient une `<TableColumnItem>` balise pour chaque colonne de la ligne. En règle générale, la `<TableColumnItem>` balise contient une `<PropertyName>` balise qui identifie la propriété de l’objet à afficher dans l’emplacement défini, ou une `<ScriptBlock>` balise qui contient le code de script qui calcule un résultat à afficher à l’emplacement.

> [!NOTE]
> Les blocs de script peuvent également être utilisés ailleurs dans des emplacements où les résultats calculés peuvent être utiles.

La `<TableColumnItem>` balise peut également contenir une `<FormatString>` balise qui spécifie la façon dont la propriété ou les résultats calculés sont affichés.

### <a name="listcontrol-tag"></a>Balise ListControl

La `<ListControl>` balise contient généralement une `<ListEntries>` balise. La `<ListEntries>` balise contient une `<ListEntry>` balise. La `<ListEntry>` balise contient une `<ListItems>` balise. La `<ListItems>` balise contient des `<ListItem>` balises qui contiennent des `<PropertyName>` balises. Les `<PropertyName>` balises spécifient la propriété de l’objet à afficher à l’emplacement spécifié dans la liste. Si la sélection de la vue est définie à l’aide d’un jeu de sélection, les `<ListControl>` `<ListEntry>` balises et peuvent également contenir une `<EntrySelectedBy>` balise qui contient une ou plusieurs `<TypeName>` balises. Ces `<TypeName>` balises spécifient le type d’objet que la `<ListControl>` balise doit afficher.

### <a name="widecontrol-tag"></a>Balise WideControl

La `<WideControl>` balise contient généralement une `<WideEntries>` balise. La `<WideEntries>` balise contient une ou plusieurs `<WideEntry>` balises. Une `<WideEntry>` balise contient généralement une `<PropertyName>` balise qui spécifie la propriété à afficher à l’emplacement spécifié dans la vue. La `<PropertyName>` balise peut contenir une `<FormatString>` balise qui spécifie la manière dont la propriété doit être affichée.

### <a name="customcontrol-tag"></a>CustomControl (balise)

La `<CustomControl>` balise vous permet d’utiliser un bloc de script pour définir un format. Une `<CustomControl>` balise contient généralement une `<CustomEntries>` balise qui contient plusieurs `<CustomEntry>` balises. Chaque `<CustomEntry>` balise contient une `<CustomItem>` balise qui peut contenir diverses balises qui spécifient le contenu et la mise en forme de l’emplacement spécifié dans la vue, y compris les `<Text>` `<Indentation>` balises,, `<ExpressionBinding>` et `<NewLine>` .

## <a name="tracing-formatps1xml-file-use"></a>Suivi de l’utilisation du fichier XML Format.ps1

Pour détecter les erreurs lors du chargement ou de l’application de `Format.ps1xml` fichiers, utilisez l' `Trace-Command` applet de commande avec l’un des composants de format suivants comme valeur du paramètre **Name** :

- FormatFileLoading
- FormatViewBinding

Pour plus d’informations, consultez [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) et [obten-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).

## <a name="signing-a-formatps1xml-file"></a>Signature d’un fichier XML Format.ps1

Pour protéger les utilisateurs de votre `Format.ps1xml` fichier, signez le fichier à l’aide d’une signature numérique. Pour plus d’informations, consultez [about_Signing](about_Signing.md).

## <a name="sample-xml-for-a-format-table-custom-view"></a>Exemple de code XML pour une vue personnalisée Format-Table

L’exemple de code XML suivant crée une `Format-Table` vue personnalisée pour les objets **System. IO. DirectoryInfo** et **System. IO. FileInfo** créés par `Get-ChildItem` . La vue personnalisée est nommée **mygciview** et ajoute la colonne **CreationTime** à la table.

Pour créer la vue personnalisée, utilisez les `Get-FormatData` applets de commande et `Export-FormatData` pour générer un `.ps1xml` fichier. Modifiez ensuite votre `.ps1xml` fichier pour créer le code de votre vue personnalisée. Le `.ps1xml` fichier peut être stocké dans n’importe quel répertoire auquel PowerShell peut accéder. Par exemple, un sous-répertoire de `$HOME` .

Une fois le `.ps1xml` fichier créé, utilisez l' `Update-FormatData` applet de commande pour inclure la vue dans la session PowerShell active. Vous pouvez aussi ajouter la commande de mise à jour à votre profil PowerShell Si vous avez besoin de la vue disponible dans toutes les sessions PowerShell.

Pour cet exemple, la vue personnalisée doit utiliser le format de table ; sinon, `Format-Table` échoue.

Utilisez `Format-Table` avec le paramètre **View** pour spécifier le nom de la vue personnalisée, **mygciview** , et mettez en forme la sortie de la table avec la colonne **CreationTime** . Pour obtenir un exemple de la façon dont la commande est exécutée, consultez [format-table](xref:Microsoft.PowerShell.Utility.Format-Table).

> [!NOTE]
> Bien que vous puissiez obtenir le code XML de mise en forme du code source pour créer une vue personnalisée, un développement plus grand peut être nécessaire pour obtenir le résultat souhaité.

Dans la `Get-FormatData` commande suivante, vous pouvez utiliser le paramètre **PowerShellVersion** pour vous assurer que toutes les informations de mise en forme locale sont retournées. Utilisez `-PowerShellVersion $PSVersionTable.PSVersion` plutôt qu’une version spécifique de PowerShell.

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

## <a name="see-also"></a>Voir aussi

[Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[Informations de référence sur le XML des schémas de format](/powershell/scripting/developer/format/format-schema-xml-reference)

[Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command)

[Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[Écriture d’un fichier de mise en forme PowerShell](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
