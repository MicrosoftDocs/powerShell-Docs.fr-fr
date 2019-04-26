---
title: Création d’une vue liste | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066853"
---
# <a name="creating-a-list-view"></a>Création d’une vue de liste

Une vue de liste affiche les données dans une seule colonne (dans un ordre séquentiel). Les données affichées dans la liste peuvent être la valeur d’une propriété .NET ou la valeur d’un script.

## <a name="a-list-view-display"></a>Un affichage de la vue liste

La sortie suivante montre comment Windows PowerShell affiche les propriétés de [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets qui sont retournés par la [Get-Service](/powershell/module/microsoft.powershell.management/get-service) applet de commande. Dans cet exemple, trois objets ont été retournés, où chaque objet séparé à partir de l’objet précédent par une ligne vide.

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

## <a name="defining-the-list-view"></a>Définition de la vue liste

Le code XML suivant montre le schéma de la vue liste permettant d’afficher plusieurs propriétés de la [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objet. Vous devez spécifier chaque propriété que vous souhaitez afficher dans la vue liste.

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

Les éléments XML suivants sont utilisés pour définir une vue de liste :

- Le [vue](./view-element-format.md) élément est l’élément parent de la vue liste. (Ceci est le même élément parent pour la table, les vues de contrôle de large et personnalisées).

- Le [nom](./name-element-for-view-format.md) élément spécifie le nom de la vue. Cet élément est requis pour toutes les vues.

- Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui utilisent la vue. Cet élément est requis.

- Le [GroupBy](./groupby-element-for-view-format.md) élément définit quand un nouveau groupe d’objets s’affiche. Un nouveau groupe est démarré à chaque modification de la valeur d’une propriété spécifique ou d’un script. Cet élément est facultatif.

- Le [contrôles](./controls-element-for-view-format.md) élément définit les contrôles personnalisés qui sont définies par l’affichage de liste. Contrôles vous permettent de préciser la façon dont les données sont affichées. Cet élément est facultatif. Une vue peut définir ses propres contrôles personnalisés, ou il peut utiliser des contrôles communs qui peuvent être utilisées par n’importe quelle vue dans le fichier de mise en forme. Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

- Le [ListControl](./listcontrol-element-format.md) élément définit ce qui est affiché dans la vue et la mise en forme. Comme pour toutes les autres vues, une vue de liste peut afficher les valeurs des propriétés de l’objet ou les valeurs générées par script.

Pour obtenir un exemple d’un fichier de mise en forme complète qui définit une vue de liste simple, consultez [vue liste (Basic)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Fournissant des définitions de votre affichage de liste

Affichages de liste peuvent fournir une ou plusieurs définitions en utilisant les éléments enfants de la [ListControl](./listcontrol-element-format.md) élément. En règle générale, une vue aura qu’une seule définition. Dans l’exemple suivant, la vue fournit une définition unique qui permet d’afficher plusieurs propriétés de la [System.Diagnostics.Process ? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objet. Un affichage de liste permet d’afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple).

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

Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour un affichage de liste :

- Le [ListControl](./listcontrol-element-format.md) élément et ses éléments enfants définissent ce qui est affiché dans la vue.

- Le [situés](./listentries-element-for-listcontrol-format.md) élément fournit les définitions de la vue. Dans la plupart des cas, une vue aura qu’une seule définition. Cet élément est requis.

- Le [ListEntry](./listentry-element-for-listcontrol-format.md) élément fournit une définition de la vue. Au moins un [ListEntry](./listentry-element-for-listcontrol-format.md) est requis ; Toutefois, il n’existe aucune limite maximale pour le nombre d’éléments que vous pouvez ajouter. Dans la plupart des cas, une vue aura qu’une seule définition.

- Le [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) élément spécifie les objets qui sont affichés par une définition spécifique. Cet élément est facultatif et est nécessaire uniquement lorsque vous définissez plusieurs [ListEntry](./listentry-element-for-listcontrol-format.md) éléments qui affichent des objets différents.

- Le [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) élément spécifie les propriétés et les scripts dont les valeurs sont affichées dans les lignes de la vue liste.

- Le [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) élément spécifie une propriété ou un script dont la valeur est affichée dans une ligne de la vue liste. Une vue de liste doit spécifier au moins une propriété ou le script. Il n’existe aucune limite maximale pour le nombre de lignes qui peuvent être spécifiées.

- Le [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) élément spécifie la propriété dont la valeur est affichée dans la ligne. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.

- Le [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) élément spécifie le script dont la valeur est affichée dans la ligne. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.

- Le [étiquette](./label-element-for-listitem-for-listcontrol-format.md) élément spécifie l’étiquette qui s’affiche à gauche de la valeur de propriété ou un script dans la ligne. Cet élément est facultatif. Si une étiquette n’est pas spécifiée, le nom de la propriété ou le script s’affiche. Pour obtenir un exemple complet, consultez [vue liste (étiquettes)](./list-view-labels.md).

- Le [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) élément spécifie une condition qui doit exister pour la ligne à afficher. Pour plus d’informations sur l’ajout de conditions à l’affichage de liste, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md). Cet élément est facultatif.

- Le [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) élément spécifie un modèle qui est utilisé pour afficher la valeur de la propriété ou un script. Cet élément est facultatif.

Pour obtenir un exemple d’un fichier de mise en forme complète qui définit une vue de liste simple, consultez [vue liste (Basic)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Définition des objets qui utilisent la vue liste

Il existe deux façons de définir les objets .NET utilisent l’affichage de liste. Vous pouvez utiliser la [ViewSelectedBy](./viewselectedby-element-format.md) élément pour définir les objets qui peuvent être affichées par toutes les définitions de la vue, ou vous pouvez utiliser la [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) élément pour définir quels objets sont affichés par un définition spécifique de la vue. Dans la plupart des cas, une vue n'a qu’une seule définition, donc les objets sont généralement définies par le [ViewSelectedBy](./viewselectedby-element-format.md) élément.

L’exemple suivant montre comment définir les objets qui sont affichés par la vue de liste en utilisant le [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) éléments. Il n’existe aucune limite au nombre de [TypeName](./typename-element-for-viewselectedby-format.md) éléments que vous pouvez spécifier, et leur ordre n’est pas significatif.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par la vue de liste :

- Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par la vue de liste.

- Le [TypeName](./typename-element-for-viewselectedby-format.md) élément spécifie l’objet .NET qui est affiché par la vue. Le nom de type .NET complet est requis. Vous devez spécifier au moins un type ou la sélection définie pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

Pour obtenir un exemple d’un fichier de mise en forme complète, consultez [vue liste (Basic)](./list-view-basic.md).

L’exemple suivant utilise le [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) éléments. Utiliser des jeux de sélection où vous avez un ensemble d’objets qui sont affichés à l’aide de plusieurs vues, comme lorsque vous définissez un affichage de liste et une vue de table pour les mêmes objets liés. Pour plus d’informations sur la création d’un jeu de sélection, consultez [définissant des ensembles de sélection](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par la vue de liste :

- Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par la vue de liste.

- Le [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) élément spécifie un ensemble d’objets qui peuvent être affichés par la vue. Vous devez spécifier au moins un jeu de sélection ou de type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

L’exemple suivant montre comment définir les objets affichés par une définition spécifique de la vue de liste en utilisant le [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) élément. À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un ensemble de la sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée. Pour plus d’informations sur la façon de créer une sélection des conditions, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par une définition spécifique de la vue de liste :

- Le [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) élément définit les objets qui sont affichés par la définition.

- Le [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) élément spécifie l’objet .NET qui est affiché par la définition. Lorsque vous utilisez cet élément, le nom de type .NET complet est requis. Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

- Le [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) élément (non illustré) spécifie un ensemble d’objets qui peuvent être affichées par cette définition. Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

- Le [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) élément (non illustré) spécifie une condition qui doit exister pour cette définition à utiliser. Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées. Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Affichage des groupes d’objets dans une vue liste

Vous pouvez séparer les objets qui sont affichés par la vue de liste en groupes. Cela ne signifie pas la que vous définissez un groupe, uniquement que PowerShell Windows démarre un nouveau groupe chaque fois que la valeur d’une propriété spécifique ou un script change. Dans l’exemple suivant, un nouveau groupe est démarré chaque fois que la valeur de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) les modifications de propriété.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Les éléments XML suivants sont utilisés pour définir le démarrage d’un groupe :

- Le [GroupBy](./groupby-element-for-view-format.md) élément définit la propriété ou un script qui démarre le nouveau groupe et définit la façon dont le groupe est affiché.

- Le [PropertyName](./propertyname-element-for-groupby-format.md) élément spécifie la propriété qui commence un nouveau groupe chaque fois que sa valeur change. Vous devez spécifier une propriété ou un script pour démarrer le groupe, mais vous ne pouvez pas spécifier à la fois.

- Le [ScriptBlock](./scriptblock-element-for-groupby-format.md) élément spécifie le script qui démarre un nouveau groupe chaque fois que sa valeur change. Vous devez spécifier un script ou une propriété pour démarrer le groupe, mais vous ne pouvez pas spécifier à la fois.

- Le [étiquette](./label-element-for-groupby-format.md) élément définit une étiquette qui s’affiche au début de chaque groupe. En plus du texte spécifié par cet élément, Windows PowerShell affiche la valeur qui a déclenché le nouveau groupe et ajoute une ligne vide avant et après l’étiquette. Cet élément est facultatif.

- Le [CustomControl](./customcontrol-element-for-groupby-format.md) élément définit un contrôle qui est utilisé pour afficher les données. Cet élément est facultatif.

- Le [CustomControlName](./customcontrolname-element-for-groupby-format.md) élément spécifie un commun ou d’afficher le contrôle qui est utilisé pour afficher les données. Cet élément est facultatif.

Pour obtenir un exemple d’un fichier de mise en forme complète qui définit les groupes, consultez [vue liste (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>À l’aide de chaînes de Format

Mise en forme de chaînes peuvent être ajoutés à une vue pour définir plus précisément la façon dont les données sont affichées. L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :

- Le [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) élément spécifie les données qui sont affichées par la vue.

- Le [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) élément spécifie la propriété dont la valeur est affichée par la vue. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.

- Le [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) élément spécifie un modèle de format qui définit comment la valeur de propriété ou un script est affichée dans la vue.

- Le [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) élément (non illustré) spécifie le script dont la valeur est affichée par la vue. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.

Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script. Scripts peuvent appeler n’importe quelle méthode d’un objet. Par conséquent, si un objet possède une méthode, tel que `ToString`, qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

L’élément XML suivant peut être utilisé pour appeler le `ToString` méthode :

- Le [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) élément spécifie les données qui sont affichées par la vue.

- Le [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) élément (non illustré) spécifie le script dont la valeur est affichée par la vue. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
