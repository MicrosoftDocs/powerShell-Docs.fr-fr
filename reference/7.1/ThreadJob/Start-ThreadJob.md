---
external help file: ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 01/28/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: 9ac0570a5e26de47438a48817785836348de19cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202593"
---
# Start-ThreadJob

## SYNOPSIS
Crée des travaux en arrière-plan similaires à l’applet de commande `Start-Job` .

## SYNTAX

### ScriptBlock

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### FilePath

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

## Description

`Start-ThreadJob` crée des travaux en arrière-plan similaires à l’applet de commande `Start-Job` . La principale différence réside dans le fait que les tâches qui sont créées s’exécutent dans des threads distincts au sein du processus local. Par défaut, les travaux utilisent le répertoire de travail actuel de l’appelant qui a démarré le travail.

L’applet de commande prend également en charge un paramètre **ThrottleLimit** pour limiter le nombre de travaux en cours d’exécution en même temps. À mesure que d’autres tâches sont démarrées, elles sont mises en file d’attente et patientent jusqu’à ce que le nombre de travaux en cours descend en dessous de la limite de limitation.

## EXEMPLES

### Exemple 1 : créer des tâches en arrière-plan avec une limite de threads de 2

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### Exemple 2 : comparaison des performances des Start-Job et des Start-ThreadJob

Cet exemple montre la différence entre `Start-Job` et `Start-ThreadJob` . Les tâches exécutent l' `Start-Sleep` applet de commande pendant 1 seconde. Étant donné que les tâches s’exécutent en parallèle, le temps total d’exécution est d’environ 1 seconde, plus tout moment nécessaire pour créer les travaux.

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

Après avoir soustrait 1 seconde pour la durée d’exécution, vous pouvez constater qu' `Start-Job` environ 4,8 secondes sont nécessaires pour créer cinq travaux. `Start-ThreadJob` est 8 fois plus rapide, ce qui prend environ 0,6 secondes pour créer cinq tâches. Les résultats peuvent varier dans votre environnement, mais l’amélioration relative doit être la même.

### Exemple 3 : créer des travaux à l’aide d’InputObject

Dans cet exemple, le bloc de script utilise la `$input` variable pour recevoir l’entrée du paramètre **InputObject** . Pour ce faire, vous pouvez également rediriger les objets vers `Start-ThreadJob` .

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

## PARAMETERS

### -ArgumentList

Spécifie un tableau d’arguments, ou valeurs de paramètre, pour le script spécifié par les paramètres **filePath** ou **scriptblock** .

**Argumentlist** doit être le dernier paramètre sur la ligne de commande. Toutes les valeurs qui suivent le nom du paramètre sont des valeurs interprétées dans la liste d’arguments.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie un fichier de script à exécuter en tant que tâche en arrière-plan. Entrez le chemin d’accès et le nom de fichier du script. Le script doit se trouver sur l’ordinateur local ou dans un dossier accessible à l’ordinateur local.

Lorsque vous utilisez ce paramètre, PowerShell convertit le contenu du fichier de script spécifié en un bloc de script et exécute le bloc de script en tant que tâche en arrière-plan.

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

Spécifie les commandes à exécuter avant le début de la tâche. Placez les commandes entre accolades ( `{}` ) pour créer un bloc de script.

Utilisez ce paramètre pour préparer la session dans laquelle la tâche s'exécute. Par exemple, vous pouvez l’utiliser pour ajouter des fonctions et des modules à la session.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets utilisés comme entrée pour le bloc de script. Il permet également l’entrée de pipeline. Utilisez la `$input` variable automatique dans le bloc de script pour accéder aux objets d’entrée.

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

### -Name

Spécifie le nom convivial de la nouvelle tâche. Vous pouvez utiliser le nom pour identifier le travail à d’autres applets de commande de tâche, telles que l’applet de commande `Stop-Job` .

Le nom convivial par défaut est « Job # », où « # » est un nombre ordinal qui est incrémenté pour chaque tâche.

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

### -ScriptBlock

Spécifie les commandes à exécuter dans la tâche en arrière-plan. Placez les commandes entre accolades ( `{}` ) pour créer un bloc de script. Utilisez la `$Input` variable Automatic pour accéder à la valeur du paramètre **InputObject** . Ce paramètre est obligatoire.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StreamingHost

Ce paramètre fournit une méthode thread-safe pour permettre `Write-Host` à la sortie d’accéder directement à l’objet **PSHost** passé. Sans celui-ci, `Write-Host` la sortie est envoyée à la collection de flux de données d’informations sur le travail et n’apparaît pas dans une console hôte jusqu’à la fin de l’exécution des travaux.

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Ce paramètre limite le nombre de travaux en cours d’exécution en même temps. À mesure que les tâches sont démarrées, elles sont mises en file d’attente et attendent jusqu’à ce qu’un thread soit disponible dans le pool de threads pour exécuter le travail. La limite par défaut est de 5 threads.

La taille du pool de threads est globale pour la session PowerShell. La spécification d’un **ThrottleLimit** dans un appel définit la limite pour les appels suivants dans la même session.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

## SORTIES

### ThreadJob.ThreadJob

## REMARQUES

## LIENS CONNEXES

[Start-Job](../Microsoft.PowerShell.Core/Start-Job.md)

[Stop-Job](../Microsoft.PowerShell.Core/Stop-Job.md)

[Receive-Job](../Microsoft.PowerShell.Core/Receive-Job.md)

