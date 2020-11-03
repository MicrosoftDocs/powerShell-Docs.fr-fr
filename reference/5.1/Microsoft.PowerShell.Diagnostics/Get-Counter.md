---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: 7c1ab665fc7ffddc54ec936f80b76b4329291a3b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202629"
---
# Get-Counter

## SYNOPSIS
Obtient les données de compteur de performances provenant des ordinateurs locaux et distants.

## SYNTAX

### GetCounterSet (par défaut)

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### ListSetSet

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## Description

L' `Get-Counter` applet de commande obtient les données du compteur de performance directement à partir de l’instrumentation d’analyse des performances dans la famille de systèmes d’exploitation Windows. `Get-Counter` Obtient les données de performances d’un ordinateur local ou d’ordinateurs distants.

Vous pouvez utiliser les `Get-Counter` paramètres pour spécifier un ou plusieurs ordinateurs, répertorier les ensembles de compteurs de performance et les instances qu’ils contiennent, définir les intervalles d’échantillonnage et spécifier le nombre maximal d’échantillons. Sans paramètres, `Get-Counter` obtient les données des compteurs de performances pour un ensemble de compteurs système.

De nombreux ensembles de compteurs sont protégés par des listes de contrôle d’accès (ACL). Pour afficher tous les ensembles de compteurs, ouvrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

## EXEMPLES

### Exemple 1 : récupération de la liste des ensembles de compteurs

Cet exemple obtient la liste des ensembles de compteurs de l’ordinateur local.

```powershell
Get-Counter -ListSet *
```

```Output
CounterSetName     : Processor
MachineName        : .
CounterSetType     : MultiInstance
Description        : The Processor performance object consists of counters that measure aspects ...
                     computer that performs arithmetic and logical computations, initiates ...
                     computer can have multiple processors.  The processor object represents ...
Paths              : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
PathsWithInstances : {\Processor(0)\% Processor Time, \Processor(1)\% Processor Time, ...
Counter            : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
```

`Get-Counter` utilise le paramètre **ListSet** avec un astérisque ( `*` ) pour récupérer la liste des ensembles de compteurs.
Le point ( `.` ) dans la colonne **MachineName** représente l’ordinateur local.

### Exemple 2 : spécifier SampleInterval et MaxSamples

Cet exemple obtient les données de compteur pour tous les processeurs sur l’ordinateur local. Les données sont collectées à intervalles de deux secondes jusqu’à ce qu’il y ait trois échantillons.

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -SampleInterval 2 -MaxSamples 3
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/18/2019 14:39:56        \\Computer01\processor(_total)\% processor time :
                          20.7144271584086

6/18/2019 14:39:58        \\Computer01\processor(_total)\% processor time :
                          10.4391790575511

6/18/2019 14:40:01        \\Computer01\processor(_total)\% processor time :
                          37.5968799396998
```

`Get-Counter` utilise le paramètre **Counter** pour spécifier le chemin d’accès au compteur `\Processor(_Total)\% Processor Time` . Le paramètre **SampleInterval** définit un intervalle de deux secondes pour vérifier le compteur. **MaxSamples** détermine que trois est le nombre maximal de fois que le compteur est vérifié.

### Exemple 3 : obtenir des échantillons continus d’un compteur

Cet exemple obtient des échantillons continus pour un compteur chaque seconde. Pour arrêter la commande, appuyez sur <kbd>CTRL</kbd> + <kbd>C</kbd>. Pour spécifier un intervalle plus long entre les échantillons, utilisez le paramètre **SampleInterval** .

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -Continuous
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 15:35:03        \\Computer01\processor(_total)\% processor time :
                          43.8522842937022

6/19/2019 15:35:04        \\Computer01\processor(_total)\% processor time :
                          29.7896844697383

6/19/2019 15:35:05        \\Computer01\processor(_total)\% processor time :
                          29.4962645638135

6/19/2019 15:35:06        \\Computer01\processor(_total)\% processor time :
                          25.5901500127408
```

`Get-Counter` utilise le paramètre **Counter** pour spécifier le `\Processor\% Processor Time` compteur.
Le paramètre **Continuous** spécifie d’utiliser des échantillons chaque seconde jusqu’à ce que la commande soit arrêtée avec <kbd>CTRL</kbd> + <kbd>C</kbd>.

### Exemple 4 : liste alphabétique des ensembles de compteurs

Cet exemple utilise le pipeline pour récupérer le jeu de listes de compteurs, puis trier la liste par ordre alphabétique.

```powershell
Get-Counter -ListSet * | Sort-Object -Property CounterSetName | Format-Table -AutoSize
```

```Output
CounterSetName                        MachineName CounterSetType  Description
--------------                        ----------- --------------  -----------
.NET CLR Data                         .           SingleInstance  .Net CLR Data
.NET Data Provider for SqlServer      .           SingleInstance  Counters for System.Data.SqlClient
AppV Client Streamed Data Percentage  .           SingleInstance  Size of data streamed to disk ...
Authorization Manager Applications    .           SingleInstance  The set of Counters for ...
BitLocker                             .           MultiInstance   BitLocker Drive Encryption ...
Bluetooth Device                      .           SingleInstance  Counters related to a remote ...
Cache                                 .           SingleInstance  The Cache performance object ...
Client Side Caching                   .           SingleInstance  Performance counters for SMB ...
```

`Get-Counter` utilise le paramètre **ListSet** avec un astérisque ( `*` ) pour obtenir la liste complète des ensembles de compteurs. Les objets **CounterSet** sont envoyés dans le pipeline. `Sort-Object` utilise le paramètre **Property** pour spécifier que les objets sont triés par **CounterSetName** . Les objets sont envoyés dans le pipeline à `Format-Table` . Le paramètre **AutoSize** ajuste les largeurs de colonne pour réduire la troncation.

Le point ( `.` ) dans la colonne **MachineName** représente l’ordinateur local.

### Exemple 5 : exécuter une tâche en arrière-plan pour obtenir des données de compteur

Dans cet exemple, `Start-Job` exécute une `Get-Counter` commande en tant que tâche en arrière-plan sur l’ordinateur local.
Pour afficher la sortie du compteur de performance à partir du travail, utilisez l’applet de commande `Receive-Job` .

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

`Start-Job` utilise le paramètre **scriptblock** pour exécuter une `Get-Counter` commande. `Get-Counter` utilise le paramètre **Counter** pour spécifier le chemin d’accès au compteur `\LogicalDisk(_Total)\% Free Space` . Le paramètre **MaxSamples** spécifie d’utiliser les exemples 1000 du compteur.

### Exemple 6 : récupérer des données de compteur à partir de plusieurs ordinateurs

Cet exemple utilise une variable pour obtenir les données des compteurs de performances de deux ordinateurs.

```powershell
$DiskReads = "\LogicalDisk(C:)\Disk Reads/sec"
$DiskReads | Get-Counter -ComputerName Server01, Server02 -MaxSamples 10
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/21/2019 10:51:04        \\Server01\logicaldisk(c:)\disk reads/sec :
                          0

                          \\Server02\logicaldisk(c:)\disk reads/sec :
                          0.983050344269146
```

La `$DiskReads` variable stocke le `\LogicalDisk(C:)\Disk Reads/sec` chemin d’accès au compteur. La `$DiskReads` variable est envoyée dans le pipeline à `Get-Counter` . **Counter** est le premier paramètre de position et accepte le chemin d’accès stocké dans `$DiskReads` . **ComputerName** spécifie les deux ordinateurs et **MaxSamples** spécifie d’avoir 10 échantillons sur chaque ordinateur.

### Exemple 7 : obtenir les valeurs d’instance d’un compteur à partir de plusieurs ordinateurs aléatoires

Cet exemple obtient la valeur d’un compteur de performances sur les ordinateurs distants aléatoires 50 de l’entreprise. Le paramètre **ComputerName** utilise des noms d’ordinateur aléatoires stockés dans une variable. Pour mettre à jour les noms d’ordinateur dans la variable, recréez la variable.

Une alternative pour les noms de serveur dans le paramètre **ComputerName** consiste à utiliser un fichier texte. Par exemple :

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

Le chemin d’accès du compteur comprend un astérisque ( `*` ) dans le nom de l’instance pour obtenir les données pour chaque processeur de l’ordinateur distant.

```powershell
$Servers = Get-Random (Get-Content -Path C:\Servers.txt) -Count 50
$Counter = "\Processor(*)\% Processor Time"
Get-Counter -Counter $Counter -ComputerName $Servers
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/20/2019 12:20:35        \\Server01\processor(0)\% processor time :
                          6.52610319637854

                          \\Server01\processor(1)\% processor time :
                          3.41030663625782

                          \\Server01\processor(2)\% processor time :
                          9.64189975649925

                          \\Server01\processor(3)\% processor time :
                          1.85240835619747

                          \\Server01\processor(_total)\% processor time :
                          5.35768447160776
```

L' `Get-Random` applet de commande utilise `Get-Content` pour sélectionner 50 noms d’ordinateur aléatoires dans le `Servers.txt` fichier. Les noms des ordinateurs distants sont stockés dans la `$Servers` variable. Le `\Processor(*)\% Processor Time` chemin d’accès du compteur est stocké dans la `$Counter` variable. `Get-Counter` utilise le paramètre **Counter** pour spécifier les compteurs dans la `$Counter` variable. Le paramètre **ComputerName** spécifie les noms d’ordinateur dans la `$Servers` variable.

### Exemple 8 : utiliser la propriété Path pour récupérer les noms de chemin d’accès mis en forme

Cet exemple utilise la propriété **path** d’un ensemble de compteurs pour rechercher les noms de chemin d’accès mis en forme pour les compteurs de performance.

Le pipeline est utilisé avec l' `Where-Object` applet de commande pour rechercher un sous-ensemble des noms de chemins d’accès. Pour rechercher un ensemble de compteurs liste complète des chemins de compteur, supprimez le pipeline ( `|` ) et la `Where-Object` commande.

`$_`Est une variable automatique pour l’objet actuel dans le pipeline.
Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

```powershell
(Get-Counter -ListSet Memory).Paths | Where-Object { $_ -like "*Cache*" }
```

```Output
\Memory\Cache Faults/sec
\Memory\Cache Bytes
\Memory\Cache Bytes Peak
\Memory\System Cache Resident Bytes
\Memory\Standby Cache Reserve Bytes
\Memory\Standby Cache Normal Priority Bytes
\Memory\Standby Cache Core Bytes
\Memory\Long-Term Average Standby Cache Lifetime (s)
```

`Get-Counter` utilise le paramètre **ListSet** pour spécifier le jeu de compteurs de **mémoire** . La commande est placée entre parenthèses afin que la propriété **paths** retourne chaque chemin d’accès sous forme de chaîne. Les objets sont envoyés dans le pipeline à `Where-Object` . `Where-Object` utilise la variable `$_` pour traiter chaque objet et utilise l' `-like` opérateur pour rechercher les correspondances de la chaîne `*Cache*` . Les astérisques ( `*` ) sont des caractères génériques pour n’importe quel caractère.

### Exemple 9 : utiliser la propriété PathsWithInstances pour récupérer les noms de chemin d’accès mis en forme

Cet exemple obtient les noms de chemin d’accès mis en forme qui incluent les instances des compteurs de performance **PhysicalDisk** .

```powershell
(Get-Counter -ListSet PhysicalDisk).PathsWithInstances
```

```Output
\PhysicalDisk(0 C:)\Current Disk Queue Length
\PhysicalDisk(_Total)\Current Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Time
\PhysicalDisk(_Total)\% Disk Time
\PhysicalDisk(0 C:)\Avg. Disk Queue Length
\PhysicalDisk(_Total)\Avg. Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Read Time
\PhysicalDisk(_Total)\% Disk Read Time
```

`Get-Counter` utilise le paramètre **ListSet** pour spécifier l’ensemble de compteurs de **disque physique** . La commande est placée entre parenthèses afin que la propriété **PathsWithInstances** retourne chaque instance de chemin d’accès en tant que chaîne.

### Exemple 10 : obtenir une valeur unique pour chaque compteur dans un ensemble de compteurs

Dans cet exemple, une valeur unique est retournée pour chaque compteur de performance dans l’ensemble de compteurs de **mémoire** de l’ordinateur local.

```powershell
$MemCounters = (Get-Counter -ListSet Memory).Paths
Get-Counter -Counter $MemCounters
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 12:05:00        \\Computer01\memory\page faults/sec :
                          868.772077545597

                          \\Computer01\memory\available bytes :
                          9031176192

                          \\Computer01\memory\committed bytes :
                          8242982912

                          \\Computer01\memory\commit limit :
                          19603333120
```

`Get-Counter` utilise le paramètre **ListSet** pour spécifier le jeu de compteurs de **mémoire** . La commande est placée entre parenthèses afin que la propriété **paths** retourne chaque chemin d’accès sous forme de chaîne. Les chemins d’accès sont stockés dans la `$MemCounters` variable. `Get-Counter` utilise le paramètre **Counter** pour spécifier les chemins de compteur dans la `$MemCounters` variable.

### Exemple 11 : afficher les valeurs de propriété d’un objet

Les valeurs de propriété de l’objet **PerformanceCounterSample** représentent chaque échantillon de données. Dans cet exemple, nous utilisons les propriétés de l’objet **CounterSamples** pour examiner, sélectionner, trier et regrouper les données.

```powershell
$Counter = "\\Server01\Process(Idle)\% Processor Time"
$Data = Get-Counter $Counter
$Data.CounterSamples | Format-List -Property *
```

```Output
Path             : \\Server01\process(idle)\% processor time
InstanceName     : idle
CookedValue      : 198.467899571389
RawValue         : 14329160321003
SecondValue      : 128606459528326201
MultipleCount    : 1
CounterType      : Timer100Ns
Timestamp        : 6/19/2019 12:20:49
Timestamp100NSec : 128606207528320000
Status           : 0
DefaultScale     : 0
TimeBase         : 10000000
```

Le chemin d’accès au compteur est stocké dans la `$Counter` variable. `Get-Counter` Obtient un échantillon des valeurs de compteur et stocke les résultats dans la `$Data` variable. La `$Data` variable utilise la propriété **CounterSamples** pour récupérer les propriétés de l’objet. L’objet est envoyé dans le pipeline à `Format-List` . Le paramètre **Property** utilise un `*` caractère générique astérisque () pour sélectionner toutes les propriétés.

### Exemple 12 : valeurs du tableau des compteurs de performances

Dans cet exemple, une variable stocke chaque compteur de performance. La propriété **CounterSamples** est un tableau qui peut afficher des valeurs de compteur spécifiques.

Pour afficher chaque échantillon de compteur, utilisez `$Counter.CounterSamples` .

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

`Get-Counter` utilise le paramètre **Counter** pour spécifier le compteur `\Processor(*)\% Processor Time` . Les valeurs sont stockées dans la `$Counter` variable.
`$Counter.CounterSamples[0]` affiche la valeur de tableau pour la première valeur de compteur.

### Exemple 13 : comparer les valeurs des compteurs de performance

Cet exemple recherche la quantité de temps processeur utilisée par chaque processeur sur l’ordinateur local. La propriété **CounterSamples** est utilisée pour comparer les données de compteur par rapport à une valeur spécifiée.

Pour afficher chaque échantillon de compteur, utilisez `$Counter.CounterSamples` .

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples | Where-Object { $_.CookedValue -lt "20" }
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              12.6398025240208
\\Computer01\processor(1)\% processor time   1              15.7598095767344
```

`Get-Counter` utilise le paramètre **Counter** pour spécifier le compteur `\Processor(*)\% Processor Time` . Les valeurs sont stockées dans la `$Counter` variable. Les objets stockés dans `$Counter.CounterSamples` sont envoyés dans le pipeline. `Where-Object` utilise un bloc de script pour comparer chaque valeur d’objet à une valeur spécifiée de 20. `$_.CookedValue`Est une variable pour l’objet actuel dans le pipeline. Les compteurs avec un **CookedValue** inférieur à 20 s’affichent.

### Exemple 14 : trier les données des compteurs de performances

Cet exemple montre comment trier des données de compteur de performance. L’exemple recherche les processus sur l’ordinateur qui utilisent le plus de temps processeur au cours de l’exemple.

```powershell
$Procs = Get-Counter -Counter "\Process(*)\% Processor Time"
$Procs.CounterSamples | Sort-Object -Property CookedValue -Descending |
   Format-Table -Property Path, InstanceName, CookedValue -AutoSize
```

```Output
Path                                                         InstanceName             CookedValue
----                                                         ------------             -----------
\\Computer01\process(_total)\% processor time                _total              395.464129650573
\\Computer01\process(idle)\% processor time                  idle                389.356575524695
\\Computer01\process(mssense)\% processor time               mssense             3.05377706293879
\\Computer01\process(csrss#1)\% processor time               csrss               1.52688853146939
\\Computer01\process(microsoftedgecp#10)\% processor time    microsoftedgecp     1.52688853146939
\\Computer01\process(runtimebroker#5)\% processor time       runtimebroker                      0
\\Computer01\process(settingsynchost)\% processor time       settingsynchost                    0
\\Computer01\process(microsoftedgecp#16)\% processor time    microsoftedgecp                    0
```

`Get-Counter` utilise le paramètre **Counter** pour spécifier le `\Process(*)\% Processor Time` compteur de tous les processus sur l’ordinateur local. Le résultat est stocké dans la `$Procs` variable. La `$Procs` variable avec la propriété **CounterSamples** envoie les objets **PerformanceCounterSample** dans le pipeline. `Sort-Object` utilise le paramètre **Property** pour trier les objets par **CookedValue** dans l’ordre **décroissant** . `Format-Table` utilise le paramètre **Property** pour sélectionner les colonnes de la sortie. Le paramètre **AutoSize** ajuste les largeurs de colonne pour réduire la troncation.

## PARAMETERS

### -ComputerName

Spécifie un nom d’ordinateur ou un tableau de noms d’ordinateurs **distants** séparés par des virgules. Utilisez le nom NetBIOS, une adresse IP ou le nom de domaine complet de l’ordinateur.

Pour récupérer les données du compteur de performance à partir de l’ordinateur **local** , excluez le paramètre **ComputerName** .
Pour une sortie telle qu’un **ListSet** qui contient la colonne **MachineName** , un point ( `.` ) indique l’ordinateur local.

`Get-Counter` ne repose pas sur la communication à distance PowerShell. Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Continuous

Lorsque la **continuation** est spécifiée, `Get-Counter` obtient des exemples jusqu’à ce que vous appuyiez sur <kbd>CTRL</kbd> + <kbd>C</kbd>. Les échantillons sont obtenus chaque seconde pour chaque compteur de performance spécifié. Utilisez le paramètre **SampleInterval** pour augmenter l’intervalle entre les échantillons continus.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Compteur

Spécifie le chemin d’accès à un ou plusieurs chemins de compteur. Les chemins d’accès sont des entrées sous la forme d’un tableau séparé par des virgules, d’une variable ou de valeurs d’un fichier texte. Vous pouvez envoyer des chaînes de chemin d’accès de compteur vers le pipeline `Get-Counter` .

Les chemins de compteur utilisent la syntaxe suivante :

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

Par exemple :

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

`\\ComputerName`Est facultatif dans un chemin d’accès de compteur de performance. Si le chemin d’accès au compteur n’inclut pas le nom de l’ordinateur, `Get-Counter` utilise l’ordinateur local.

Un astérisque ( `*` ) dans l’instance est un caractère générique pour obtenir toutes les instances du compteur.

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -ListSet

Répertorie les ensembles de compteurs de performances sur les ordinateurs. Utilisez un astérisque ( `*` ) pour spécifier tous les ensembles de compteurs. Entrez un nom ou une chaîne séparée par des virgules de noms d’ensembles de compteurs. Vous pouvez envoyer des noms d’ensemble de compteurs vers le pipeline.

Pour obtenir un ensemble de compteurs avec des chemins de compteur mis en forme, utilisez le paramètre **ListSet** . Les propriétés **paths** et **PathsWithInstances** de chaque ensemble de compteurs contiennent les chemins de compteur individuels mis en forme en tant que chaîne.

Vous pouvez enregistrer les chaînes de chemin de compteur dans une variable ou utiliser le pipeline pour envoyer la chaîne à une autre `Get-Counter` commande.

Par exemple, pour envoyer chaque chemin de compteur de **processeur** à `Get-Counter` :

`Get-Counter -ListSet Processor | Get-Counter`

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -MaxSamples

Spécifie le nombre d’échantillons à récupérer à partir de chaque compteur de performance spécifié. Pour obtenir un flux constant d’exemples, utilisez le paramètre **Continuous** .

Si le paramètre **MaxSamples** n’est pas spécifié, `Get-Counter` obtient uniquement un échantillon pour chaque compteur spécifié.

Pour collecter un jeu de données volumineux, exécutez `Get-Counter` en tant que tâche en arrière-plan PowerShell. Pour plus d’informations, consultez [à propos des_tâches](../Microsoft.PowerShell.Core/About/about_Jobs.md).

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SampleInterval

Spécifie le nombre de secondes entre les échantillons pour chaque compteur de performance spécifié. Si le paramètre **SampleInterval** n’est pas spécifié, `Get-Counter` utilise un intervalle d’une seconde.

```yaml
Type: System.Int32
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String[]

`Get-Counter` accepte l’entrée de pipeline pour les chemins de compteurs et les noms des ensembles de compteurs.

## SORTIES

### Microsoft. PowerShell. Commands. GetCounter. CounterSet, Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSampleSet, Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSample

Pour afficher les propriétés d’un objet, envoyez la sortie vers le pipeline dans le pipeline `Get-Member` . Les types d’objets qui sont générés sont les suivants :

Paramètre **ListSet** : **Microsoft. PowerShell. Commands. GetCounter. CounterSet**

Paramètre de **compteur** : **Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSampleSet**

Propriété **CounterSamples** : **Microsoft. PowerShell. Commands. GetCounter. PerformanceCounterSample**

## REMARQUES

Si aucun paramètre n’est spécifié, `Get-Counter` obtient un échantillon pour chaque compteur de performance spécifié. Utilisez les paramètres **MaxSamples** et **Continuous** pour obtenir d’autres exemples.

`Get-Counter` utilise un intervalle d’une seconde entre les échantillons. Utilisez le paramètre **SampleInterval** pour augmenter l’intervalle.

Les valeurs **MaxSamples** et **SampleInterval** s’appliquent à tous les compteurs de chaque ordinateur dans la commande. Pour définir des valeurs différentes pour différents compteurs, entrez des `Get-Counter` commandes distinctes.

## LIENS CONNEXES

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Get-Member](../Microsoft.PowerShell.Utility/Get-Member.md)

[Receive-Job](../Microsoft.PowerShell.Core/Receive-Job.md)

[Start-Job](../Microsoft.PowerShell.Core/Start-Job.md)

[Where-Object](..//Microsoft.PowerShell.Core/Where-Object.md)
