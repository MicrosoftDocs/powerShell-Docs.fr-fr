---
title: Création d’un affichage de liste | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368978"
---
# <a name="creating-a-list-view"></a>Création d’une vue de liste

Un affichage de liste affiche des données dans une seule colonne (dans l’ordre séquentiel). Les données affichées dans la liste peuvent être la valeur d’une propriété .NET ou la valeur d’un script.

## <a name="a-list-view-display"></a>Affichage de liste

La sortie suivante montre comment Windows PowerShell affiche les propriétés de [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objets qui sont retournés par l’applet de commande [obtient-service](/powershell/module/microsoft.powershell.management/get-service) . Dans cet exemple, trois objets ont été retournés, chaque objet étant séparé de l’objet précédent par une ligne vide.

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>Définition de la vue Liste

Le code XML suivant montre le schéma de la vue liste pour afficher plusieurs propriétés de [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) , objet. Vous devez spécifier chaque propriété que vous souhaitez afficher en mode liste.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

Les éléments XML suivants sont utilisés pour définir un mode liste :

- L’élément [View](./view-element-format.md) est l’élément parent de la vue liste. (Il s’agit du même élément parent pour les vues de contrôle table, larges et personnalisées.)

- L’élément [Name](./name-element-for-view-format.md) spécifie le nom de la vue. Cet élément est requis pour toutes les vues.

- L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui utilisent la vue. Cet élément est obligatoire.

- L’élément [GroupBy](./groupby-element-for-view-format.md) définit le moment où un nouveau groupe d’objets est affiché. Un nouveau groupe est démarré chaque fois que la valeur d’une propriété ou d’un script spécifique change. Cet élément est facultatif.

- L’élément [Controls](./controls-element-for-view-format.md) définit les contrôles personnalisés qui sont définis par l’affichage de liste. Les contrôles vous permettent de spécifier davantage la façon dont les données sont affichées. Cet élément est facultatif. Une vue peut définir ses propres contrôles personnalisés, ou elle peut utiliser des contrôles communs qui peuvent être utilisés par n’importe quelle vue dans le fichier de mise en forme. Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

- L’élément [ListControl](./listcontrol-element-format.md) définit ce qui est affiché dans la vue et comment il est mis en forme. Comme pour toutes les autres vues, un affichage de liste peut afficher les valeurs des propriétés d’objet ou les valeurs générées par le script.

Pour obtenir un exemple de fichier de mise en forme complet qui définit un affichage de liste simple, consultez [mode liste (de base)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Fournir des définitions pour votre mode liste

Les affichages de liste peuvent fournir une ou plusieurs définitions à l’aide des éléments enfants de l’élément [ListControl](./listcontrol-element-format.md) . En règle générale, une vue n’a qu’une seule définition. Dans l’exemple suivant, la vue fournit une définition unique qui affiche plusieurs propriétés de [System. Diagnostics. Process ? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) , objet. Un affichage de liste peut afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple).

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour une vue Liste :

- L’élément [ListControl](./listcontrol-element-format.md) et ses éléments enfants définissent ce qui est affiché dans la vue.

- L’élément [ListEntries](./listentries-element-for-listcontrol-format.md) fournit les définitions de la vue. Dans la plupart des cas, une vue n’a qu’une seule définition. Cet élément est obligatoire.

- L’élément [ListEntry](./listentry-element-for-listcontrol-format.md) fournit une définition de la vue. Au moins un [ListEntry](./listentry-element-for-listcontrol-format.md) est requis ; Toutefois, il n’existe pas de limite maximale pour le nombre d’éléments que vous pouvez ajouter. Dans la plupart des cas, une vue n’a qu’une seule définition.

- L’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) spécifie les objets qui sont affichés par une définition spécifique. Cet élément est facultatif et n’est nécessaire que lorsque vous définissez plusieurs éléments [ListEntry](./listentry-element-for-listcontrol-format.md) qui affichent des objets différents.

- L’élément [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) spécifie les propriétés et les scripts dont les valeurs sont affichées dans les lignes de la vue liste.

- L’élément [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) spécifie une propriété ou un script dont la valeur est affichée dans une ligne de la vue liste. Un affichage de liste doit spécifier au moins une propriété ou un script. Il n’existe pas de limite maximale pour le nombre de lignes qui peuvent être spécifiées.

- L’élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) spécifie la propriété dont la valeur est affichée dans la ligne. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.

- L’élément [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) spécifie le script dont la valeur est affichée dans la ligne. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.

- L’élément [label](./label-element-for-listitem-for-listcontrol-format.md) spécifie l’étiquette affichée à gauche de la valeur de la propriété ou du script dans la ligne. Cet élément est facultatif. Si aucune étiquette n’est spécifiée, le nom de la propriété ou du script est affiché. Pour obtenir un exemple complet, consultez [affichage de liste (étiquettes)](./list-view-labels.md).

- L’élément [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) spécifie une condition qui doit exister pour que la ligne soit affichée. Pour plus d’informations sur l’ajout de conditions à l’affichage de liste, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md). Cet élément est facultatif.

- L’élément [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) spécifie un modèle qui est utilisé pour afficher la valeur de la propriété ou du script. Cet élément est facultatif.

Pour obtenir un exemple de fichier de mise en forme complet qui définit un affichage de liste simple, consultez [mode liste (de base)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Définition des objets qui utilisent le mode liste

Il existe deux façons de définir les objets .NET qui utilisent le mode liste. Vous pouvez utiliser l’élément [ViewSelectedBy](./viewselectedby-element-format.md) pour définir les objets qui peuvent être affichés par toutes les définitions de la vue, ou vous pouvez utiliser l’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) pour définir les objets qui sont affichés par une définition spécifique de la vue. Dans la plupart des cas, une vue n’a qu’une seule définition, de sorte que les objets sont généralement définis par l’élément [ViewSelectedBy](./viewselectedby-element-format.md) .

L’exemple suivant montre comment définir les objets qui sont affichés par le mode liste à l’aide des éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) . Il n’existe aucune limite quant au nombre d’éléments [TypeName](./typename-element-for-viewselectedby-format.md) que vous pouvez spécifier, et leur ordre n’est pas significatif.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage de liste :

- L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par le mode liste.

- L’élément [TypeName](./typename-element-for-viewselectedby-format.md) spécifie l’objet .net qui est affiché par la vue. Le nom complet du type .NET est obligatoire. Vous devez spécifier au moins un type ou un jeu de sélection pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

Pour obtenir un exemple de fichier de mise en forme complet, consultez [vue liste (de base)](./list-view-basic.md).

L’exemple suivant utilise les éléments [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) . Utilisez des jeux de sélection dans lesquels vous avez un ensemble d’objets associés qui sont affichés à l’aide de plusieurs vues, par exemple lorsque vous définissez un affichage de liste et une vue de table pour les mêmes objets. Pour plus d’informations sur la création d’un jeu de sélection, consultez [définition des jeux de sélection](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par l’affichage de liste :

- L’élément [ViewSelectedBy](./viewselectedby-element-format.md) définit les objets qui sont affichés par le mode liste.

- L’élément [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) spécifie un ensemble d’objets qui peuvent être affichés par la vue. Vous devez spécifier au moins un jeu de sélection ou un type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue liste à l’aide de l’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) . À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un jeu de sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée. Pour plus d’informations sur la création de conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets utilisés par une définition spécifique de la vue Liste :

- L’élément [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) définit les objets qui sont affichés par la définition.

- L’élément [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) spécifie l’objet .net qui est affiché par la définition. Lors de l’utilisation de cet élément, le nom complet du type .NET est requis. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

- L’élément [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) (non affiché) spécifie un ensemble d’objets qui peuvent être affichés par cette définition. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés.

- L’élément [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (non affiché) spécifie une condition qui doit exister pour que cette définition soit utilisée. Vous devez spécifier au moins un type, un jeu de sélection ou une condition de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiés. Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des conditions d’affichage des données](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Affichage des groupes d’objets dans une liste

Vous pouvez séparer les objets qui sont affichés par le mode liste en groupes. Cela ne signifie pas que vous définissez un groupe, mais uniquement que Windows PowerShell démarre un nouveau groupe chaque fois que la valeur d’une propriété ou d’un script spécifique change. Dans l’exemple suivant, un nouveau groupe est démarré chaque fois que la valeur de la propriété [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) change.

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

Pour obtenir un exemple de fichier de mise en forme complet qui définit des groupes, consultez [vue liste (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Utilisation de chaînes de format

La mise en forme des chaînes peut être ajoutée à une vue pour définir davantage la façon dont les données sont affichées. L’exemple suivant montre comment définir une chaîne de mise en forme pour la valeur de la propriété `StartTime`.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :

- L’élément [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) spécifie les données affichées par la vue.

- L’élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) spécifie la propriété dont la valeur est affichée par la vue. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier les deux.

- L’élément [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) spécifie un modèle de format qui définit la façon dont la valeur de la propriété ou du script est affichée dans la vue.

- L’élément [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (non affiché) spécifie le script dont la valeur est affichée par la vue. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.

Dans l’exemple suivant, la méthode `ToString` est appelée pour mettre en forme la valeur du script. Les scripts peuvent appeler n’importe quelle méthode d’un objet. Par conséquent, si un objet a une méthode, telle que `ToString`, qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

L’élément XML suivant peut être utilisé pour appeler la méthode `ToString` :

- L’élément [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) spécifie les données affichées par la vue.

- L’élément [scriptblock](./scriptblock-element-for-listitem-for-listcontrol-format.md) (non affiché) spécifie le script dont la valeur est affichée par la vue. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier les deux.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
