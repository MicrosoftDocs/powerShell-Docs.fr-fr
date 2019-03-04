---
title: Création d’un affichage plus large | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858495"
---
# <a name="creating-a-wide-view"></a>Création d’une vue large

Un affichage plus large affiche une valeur unique pour chaque objet qui s’affiche. La valeur affichée peut être la valeur d’une propriété d’objet .NET ou la valeur d’un script. Par défaut, il n’existe aucune étiquette ou un en-tête pour cette vue.

## <a name="a-wide-view-display"></a>Un écran d’affichage plus large

L’exemple suivant montre comment Windows PowerShell affiche le [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet qui est retourné par la [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande lors de sa sortie est dirigée vers le [ Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) applet de commande. (Par défaut, le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande renvoie une table de vue.) Dans cet exemple, les deux colonnes sont utilisés pour afficher le nom du processus pour chaque objet retourné. Le nom de propriété de l’objet n’est pas affiché, seule la valeur de la propriété.

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

## <a name="defining-the-wide-view"></a>Définition de la vue large

Le code XML suivant montre le schéma de l’affichage plus large pour le [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objet.

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

Les éléments XML suivants sont utilisés pour définir un affichage plus large :

- Le [vue](./view-element-format.md) élément est l’élément parent de l’affichage plus large. (Ceci est le même élément parent pour la table, liste et les vues de contrôle personnalisé.)

- Le [nom](./name-element-for-view-format.md) élément spécifie le nom de la vue. Cet élément est requis pour toutes les vues.

- Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui utilisent la vue. Cet élément est requis.

- Le [GroupBy](./groupby-element-for-view-format.md) élément définit quand un nouveau groupe d’objets s’affiche. Un nouveau groupe est démarré à chaque modification de la valeur d’une propriété spécifique ou d’un script. Cet élément est facultatif.

- Le [contrôles](./controls-element-for-view-format.md) éléments définit les contrôles personnalisés qui sont définies par l’affichage plus large. Contrôles vous permettent de préciser la façon dont les données sont affichées. Cet élément est facultatif. Une vue peut définir ses propres contrôles personnalisés, ou il peut utiliser des contrôles communs qui peuvent être utilisées par n’importe quelle vue dans le fichier de mise en forme. Pour plus d’informations sur les contrôles personnalisés, consultez [création de contrôles personnalisés](./creating-custom-controls.md).

- Le [WideControl](./widecontrol-element-format.md) élément et ses éléments enfants définissent ce qui est affiché dans la vue. Dans l’exemple précédent, la vue est conçue pour afficher le [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propriété.

Pour obtenir un exemple d’un fichier de mise en forme complète qui définit un affichage plus large simple, consultez [affichage plus large (Basic)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Fournissant des définitions de votre affichage large

Affichage large peut fournir une ou plusieurs définitions en utilisant les éléments enfants de la [WideControl](./widecontrol-element-format.md) élément. En règle générale, une vue aura qu’une seule définition. Dans l’exemple suivant, la vue fournit une définition unique qui affiche la valeur de la [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propriété. Un affichage plus large peut afficher la valeur d’une propriété ou la valeur d’un script (non illustré dans l’exemple).

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

Les éléments XML suivants peuvent être utilisés pour fournir des définitions pour un affichage plus large :

- Le [WideControl](./widecontrol-element-format.md) élément et ses éléments enfants définissent ce qui est affiché dans la vue.

- Le [AutoSize](./autosize-element-for-widecontrol-format.md) élément spécifie si la taille de colonne et le nombre de colonnes sont ajustées en fonction de la taille des données. Cet élément est facultatif.

- Le [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) élément spécifie le nombre de colonnes affichées dans l’affichage plus large. Cet élément est facultatif.

- Le [WideEntries](./wideentries-element-for-widecontrol-format.md) élément fournit les définitions de la vue. Dans la plupart des cas, une vue aura qu’une seule définition. Cet élément est requis.

- Le [WideEntry](./wideentry-element-for-widecontrol-format.md) élément fournit une définition de la vue. Au moins un [WideEntry](./wideentry-element-for-widecontrol-format.md) est requis ; Toutefois, il n’existe aucune limite maximale pour le nombre d’éléments que vous pouvez ajouter. Dans la plupart des cas, une vue aura qu’une seule définition.

- Le [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) élément spécifie les objets qui sont affichés par une définition spécifique. Cet élément est facultatif et est nécessaire uniquement lorsque vous définissez plusieurs [WideEntry](./wideentry-element-for-widecontrol-format.md) éléments qui affichent des objets différents.

- Le [WideItem](./wideitem-element-for-widecontrol-format.md) élément spécifie les données qui sont affichées par la vue. Contrairement à d’autres types de vues, un contrôle large peut afficher qu’un seul élément.

- Le [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) élément spécifie la propriété dont la valeur est affichée par la vue. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.

- Le [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) élément spécifie le script dont la valeur est affichée par la vue. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.

- Le [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) élément spécifie un modèle qui est utilisé pour afficher les données. Cet élément est facultatif.

Pour obtenir un exemple d’un fichier de mise en forme complète qui définit une définition d’affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Définition des objets qui utilisent l’affichage plus large

Il existe deux façons de définir les objets .NET utilisent l’affichage plus large. Vous pouvez utiliser la [ViewSelectedBy](./viewselectedby-element-format.md) élément pour définir les objets qui peuvent être affichées par toutes les définitions de la vue, ou vous pouvez utiliser la [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) élément pour définir quels objets sont affichés par un définition spécifique de la vue. Dans la plupart des cas, une vue n'a qu’une seule définition, donc les objets sont généralement définies par le [ViewSelectedBy](./viewselectedby-element-format.md) élément.

L’exemple suivant montre comment définir les objets qui sont affichés par l’affichage plus large à l’aide de la [ViewSelectedBy](./viewselectedby-element-format.md) et [TypeName](./typename-element-for-viewselectedby-format.md) éléments. Il n’existe aucune limite au nombre de [TypeName](./typename-element-for-viewselectedby-format.md) éléments que vous pouvez spécifier, et leur ordre n’est pas significatif.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par l’affichage plus large :

- Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par l’affichage plus large.

- Le [TypeName](./typename-element-for-viewselectedby-format.md) élément spécifie .NET qui est affiché par la vue. Le nom de type .NET complet est requis. Vous devez spécifier au moins un type ou la sélection définie pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

Pour obtenir un exemple d’un fichier de mise en forme complète, consultez [affichage plus large (Basic)](./wide-view-basic.md).

L’exemple suivant utilise le [ViewSelectedBy](./viewselectedby-element-format.md) et [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) éléments. Utiliser des jeux de sélection où vous avez un ensemble d’objets qui sont affichés à l’aide de plusieurs vues, comme lorsque vous définissez un affichage plus large et un affichage de tableau pour les mêmes objets liés. Pour plus d’informations sur la création d’un jeu de sélection, consultez [définissant des ensembles de sélection](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par l’affichage plus large :

- Le [ViewSelectedBy](./viewselectedby-element-format.md) élément définit les objets qui sont affichés par l’affichage plus large.

- Le [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) élément spécifie un ensemble d’objets qui peuvent être affichés par la vue. Vous devez spécifier au moins un jeu de sélection ou de type pour la vue, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

L’exemple suivant montre comment définir les objets affichés par une définition spécifique de l’affichage plus large en utilisant le [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) élément. À l’aide de cet élément, vous pouvez spécifier le nom de type .NET de l’objet, un ensemble de la sélection d’objets ou une condition de sélection qui spécifie quand la définition est utilisée. Pour plus d’informations sur la façon de créer une sélection des conditions, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Les éléments XML suivants peuvent être utilisés pour spécifier les objets qui sont utilisés par une définition spécifique de l’affichage plus large :

- Le [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) élément définit les objets qui sont affichés par la définition.

- Le [TypeName](./typename-element-for-viewselectedby-format.md) élément spécifie .NET qui est affiché par la définition. Lors de l’utilisation de cet élément, le nom de type .NET complet est requis. Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

- Le [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) élément (non illustré) spécifie un ensemble d’objets qui peuvent être affichées par cette définition. Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées.

- Le [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) élément (non illustré) spécifie une condition qui doit exister pour cette définition à utiliser. Vous devez spécifier au moins un type, jeu de sélection ou le critère de sélection pour la définition, mais il n’existe aucun nombre maximal d’éléments qui peuvent être spécifiées. Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Affichage des groupes d’objets dans un affichage plus large

Vous pouvez séparer les objets qui sont affichés par l’affichage plus large en groupes. Cela ne signifie pas la que vous définissez un groupe, uniquement que PowerShell Windows démarre un nouveau groupe chaque fois que la valeur d’une propriété spécifique ou un script change. Dans l’exemple suivant, un nouveau groupe est démarré chaque fois que la valeur de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) les modifications de propriété.

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

Pour obtenir un exemple d’un fichier de mise en forme complète qui définit les groupes, consultez [affichage plus large (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>À l’aide de chaînes de Format

Mise en forme de chaînes peuvent être ajoutés à un affichage plus large d’affiner la façon dont les données sont affichées. L’exemple suivant montre comment définir une chaîne mise en forme pour la valeur de la `StartTime` propriété.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Les éléments XML suivants peuvent être utilisés pour spécifier un modèle de format :

- Le [WideItem](./wideitem-element-for-widecontrol-format.md) élément spécifie les données qui sont affichées par la vue.

- Le [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) élément spécifie la propriété dont la valeur est affichée par la vue. Vous devez spécifier une propriété ou un script, mais vous ne pouvez pas spécifier à la fois.

- Le [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) élément spécifie un modèle de format qui définit comment la valeur de propriété ou un script est affichée dans la vue

- Le [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) élément (non illustré) spécifie le script dont la valeur est affichée par la vue. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.

Dans l’exemple suivant, la `ToString` méthode est appelée pour mettre en forme la valeur du script. Scripts peuvent appeler n’importe quelle méthode d’un objet. Par conséquent, si un objet possède une méthode, tel que `ToString`, qui a des paramètres de mise en forme, le script peut appeler cette méthode pour mettre en forme la valeur de sortie du script.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

L’élément XML suivant peut être utilisé pour appeler le `ToString` méthode :

- Le [WideItem](./wideitem-element-for-widecontrol-format.md) élément spécifie les données qui sont affichées par la vue.

- Le [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) élément (non illustré) spécifie le script dont la valeur est affichée par la vue. Vous devez spécifier un script ou une propriété, mais vous ne pouvez pas spécifier à la fois.

## <a name="see-also"></a>Voir aussi

[Affichage plus large (Basic)](./wide-view-basic.md)

[Affichage plus large (GroupBy)](./wide-view-groupby.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
