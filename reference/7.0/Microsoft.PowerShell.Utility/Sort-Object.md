---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: ad546ee4dddac112e76903c28687f2ee974f06a7
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205926"
---
# Sort-Object

## SYNOPSIS
Trie les objets selon les valeurs de propriété.

## SYNTAX

### Valeur par défaut (par défaut)

```
Sort-Object [-Stable] [-Descending] [-Unique] [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### Haut

```
Sort-Object [-Descending] [-Unique] -Top <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### Bas

```
Sort-Object [-Descending] [-Unique] -Bottom <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## Description

L' `Sort-Object` applet de commande trie les objets dans l’ordre croissant ou décroissant en fonction des valeurs de propriété de l’objet. Si les propriétés de tri ne sont pas incluses dans une commande, PowerShell utilise les propriétés de tri par défaut du premier objet d’entrée. Si le type de l’objet d’entrée n’a pas de propriétés de tri par défaut, PowerShell tente de comparer les objets eux-mêmes. Pour plus d’informations, consultez la section [Remarques](#notes) .

Vous pouvez trier les objets par une ou plusieurs propriétés. Plusieurs propriétés utilisent des tables de hachage pour trier par ordre croissant, ordre décroissant ou combinaison d’ordres de tri. Les propriétés sont triées en respectant la casse ou ne respectent pas la casse. Utilisez le paramètre **unique** pour éliminer les doublons de la sortie.

## EXEMPLES

### Exemple 1 : trier le répertoire actif par nom

Cet exemple trie les fichiers et les sous-répertoires d’un répertoire.

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

L' `Get-ChildItem` applet de commande obtient les fichiers et les sous-répertoires du répertoire spécifié par le paramètre de **chemin d’accès** , **C:\test** . Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .
`Sort-Object` ne spécifie pas de propriété, de sorte que la sortie est triée par la propriété de tri par défaut, **Name** .

### Exemple 2 : trier le répertoire actif par longueur de fichier

Cette commande affiche les fichiers dans le répertoire actif par longueur dans l’ordre croissant.

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

L' `Get-ChildItem` applet de commande obtient les fichiers du répertoire spécifié par le paramètre **path** .
Le paramètre **file** spécifie que `Get-ChildItem` obtient uniquement les objets de fichier. Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` . `Sort-Object` utilise le paramètre **Length** pour trier les fichiers par longueur dans l’ordre croissant.

### Exemple 3 : trier les processus par utilisation de la mémoire

Cet exemple affiche les processus avec l’utilisation de mémoire la plus élevée en fonction de leur taille de jeu de travail (WS).

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

L' `Get-Process` applet de commande obtient la liste des processus en cours d’exécution sur l’ordinateur. Les objets processus sont envoyés dans le pipeline à l’applet de commande `Sort-Object` . `Sort-Object` utilise le paramètre **Property** pour trier les objets par **WS** . Les objets sont envoyés dans le pipeline à l’applet de commande `Select-Object` .
`Select-Object` utilise le **dernier** paramètre pour spécifier les cinq derniers objets, qui sont les objets avec l’utilisation de **WS** la plus élevée.

Dans PowerShell 6, le `Sort-Object` paramètre en **bas** est une alternative à `Select-Object` . Par exemple : `Get-Process | Sort-Object -Property WS -Bottom 5`.

### Exemple 4 : trier les objets HistoryInfo par ID

Cette commande trie les objets **HistoryInfo** de la session PowerShell à l’aide de la propriété **ID** . Chaque session PowerShell a son propre historique de commande.

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

L' `Get-History` applet de commande obtient les objets d’historique de la session PowerShell active. Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` . `Sort-Object` utilise le paramètre **Property** pour trier les objets par **ID** . Le paramètre **décroissant** trie l’historique des commandes du plus récent au plus ancien.

### Exemple 5 : utiliser une table de hachage pour trier les propriétés dans l’ordre croissant et décroissant

Cet exemple utilise deux propriétés pour trier les objets, **Status** et **DisplayName** . L' **État** est trié par ordre décroissant et **DisplayName** est trié dans l’ordre croissant.

Une table de hachage est utilisée pour spécifier la valeur du paramètre de **propriété** . La table de hachage utilise une expression pour spécifier les noms de propriétés et les ordres de tri. Pour plus d’informations sur les tables de hachage, voir [À propos des tables de hachage](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).

La propriété **Status** utilisée dans la table de hachage est une propriété énumérée.
Pour plus d’informations, consultez [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

L' `Get-Service` applet de commande obtient la liste des services sur l’ordinateur. Les objets de service sont envoyés dans le pipeline à l’applet de commande `Sort-Object` . `Sort-Object` utilise le paramètre **Property** avec une table de hachage pour spécifier les noms de propriétés et les ordres de tri. Le paramètre **Property** est trié par deux propriétés, **Status** dans l’ordre décroissant et **DisplayName** dans l’ordre croissant.

**Status** est une propriété énumérée. **Stopped** a la valeur **1** et **Running** a la valeur **4** . Le paramètre **décroissant** est défini sur `$True` afin que les processus **en cours d’exécution** soient affichés avant les processus **arrêtés** . **DisplayName** définit le paramètre **décroissant** sur `$False` pour trier les noms d’affichage par ordre alphabétique.

### Exemple 6 : trier des fichiers texte par intervalle de temps

Cette commande trie les fichiers texte par ordre décroissant selon l’intervalle de temps entre **CreationTime** et **LastWriteTime** .

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt
```

L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le répertoire **C:\test** et tous les `*.txt` fichiers. Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .
`Sort-Object` utilise le paramètre **Property** avec une table de hachage pour déterminer l’intervalle de temps entre les fichiers **CreationTime** et **LastWriteTime** . Le paramètre **décroissant** est défini sur `$False` pour trier dans l’ordre de l’intervalle de temps le plus long au plus bref.

### Exemple 7 : trier les noms dans un fichier texte

Cet exemple montre comment trier une liste à partir d’un fichier texte. Le fichier d’origine s’affiche sous la forme d’une liste non triée. `Sort-Object` trie le contenu, puis trie le contenu avec le paramètre **unique** qui supprime les doublons.

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier le répertoire et le nom de fichier. Le **ServerNames.txt** de fichier contient une liste non triée de noms d’ordinateurs.

L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier le répertoire et le nom de fichier. Le **ServerNames.txt** de fichier contient une liste non triée de noms d’ordinateurs. Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` . `Sort-Object` trie la liste dans l’ordre par défaut, en ordre croissant.

L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier le répertoire et le nom de fichier. Le **ServerNames.txt** de fichier contient une liste non triée de noms d’ordinateurs. Les objets sont envoyés dans le pipeline à l’applet de commande `Sort-Object` . `Sort-Object` utilise le paramètre **unique** pour supprimer les noms d’ordinateur en double. La liste est triée dans l’ordre par défaut, en ordre croissant.

### Exemple 8 : trier une chaîne comme un entier

Cet exemple montre comment trier un fichier texte qui contient des objets String en tant qu’entiers. Vous pouvez envoyer chaque commande dans le pipeline à `Get-Member` et vérifier que les objets sont des chaînes et non des entiers. Pour ces exemples, le `ProductId.txt` fichier contient une liste non triée de numéros de produits.

Dans le premier exemple, `Get-Content` obtient le contenu du fichier et canalise les lignes vers l’applet de commande `Sort-Object` . `Sort-Object` trie les objets String dans l’ordre croissant.

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

Dans le deuxième exemple, `Get-Content` obtient le contenu du fichier et canalise les lignes vers l’applet de commande `Sort-Object` . `Sort-Object` utilise un bloc de script pour convertir les chaînes en entiers. Dans l’exemple de code, `[int]` convertit la chaîne en un entier et `$_` représente chaque chaîne au fur et à mesure qu’elle apparaît dans le pipeline. Les objets entiers sont envoyés dans le pipeline à l’applet de commande `Sort-Object` .
`Sort-Object` trie les objets entiers dans l’ordre numérique.

### Exemple 9 : utilisation de tris stables

Lorsque vous utilisez les paramètres **supérieur** , **inférieur** ou **stable** , les objets triés sont remis dans l’ordre dans lequel ils ont été reçus `Sort-Object` lorsque les critères de tri sont égaux. Dans cet exemple, nous triant les nombres 1 à 20 par leur valeur « modulo 3 ». La valeur modulo est comprise entre zéro et deux.

```powershell
PS> 1..20 |Sort-Object {$_ % 3}
18
3
15
6
12
9
1
16
13
10
7
4
19
11
8
14
5
17
2
20

PS> 1..20 |Sort-Object {$_ % 3} -Stable
3
6
9
12
15
18
1
4
7
10
13
16
19
2
5
8
11
14
17
20
```

La sortie du premier tri est correctement regroupée selon la valeur du modulo, mais les éléments individuels ne sont pas triés dans la plage du modulo. Le deuxième tri utilise l’option **stable** pour retourner un tri stable.

## PARAMETERS

### -Bas

Spécifie le nombre d’objets à obtenir à partir de la fin d’un tableau d’objets trié. Cela entraîne un tri stable.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Int32
Parameter Sets: Bottom
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CaseSensitive

Indique que le tri respecte la casse. Par défaut, les tris ne respectent pas la casse.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### -Culture

Spécifie la configuration culturelle à utiliser pour les tris. Utilisez `Get-Culture` pour afficher la configuration de la culture du système.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Décroissant

Indique que `Sort-Object` trie les objets dans l’ordre décroissant. La valeur par défaut est l'ordre croissant.

Pour trier plusieurs propriétés avec différents ordres de tri, utilisez une table de hachage. Par exemple, avec une table de hachage, vous pouvez trier une propriété par ordre croissant et une autre propriété dans l’ordre décroissant.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Pour trier les objets, envoyez-les dans le pipeline à `Sort-Object` . Si vous utilisez le paramètre **InputObject** pour envoyer une collection d’éléments, `Sort-Object` reçoit un objet qui représente la collection. Étant donné qu’un objet ne peut pas être trié, `Sort-Object` retourne la collection entière inchangée.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Propriété

Spécifie les noms de propriété que `Sort-Object` utilise pour trier les objets. Les caractères génériques sont autorisés.
Les objets sont triés en fonction des valeurs de propriété. Si vous ne spécifiez pas de propriété, effectue un `Sort-Object` Tri en fonction des propriétés par défaut du type d’objet ou des objets eux-mêmes.

Plusieurs propriétés peuvent être triées par ordre croissant, ordre décroissant ou combinaison d’ordres de tri. Lorsque vous spécifiez plusieurs propriétés, les objets sont triés par la première propriété. Si plusieurs objets ont la même valeur pour la première propriété, ces objets sont triés par la deuxième propriété. Ce processus se poursuit jusqu'à ce qu'il ne reste plus aucune propriété spécifiée ou aucun groupe d'objets.

La valeur du paramètre **Property** peut être une propriété calculée. Pour créer une propriété calculée, utilisez une table de hachage.

Les clés valides pour une table de hachage sont les suivantes :

- `expression` - `<string>` ou `<script block>`
- `ascending` ni `descending` - `<boolean>`

Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### -Haut

Spécifie le nombre d’objets à obtenir à partir du début d’un tableau d’objets trié. Cela entraîne un tri stable.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Int32
Parameter Sets: Top
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Unique

Indique que `Sort-Object` élimine les doublons et ne retourne que les membres uniques de la collection. La première instance d’une valeur unique est incluse dans la sortie triée.

**Unique** ne respecte pas la casse. Les chaînes qui diffèrent uniquement par la casse des caractères sont considérées comme identiques.
Par exemple, caractère et caractère.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stable

Les objets triés sont remis dans l’ordre dans lequel ils ont été reçus lorsque les critères de tri sont égaux.

Ce paramètre a été ajouté dans PowerShell v 6.2.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
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

### System. Management. Automation. PSObject

Vous pouvez diriger les objets à trier vers `Sort-Object` .

## SORTIES

### System. Management. Automation. PSObject

`Sort-Object` retourne les objets triés.

## REMARQUES

L' `Sort-Object` applet de commande trie les objets en fonction des propriétés spécifiées dans la commande ou des propriétés de tri par défaut du type d’objet. Les propriétés de tri par défaut sont définies à l’aide du `PropertySet` nommé `DefaultKeyPropertySet` dans un `types.ps1xml` fichier. Pour plus d’informations, consultez [about_Types.ps1XML](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).

Si un objet n’a pas l’une des propriétés spécifiées, la valeur de la propriété de cet objet est interprétée par `Sort-Object` comme **null** et placée à la fin de l’ordre de tri.

Lorsqu’aucune propriété de tri n’est disponible, PowerShell tente de comparer les objets eux-mêmes.
`Sort-Object` utilise la méthode **compare** pour chaque propriété. Si une propriété n’implémente pas **IComparable** , l’applet de commande convertit la valeur de la propriété en une chaîne et utilise la méthode **compare** pour **System. String** . Pour plus d’informations, consultez la [méthode PSObject. CompareTo (Object)](/dotnet/api/system.management.automation.psobject.compareto).

Si vous triez sur une propriété énumérée telle que **Status** , `Sort-Object` trie par valeurs d’énumération. Pour les services Windows, l’état **arrêté** a la valeur **1** et l' **exécution** a la valeur **4** .
L’état **arrêté** est trié avant l' **exécution en** raison des valeurs énumérées. Pour plus d’informations, consultez [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).

Les performances de l’algorithme de tri sont plus lentes lorsque vous procédez à un tri stable.

## LIENS CONNEXES

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Tee-Object](Tee-Object.md)
