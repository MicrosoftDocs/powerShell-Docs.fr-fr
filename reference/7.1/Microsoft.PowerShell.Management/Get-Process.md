---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: 1d4881638b616d93414851b98b0a75fca72169ff
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389791"
---
# Get-Process

## SYNOPSIS
Obtient les processus en cours d’exécution sur l’ordinateur local.

## SYNTAXE

### Nom (par défaut)

```
Get-Process [[-Name] <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### NameWithUserName

```
Get-Process [[-Name] <String[]>] -IncludeUserName [<CommonParameters>]
```

### Id

```
Get-Process -Id <Int32[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### IdWithUserName

```
Get-Process -Id <Int32[]> -IncludeUserName [<CommonParameters>]
```

### InputObject

```
Get-Process -InputObject <Process[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### InputObjectWithUserName

```
Get-Process -InputObject <Process[]> -IncludeUserName [<CommonParameters>]
```

## DESCRIPTION

L' `Get-Process` applet de commande obtient les processus sur un ordinateur local ou distant.

Sans paramètre, cette applet de commande obtient tous les processus sur l’ordinateur local. Vous pouvez également spécifier un processus particulier par nom de processus ou ID de processus (PID), ou passer un objet processus via le pipeline à cette applet de commande.

Par défaut, cette applet de commande retourne un objet processus qui contient des informations détaillées sur le processus et prend en charge des méthodes qui vous permettent de démarrer et d’arrêter le processus. Vous pouvez également utiliser les paramètres de l' `Get-Process` applet de commande pour obtenir les informations de version de fichier pour le programme qui s’exécute dans le processus et pour obtenir les modules chargés par le processus.

## EXEMPLES

### Exemple 1 : obtenir la liste de tous les processus actifs sur l’ordinateur local

```powershell
Get-Process
```

Cette commande obtient une liste de tous les processus actifs en cours d’exécution sur l’ordinateur local. Pour obtenir une définition de chaque colonne, consultez la section [Remarques](#notes) .

### Exemple 2 : obtenir toutes les données disponibles sur un ou plusieurs processus

```powershell
Get-Process winword, explorer | Format-List *
```

Cette commande obtient toutes les données disponibles sur les processus liés à Winword et à Explorer sur l'ordinateur. Elle utilise le paramètre **Name** pour spécifier les processus, mais elle omet le nom de paramètre facultatif. L’opérateur de pipeline `|` transmet les données à l’applet de commande `Format-List` , qui affiche toutes les propriétés disponibles `*` des objets de processus Winword et Explorer.

Vous pouvez également identifier un processus à l'aide de son identificateur de processus. Par exemple, `Get-Process -Id 664, 2060`.

### Exemple 3 : obtenir tous les processus avec une plage de travail supérieure à une taille spécifiée

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

Cette commande obtient tous les processus qui ont une plage de travail supérieure à 20 Mo. Elle utilise l' `Get-Process` applet de commande pour récupérer tous les processus en cours d’exécution. L’opérateur de pipeline `|` passe les objets de processus à l’applet de commande `Where-Object` , qui sélectionne uniquement l’objet dont la valeur est supérieure à 20 millions octets pour la propriété de la **plage** de temps.

La **plage** de temps est l’une des nombreuses propriétés des objets de processus. Pour afficher toutes les propriétés, tapez `Get-Process | Get-Member` . Par défaut, les valeurs de toutes les propriétés Amount sont exprimées en octets, bien que l'affichage par défaut les répertorie en kilo-octets et mégaoctets.

### Exemple 4 : répertorier les processus sur l’ordinateur dans des groupes en fonction de la priorité

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

Ces commandes répertorient les processus sur l’ordinateur dans des groupes en fonction de leur classe de priorité. La première commande récupère tous les processus sur l’ordinateur, puis les stocke dans la `$A` variable.

La deuxième commande dirige l’objet **processus** stocké dans la `$A` variable vers l’applet de commande `Get-Process` , puis vers l’applet de commande `Format-Table` , qui met en forme les processus à l’aide de la vue **Priority** .

La vue **Priority** et d’autres vues sont définies dans les fichiers de format ps1xml dans le répertoire de racine PowerShell ( `$pshome` ).

### Exemple 5 : ajouter une propriété à l’affichage de sortie standard Get-Process

```powershell
Get-Process pwsh | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 .           pwsh
     6 23500 31348   142 2.75   4016 .           pwsh
    27 54572 54520   576 5.52   4428 .           pwsh
```

Cet exemple récupère des processus à partir de l’ordinateur local et d’un ordinateur distant (S1). Les processus récupérés sont dirigés vers la `Format-Table` commande qui ajoute la propriété **MachineName** à l' `Get-Process` affichage de sortie standard.

### Exemple 6 : obtenir des informations sur la version d’un processus

```powershell
Get-Process pwsh -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.2            6.1.2            C:\Program Files\PowerShell\6\pwsh.exe
```

Cette commande utilise le paramètre **FileVersionInfo** pour obtenir les informations de version du fichier pwsh.exe qui est le module principal du processus PowerShell.

Pour exécuter cette commande avec des processus que vous ne possédez pas sur Windows Vista et les versions ultérieures de Windows, vous devez ouvrir PowerShell avec l’option Exécuter en tant qu’administrateur.

### Exemple 7 : récupération des modules chargés avec le processus spécifié

```powershell
Get-Process SQL* -Module
```

Cette commande utilise le paramètre **module** pour obtenir les modules qui ont été chargés par le processus.
Cette commande obtient les modules pour les processus dont les noms commencent par SQL.

Pour exécuter cette commande sur Windows Vista et les versions ultérieures de Windows avec des processus que vous ne possédez pas, vous devez démarrer PowerShell avec l’option Exécuter en tant qu’administrateur.

### Exemple 8 : Rechercher le propriétaire d’un processus

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     pwsh
```

Cette commande montre comment rechercher le propriétaire d'un processus.
Sur Windows, le paramètre **IncludeUserName** nécessite des droits d’utilisateur élevés (exécuter en tant qu’administrateur).
La sortie révèle que le propriétaire est Domain01\user01.

### Exemple 9 : utiliser une variable automatique pour identifier le processus qui héberge la session active

```powershell
Get-Process pwsh
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21     105.95       4.33    1192  10 pwsh
    79    83.81     117.61       2.16   10580  10 pwsh
```

```powershell
Get-Process -Id $PID
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21      77.53       4.39    1192  10 pwsh
```

Ces commandes montrent comment utiliser la `$PID` variable automatique pour identifier le processus qui héberge la session PowerShell active. Vous pouvez utiliser cette méthode pour distinguer le processus hôte des autres processus PowerShell que vous pouvez arrêter ou fermer.

La première commande obtient tous les processus PowerShell dans la session active.

La deuxième commande obtient le processus PowerShell qui héberge la session active.

### Exemple 10 : obtenir tous les processus qui ont un titre de fenêtre principale et les afficher dans une table

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

Cette commande obtient tous les processus qui ont un titre de fenêtre principale et les affiche dans un tableau avec l'ID de processus et le nom du processus.

La propriété **mainWindowTitle** n’est qu’une des nombreuses propriétés utiles de l’objet **Process** qui `Get-Process` retourne. Pour afficher toutes les propriétés, dirigez les résultats d’une `Get-Process` commande vers l' `Get-Member` applet de commande `Get-Process | Get-Member` .

## PARAMÈTRES

### -FileVersionInfo

Indique que cette applet de commande obtient les informations de version de fichier pour le programme qui s’exécute dans le processus.

Sur Windows Vista et les versions ultérieures de Windows, vous devez ouvrir PowerShell avec l’option Exécuter en tant qu’administrateur pour utiliser ce paramètre sur les processus que vous ne possédez pas.

Pour obtenir les informations de version de fichier d’un processus sur un ordinateur distant, utilisez l’applet de commande `Invoke-Command` .

L’utilisation de ce paramètre revient à obtenir la propriété **propriété MainModule. FileVersionInfo** de chaque objet processus. Lorsque vous utilisez ce paramètre, `Get-Process` retourne un **FileVersionInfo** objet FileVersionInfo **System. Diagnostics. FileVersionInfo** , et non un objet processus. Par conséquent, vous ne pouvez pas diriger la sortie de la commande vers une applet de commande qui attend un objet processus, tel que `Stop-Process` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Spécifie un ou plusieurs processus par identificateur de processus (PID). Lorsque vous spécifiez plusieurs identificateurs, séparez-les à l'aide de virgules. Pour rechercher le PID d’un processus, tapez `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: Id, IdWithUserName
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeUserName

Indique que la valeur UserName de l’objet **Process** est retournée avec les résultats de la commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie un ou plusieurs objets processus. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Module

Indique que cette applet de commande obtient les modules qui ont été chargés par les processus.

Sur Windows Vista et les versions ultérieures de Windows, vous devez ouvrir PowerShell avec l’option **exécuter en tant qu’administrateur** pour utiliser ce paramètre sur les processus que vous ne possédez pas.

Pour obtenir les modules qui ont été chargés par un processus sur un ordinateur distant, utilisez l' `Invoke-Command` applet de commande.

Ce paramètre équivaut à obtenir la propriété **modules** de chaque objet processus. Lorsque vous utilisez ce paramètre, cette applet de commande retourne un objet **ProcessModule** **System. Diagnostics. ProcessModule** , et non un objet processus. Par conséquent, vous ne pouvez pas diriger la sortie de la commande vers une applet de commande qui attend un objet processus, tel que `Stop-Process` .

Lorsque vous utilisez les paramètres *module* et **FileVersionInfo** dans la même commande, cette applet de commande retourne un objet **FileVersionInfo** avec des informations sur la version de fichier de tous les modules.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un ou plusieurs processus en fonction de leur nom de processus. Vous pouvez taper plusieurs noms de processus (séparés par des virgules) et utiliser des caractères génériques. Le nom de paramètre (« Name ») est facultatif.

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.Diagnostics.Process

Vous pouvez diriger un objet processus vers cette applet de commande.

## SORTIES

### System. Diagnostics. Process, System. Diagnostics. FileVersionInfo, System. Diagnostics. ProcessModule

Par défaut, cette applet de commande retourne un objet **System. Diagnostics. Process** . Si vous utilisez le paramètre **FileVersionInfo** , il retourne un objet **System. Diagnostics. FileVersionInfo** . Si vous utilisez le paramètre **module** sans le paramètre **FileVersionInfo** , il retourne un objet **System. Diagnostics. ProcessModule** .

## REMARQUES

- Vous pouvez également faire référence à cette applet de commande à l’aide de ses alias intégrés, PS et GPS. Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- Sur les ordinateurs qui exécutent une version 64 bits de Windows, la version 64 bits de PowerShell obtient uniquement les modules de processus 64 bits et la version 32 bits de PowerShell obtient uniquement les modules de processus 32 bits.
- Vous pouvez utiliser les propriétés et les méthodes de l’objet Win32_Process Windows Management Instrumentation (WMI) dans PowerShell. Pour plus d’informations, consultez `Get-WmiObject` et le kit de développement logiciel (SDK) WMI.
- L'affichage par défaut d'un processus est un tableau comportant les colonnes suivantes. Pour obtenir une description de toutes les propriétés des objets process, consultez [Propriétés du processus](/dotnet/api/system.diagnostics.process).
  - Handles : nombre de handles ouverts par le processus.
  - NPM (K) : quantité de mémoire non paginée utilisée par le processus, en kilo-octets.
  - PM (K) : quantité de mémoire paginable utilisée par le processus, en kilo-octets.
  - WS (K) : taille de la plage de travail du processus, en kilo-octets.
    La plage de travail inclut les pages de mémoire récemment référencées par le processus.
  - Machine virtuelle (M) : quantité de mémoire virtuelle utilisée par le processus, en mégaoctets.
    La mémoire virtuelle inclut le stockage dans les fichiers de pagination sur le disque.
  - PROCESSEUR (s) : quantité de temps processeur utilisée par le processus sur tous les processeurs, en secondes.
  - ID : ID de processus (PID) du processus.
  - ProcessName : nom du processus. Pour obtenir des informations sur les concepts liés aux processus, consultez le Glossaire du Centre d'aide et de support et l'Aide du Gestionnaire des tâches.
- Vous pouvez également utiliser les autres vues intégrées des processus disponibles avec `Format-Table` , comme **StartTime** et **Priority** , et vous pouvez concevoir vos propres vues.

## LIENS CONNEXES

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
