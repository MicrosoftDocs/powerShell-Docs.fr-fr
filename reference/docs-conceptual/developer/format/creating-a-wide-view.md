---
ms.date: 09/13/2016
ms.topic: reference
title: Création d’une vue large
description: Création d’une vue large
ms.openlocfilehash: 4230ef91a3612e962b2773b12e8016df6f760eae
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655602"
---
# <a name="creating-a-wide-view"></a>Création d’une vue large

Un affichage étendu affiche une seule valeur pour chaque objet affiché. La valeur affichée peut être la valeur d’une propriété d’objet .NET ou la valeur d’un script. Par défaut, il n’y a pas d’étiquette ou d’en-tête pour cette vue.

## <a name="a-wide-view-display"></a>Affichage étendu

L’exemple suivant montre comment Windows PowerShell affiche l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) retourné par l’applet de commande d' [obtention de processus](/powershell/module/Microsoft.PowerShell.Management/Get-Process) quand sa sortie est dirigée vers l’applet de commande [format-global](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) . (Par défaut, l’applet de commande [obtenir-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourne une vue table.) Dans cet exemple, les deux colonnes sont utilisées pour afficher le nom du processus pour chaque objet retourné. Le nom de la propriété de l’objet n’est pas affiché, uniquement la valeur de la propriété.

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>Définition de la vue étendue

Le code XML suivant montre le schéma de vue larges pour l’objet [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

Les éléments XML suivants sont utilisés pour définir une vue étendue :

- L’élément [View](./view-element-format.md) est l’élément parent de la vue larges. (Il s’agit du même élément parent pour les vues de table, de liste et de contrôle personnalisé.)

- L’élément [Name](./name-element-for-view-format.md) spécifie le nom de la vue. Cet élément est requis pour toutes les vues.

- L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui utilisent la vue. Cet élément est obligatoire.

- L’élément [GroupBy](./groupby-element-for-view-format.md) définit le moment où un nouveau groupe d’objets est affiché. Un nouveau groupe est démarré chaque fois que la valeur d’une propriété ou d’un script spécifique change. Cet élément est facultatif.

- Les éléments de [contrôle](./controls-element-for-view-format.md) définissent les contrôles personnalisés qui sont définis par la vue larges. Les contrôles vous permettent de spécifier davantage la façon dont les données sont affichées. Cet élément est facultatif. Une vue peut définir ses propres contrôles personnalisés, ou elle peut utiliser des contrôles communs qui peuvent être utilisés par n’importe quelle vue dans le fichier de mise en forme. Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

- L’élément [WideControl](./widecontrol-element-format.md) et ses éléments enfants définissent ce qui est affiché dans la vue. Dans l’exemple précédent, la vue est conçue pour afficher la propriété [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) .

Pour obtenir un exemple de fichier de mise en forme complet qui définit un affichage plus simple, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Fournir des définitions pour votre vue étendue

Les vues larges peuvent fournir une ou plusieurs définitions à l’aide des éléments enfants de l’élément [WideControl](./widecontrol-element-format.md) . En règle générale, une vue n’a qu’une seule définition. Dans l’exemple suivant, la vue fournit une définition unique qui affiche la valeur de la propriété [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) . Une vue étendue peut afficher la valeur d’une propriété ou la valeur d’un script (non illustrée dans l’exemple).

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour une vue étendue :

- L’élément [WideControl](./widecontrol-element-format.md) et ses éléments enfants définissent ce qui est affiché dans la vue.

- L’élément [AutoSize](./autosize-element-for-widecontrol-format.md) spécifie si la taille de la colonne et le nombre de colonnes sont ajustées en fonction de la taille des données. Cet élément est facultatif.

- L’élément [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) spécifie le nombre de colonnes affichées dans la vue étendue. Cet élément est facultatif.

- L’élément [WideEntries](./wideentries-element-for-widecontrol-format.md) fournit les définitions de la vue. Dans la plupart des cas, une vue n’a qu’une seule définition. Cet élément est obligatoire.

- L’élément [WideEntry](./wideentry-element-for-widecontrol-format.md) fournit une définition de la vue. Au moins un [WideEntry](./wideentry-element-for-widecontrol-format.md) est requis ; Toutefois, il n’existe pas de limite maximale pour le nombre d’éléments que vous pouvez ajouter. Dans la plupart des cas, une vue n’a qu’une seule définition.

- L’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) spécifie les objets qui sont affichés par une définition spécifique. Cet élément est facultatif et n’est nécessaire que lorsque vous définissez plusieurs éléments [WideEntry](./wideentry-element-for-widecontrol-format.md) qui affichent des objets différents.

- L’élément [WideItem](./wideitem-element-for-widecontrol-format.md) spécifie les données affichées par la vue. Contrairement à d’autres types de vues, un contrôle étendu ne peut afficher qu’un seul élément.

- L’élément [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) spécifie la propriété dont la valeur est affichée par la vue. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.

- L’élément [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) spécifie le script dont la valeur est affichée par la vue. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.

- L’élément [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) spécifie un modèle qui est utilisé pour afficher les données. Cet élément est facultatif.

Pour obtenir un exemple de fichier de mise en forme complet qui définit une définition de vue étendue, consultez [vue étendue (de base)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Définition des objets qui utilisent l’affichage étendu

Il existe deux façons de définir les objets .NET qui utilisent la vue étendue. Vous pouvez utiliser l’élément [ViewSelectedBy](./viewselectedby-element-format.md) pour définir les objets qui peuvent être affichés par toutes les définitions de la vue, ou vous pouvez utiliser l’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) pour définir les objets qui sont affichés par une définition spécifique de la vue. Dans la plupart des cas, une vue n’a qu’une seule définition, de sorte que les objets sont généralement définis par l’élément [ViewSelectedBy](./viewselectedby-element-format.md) .

L’exemple suivant montre comment définir les objets affichés par la vue larges à l’aide des éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) . Il n’existe aucune limite quant au nombre d’éléments [TypeName](./typename-element-for-viewselectedby-format.md) que vous pouvez spécifier, et leur ordre n’est pas significatif.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage étendu :

- L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par la vue larges.

- L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie le .net qui est affiché par la vue. Le nom complet du type .NET est obligatoire. Vous devez spécifier au moins un type ou un jeu de sélection pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

Pour obtenir un exemple de fichier de mise en forme complet, consultez [vue étendue (de base)](./wide-view-basic.md).

L’exemple suivant utilise les éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Utilisez des jeux de sélection dans lesquels vous avez un ensemble d’objets associés qui sont affichés à l’aide de plusieurs vues, par exemple lorsque vous définissez une vue étendue et une vue de table pour les mêmes objets. Pour plus d’informations sur la création d’un jeu de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage étendu :

- L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par la vue larges.

- L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) spécifie un ensemble d’objets qui peuvent être affichés par la vue. Vous devez spécifier au moins un jeu de sélection ou un type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue larges à l’aide de l’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) . À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un jeu de sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée. Pour plus d’informations sur la création de conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par une définition spécifique de l’affichage étendu :

- L’élément [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) définit les objets qui sont affichés par la définition.

- L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie le .net qui est affiché par la définition. Lors de l’utilisation de cet élément, le nom complet du type .NET est requis. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

- L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) (non affiché) spécifie un ensemble d’objets qui peuvent être affichés par cette définition. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

- L’élément [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (non affiché) spécifie une condition qui doit exister pour que cette définition soit utilisée. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés. Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Affichage des groupes d’objets dans un affichage étendu

Vous pouvez séparer les objets affichés par la vue larges en groupes. Cela ne signifie pas que vous définissez un groupe, mais uniquement que Windows PowerShell démarre un nouveau groupe chaque fois que la valeur d’une propriété ou d’un script spécifique change. Dans l’exemple suivant, un nouveau groupe est démarré chaque fois que la valeur de la propriété [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) change.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Les éléments XML suivants sont utilisés pour définir le moment où un groupe est démarré :

- L’élément [GroupBy](./groupby-element-for-view-format.md) définit la propriété ou le script qui démarre le nouveau groupe et définit la façon dont le groupe est affiché.

- L’élément [PropertyName](./propertyname-element-for-groupby-format.md) spécifie la propriété qui démarre un nouveau groupe chaque fois que sa valeur change. Vous devez spécifier une propriété ou un script pour démarrer le groupe, mais vous ne pouvez pas spécifier les deux.

- L’élément [scriptblock](./scriptblock-element-for-groupby-format.md) spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change. Vous devez spécifier un script ou une propriété pour démarrer le groupe, mais vous ne pouvez pas spécifier les deux.

- L’élément [label](./label-element-for-groupby-format.md) définit une étiquette qui s’affiche au début de chaque groupe. En plus du texte spécifié par cet élément, Windows PowerShell affiche la valeur qui a déclenché le nouveau groupe et ajoute une ligne vide avant et après l’étiquette. Cet élément est facultatif.

- L’élément [CustomControl](./customcontrol-element-for-groupby-format.md) définit un contrôle qui est utilisé pour afficher les données. Cet élément est facultatif.

- L’élément [CustomControlName](./customcontrolname-element-for-groupby-format.md) spécifie un contrôle d’affichage ou commun qui est utilisé pour afficher les données. Cet élément est facultatif.

Pour obtenir un exemple de fichier de mise en forme complet qui définit des groupes, consultez [vue étendue (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Utilisation de chaînes de format

La mise en forme des chaînes peut être ajoutée à une vue étendue pour définir davantage la façon dont les données sont affichées. L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la `StartTime` propriété.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :

- L’élément [WideItem](./wideitem-element-for-widecontrol-format.md) spécifie les données affichées par la vue.

- L’élément [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) spécifie la propriété dont la valeur est affichée par la vue. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.

- L’élément [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue

- L’élément [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (non affiché) spécifie le script dont la valeur est affichée par la vue. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.

Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script. Les scripts peuvent appeler n’importe quelle méthode d’un objet. Par conséquent, si un objet a une méthode, telle que `ToString` , qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

L’élément XML suivant peut être utilisé pour appeler la `ToString` méthode :

- L’élément [WideItem](./wideitem-element-for-widecontrol-format.md) spécifie les données affichées par la vue.

- L’élément [scriptblock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (non affiché) spécifie le script dont la valeur est affichée par la vue. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.

## <a name="see-also"></a>Voir aussi

[Vue large (De base)](./wide-view-basic.md)

[Vue large (GroupBy)](./wide-view-groupby.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
