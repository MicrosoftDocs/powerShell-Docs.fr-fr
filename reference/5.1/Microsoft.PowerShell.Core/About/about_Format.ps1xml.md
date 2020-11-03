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
# <a name="about-formatps1xml"></a>À propos de Format.ps1XML

## <a name="short-description"></a>Description courte

Les `Format.ps1xml` fichiers dans PowerShell définissent l’affichage par défaut des objets dans la console PowerShell. Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.

## <a name="long-description"></a>Description longue

`Format.ps1xml`Dans PowerShell, les fichiers définissent l’affichage par défaut des objets dans PowerShell. Vous pouvez créer vos propres `Format.ps1xml` fichiers pour modifier l’affichage des objets ou pour définir des affichages par défaut pour les nouveaux types d’objets que vous créez dans PowerShell.

Quand PowerShell affiche un objet, il utilise les données des fichiers de mise en forme structurés pour déterminer l’affichage par défaut de l’objet. Les données des fichiers de mise en forme déterminent si l’objet est affiché dans une table ou dans une liste, et détermine les propriétés qui sont affichées par défaut.

La mise en forme affecte uniquement l’affichage. Il n’affecte pas les propriétés d’objet qui sont passées dans le pipeline ou la manière dont elles sont passées. `Format.ps1xml` les fichiers ne peuvent pas être utilisés pour personnaliser le format de sortie des tables de hachage.

PowerShell comprend sept fichiers de mise en forme. Ces fichiers se trouvent dans le répertoire d’installation ( `$PSHOME` ). Chaque fichier définit l’affichage d’un groupe d’objets Microsoft .NET Framework :

1. `Certificate.Format.ps1xml`

   Objets dans le magasin de certificats, tels que les certificats X. 509 et les magasins de certificats.

1. `DotNetTypes.Format.ps1xml`

   Autres types de .NET Framework, tels que les objets CultureInfo, FileVersionInfo et EventLogEntry.

1. `FileSystem.Format.ps1xml`

   Objets de système de fichiers, tels que les fichiers et les répertoires.

1. `Help.Format.ps1xml`

   Affichages de l’aide, tels que des affichages détaillés et complets, des paramètres et des exemples.

1. `PowerShellCore.Format.ps1xml`

   Objets générés par les applets de commande PowerShell Core, tels que `Get-Member` et `Get-History` .

1. `PowerShellTrace.Format.ps1xml`

   Les objets de trace, tels que ceux générés par l’applet de commande `Trace-Command` .

1. `Registry.Format.ps1xml`

   Des objets de Registre, tels que des clés et des entrées.

Un fichier de mise en forme peut définir quatre vues différentes de chaque objet :

- Table de charge de travail
- List
- Large
- Custom

Par exemple, quand la sortie d’une `Get-ChildItem` commande est dirigée vers une `Format-List` commande, `Format-List` utilise la vue dans le `FileSystem.Format.ps1xml` fichier pour déterminer comment afficher les objets fichier et dossier sous la forme d’une liste.

Lorsqu’un fichier de mise en forme comprend plusieurs vues d’un objet, PowerShell applique la première vue qu’il trouve.

Dans un `Format.ps1xml` fichier, une vue est définie par un ensemble de balises XML qui décrivent le nom de la vue, le type d’objet auquel elle peut être appliquée, les en-têtes de colonne et les propriétés affichées dans le corps de la vue. Le format dans les `Format.ps1xml` fichiers est appliqué juste avant que les données ne soient présentées à l’utilisateur.

## <a name="creating-new-formatps1xml-files"></a>Création de fichiers XML Format.ps1

Les `.ps1xml` fichiers qui sont installés avec PowerShell sont signés numériquement pour empêcher la falsification, car la mise en forme peut inclure des blocs de script. Pour modifier le format d’affichage d’une vue d’objet existante, ou pour ajouter des vues pour les nouveaux objets, créez vos propres `Format.ps1xml` fichiers, puis ajoutez-les à votre session PowerShell.

Pour créer un fichier, copiez un `Format.ps1xml` fichier existant. Le nouveau fichier peut avoir n’importe quel nom, mais il doit avoir une `.ps1xml` extension de nom de fichier. Vous pouvez placer le nouveau fichier dans n’importe quel répertoire accessible à PowerShell, mais il est utile de placer les fichiers dans le répertoire d’installation de PowerShell ( `$PSHOME` ) ou dans un sous-répertoire du répertoire d’installation.

Pour modifier la mise en forme d’une vue actuelle, localisez la vue dans le fichier de mise en forme, puis utilisez les balises pour modifier la vue. Pour créer un affichage pour un nouveau type d’objet, créez un nouvel affichage ou utilisez une vue existante comme modèle. Les balises sont décrites dans la section suivante. Vous pouvez ensuite supprimer toutes les autres vues du fichier afin que les modifications soient évidentes pour toute personne qui examine le fichier.

Une fois les modifications enregistrées, utilisez l' `Update-FormatData` applet de commande pour ajouter le nouveau fichier à votre session PowerShell. Si vous souhaitez que votre vue soit prioritaire sur une vue définie dans les fichiers intégrés, utilisez le paramètre **prependpath** .
`Update-FormatData` affecte uniquement la session active. Pour apporter la modification à toutes les sessions ultérieures, ajoutez la `Update-FormatData` commande à votre profil PowerShell.

### <a name="example-adding-calendar-data-to-culture-objects"></a>Exemple : ajout de données de calendrier à des objets de culture

Cet exemple montre comment modifier la mise en forme des objets culture **System. Globalization. CultureInfo** générés par l' `Get-Culture` applet de commande dans la session PowerShell active. Les commandes de l’exemple ajoutent la propriété **Calendar** à l’affichage de table par défaut d’objets culture.

La première étape consiste à trouver le `Format.ps1xml` fichier qui contient la vue actuelle des objets culture. La `Select-String` commande suivante recherche le fichier :

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

Cette commande révèle que la définition se trouve dans le `DotNetTypes.Format.ps1xml` fichier.

La commande suivante copie le contenu du fichier dans un nouveau fichier, `MyDotNetTypes.Format.ps1xml` .

```powershell
Copy-Item $PSHome\DotNetTypes.format.ps1xml MyDotNetTypes.Format.ps1xml
```

Ouvrez le `MyDotNetTypes.Format.ps1xml` fichier dans un éditeur XML ou de texte, tel que Visual Studio code. Recherchez la section de l’objet **System. Globalization. CultureInfo** . Le code XML suivant définit les vues de l’objet **CultureInfo** . L’objet n’a qu’une vue **table (** .

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

Supprimez le reste du fichier, à l’exception des balises d’ouverture,, et, ainsi que des balises de `<?xml>` `<Configuration>` `<ViewDefinitions>` fermeture `<ViewDefinitions>` et `<Configuration>` . S’il existe une signature numérique, supprimez-la de votre `Format.ps1xml` fichier personnalisé.

Le `MyDotNetTypes.Format.ps1xml` fichier doit maintenant ressembler à l’exemple suivant :

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
Update-FormatData -PrependPath $PSHOME\MyDotNetTypes.Format.ps1xml
```

Pour tester la modification, tapez `Get-Culture` et passez en revue la sortie qui comprend la propriété **Calendar** .

```powershell
Get-Culture
```

```Output
LCID Name  Calendar                               DisplayName
---- ----  --------                               -----------
1033 en-US System.Globalization.GregorianCalendar English (United States)
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

## <a name="default-displays-in-typesps1xml"></a>Affichages par défaut dans Types.ps1XML

Les affichages par défaut de certains types d’objets de base sont définis dans le `Types.ps1xml` fichier dans le `$PSHOME` répertoire. Les nœuds sont nommés **PsStandardMembers** et les sous-nœuds utilisent l’une des balises suivantes :

- `<DefaultDisplayProperty>`
- `<DefaultDisplayPropertySet>`
- `<DefaultKeyPropertySet>`

Pour plus d’informations, consultez [about_Types.ps1XML](about_Types.ps1xml.md).

## <a name="tracing-formatps1xml-file-use"></a>Suivi de l’utilisation du fichier XML Format.ps1

Pour détecter les erreurs lors du chargement ou de l’application de `Format.ps1xml` fichiers, utilisez l' `Trace-Command` applet de commande avec l’un des composants de format suivants comme valeur du paramètre **Name** :

- FormatFileLoading
- FormatViewBinding

Pour plus d’informations, consultez [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) et [obten-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).

## <a name="signing-a-formatps1xml-file"></a>Signature d’un fichier XML Format.ps1

Pour protéger les utilisateurs de votre `Format.ps1xml` fichier, signez le fichier à l’aide d’une signature numérique. Pour plus d’informations, consultez [about_Signing](about_Signing.md).

## <a name="sample-xml-for-a-format-table-custom-view"></a>Exemple de code XML pour une vue personnalisée Format-Table

L’exemple suivant crée une `Format-Table` vue personnalisée pour les objets **System. IO. DirectoryInfo** et **System. IO. FileInfo** créés par `Get-ChildItem` . La vue personnalisée est nommée **mygciview** et ajoute la colonne **CreationTime** à la table.

La vue personnalisée est créée à partir d’une version modifiée du `FileSystem.Format.ps1xml` fichier qui est stocké dans `$PSHOME` sur PowerShell 5,1.

Une fois votre `.ps1xml` fichier personnalisé enregistré, utilisez `Update-FormatData` pour inclure la vue dans une session PowerShell. Pour cet exemple, la vue personnalisée doit utiliser le format de table ; sinon, `Format-Table` échoue.

Utilisez `Format-Table` avec le paramètre **View** pour spécifier le nom de la vue personnalisée et mettre en forme la sortie de la table. Pour obtenir un exemple de la façon dont la commande est exécutée, consultez [format-table](xref:Microsoft.PowerShell.Utility.Format-Table).

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
> Pour faire tenir l’exemple XML dans les limites de largeur de ligne, il était nécessaire de compresser une mise en retrait et d’utiliser des sauts de ligne dans le code.

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

## <a name="see-also"></a>Voir aussi

[Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[Informations de référence sur le XML des schémas de format](/powershell/scripting/developer/format/format-schema-xml-reference)

[Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command)

[Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[Écriture d’un fichier de mise en forme PowerShell](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
