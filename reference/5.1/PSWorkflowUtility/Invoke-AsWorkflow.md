---
external help file: Microsoft.PowerShell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSWorkflowUtility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflowutility/invoke-asworkflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-AsWorkflow
ms.openlocfilehash: b96bce9fe4d574fe2b7e9c7c0f1e05ee0508adce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202965"
---
# Invoke-AsWorkflow

## SYNOPSIS
Exécute une commande ou une expression comme un workflow Windows PowerShell.

## SYNTAX

### Command (par défaut)

```
Invoke-AsWorkflow [-CommandName <String>] [-Parameter <Hashtable>] [-InputObject <Object>] [<CommonParameters>]
```

### Expression

```
Invoke-AsWorkflow [-Expression <String>] [-InputObject <Object>] [<CommonParameters>]
```

## Description

Le `Invoke-AsWorkflow` flux de travail exécute une commande ou une expression comme un script inline dans un Workflow.
Ces workflows utilisent la sémantique de workflow standard, ont tous les paramètres communs de workflow et tous les avantages de workflow, notamment la possibilité d'arrêter, de reprendre et de récupérer.

Les workflows sont conçus pour les commandes de longue durée collectant des données essentielles, mais peuvent être utilisés pour exécuter toute commande.
Pour plus d’informations, consultez [about_Workflows](../PSWorkflow/About/about_Workflows.md).

Vous pouvez également ajouter des paramètres communs de workflow à cette commande.
Pour plus d’informations sur les paramètres communs de workflow, consultez [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)

Ce workflow est introduit dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : exécuter une applet de commande en tant que Workflow

```powershell
Invoke-AsWorkflow -PSComputerName (Get-Content Servers.txt) -CommandName Get-ExecutionPolicy
```

```output
PSComputerName                     PSSourceJobInstanceId                   Value
--------------                     ---------------------                   -----
Server01                           77b1cdf8-8226-4662-9067-cd2fa5c3b711    AllSigned
Server02                           a33542d7-3cdd-4339-ab99-0e7cd8e59462    Unrestricted
Server03                           279bac28-066a-4646-9497-8fcdcfe9757e    AllSigned
localhost                          0d858009-2cc4-47a4-a2e0-da17dc2883d0    RemoteSigned
```

Cette commande exécute l' `Get-ExecutionPolicy` applet de commande en tant que flux de travail sur des centaines d’ordinateurs.

La commande utilise le paramètre **CommandName** pour spécifier l'applet de commande exécutée dans le workflow.
Elle utilise le paramètre commun de workflow **PSComputerName** pour spécifier les ordinateurs sur lesquels la commande s'exécute.
La valeur du paramètre **PSComputerName** est une `Get-Content` commande qui obtient une liste de noms d’ordinateurs à partir du fichier Servers.txt.
La valeur du paramètre est placée entre parenthèses pour indiquer à Windows PowerShell d’exécuter la `Get-Command` commande avant d’utiliser la valeur.

Comme avec toutes les commandes à distance, si la commande s'exécute sur l'ordinateur local (si la valeur du paramètre PSComputerName inclut l'ordinateur local), vous devez démarrer Windows PowerShell avec l'option « Exécuter en tant qu'administrateur ».

### Exemple 2 : exécuter une applet de commande avec des paramètres

```powershell
$s = Import-Csv .\Servers.csv -Header ServerName, ServerID
Invoke-AsWorkflow -CommandName Get-ExecutionPolicy -Parameter @{Scope="Process"} -PSComputerName {$s.ServerName} -PSConnectionRetryCount 5
```

La première commande utilise l' `Import-Csv` applet de commande pour créer un objet à partir du contenu du fichier Servers.csv. La commande utilise le `Header` paramètre pour créer une `ServerName` propriété pour la colonne qui contient les noms des ordinateurs cibles, également appelés « nœuds distants ». La commande enregistre le résultat dans la `$s` variable.

La deuxième commande utilise le `Invoke-AsWorkflow` flux de travail pour exécuter une `Get-ExecutionPolicy` commande sur les ordinateurs du fichier Servers.csv. La commande utilise le paramètre **CommandName** de `Invoke-AsWorkflow`  pour spécifier la commande à exécuter dans le Workflow. Elle utilise le `Parameter` paramètre de `Invoke-AsWorkflow` pour spécifier le `Scope` paramètre de l' `Get-ExecutionPolicy` applet de commande avec la valeur **Process** . La commande utilise également le `PSConnectionRetryCount` paramètre commun de flux de travail pour limiter la commande à cinq tentatives sur chaque ordinateur et le `PSComputerName` paramètre commun de flux de travail pour spécifier les noms des nœuds distants (ordinateurs cibles). La valeur du `PSComputerName` paramètre est une expression qui obtient la `ServerName` propriété de chaque objet dans la `$s` variable.

Ces commandes exécutent une `Get-ExecutionPolicy` commande en tant que flux de travail sur des centaines d’ordinateurs.
La commande utilise le `Scope` paramètre de l' `Get-ExecutionPolicy` applet de commande avec la valeur **Process** pour obtenir la stratégie d’exécution dans la session active.

### Exemple 3 : exécuter une expression en tant que flux de travail

```powershell
Invoke-AsWorkflow -Expression "ipconfig /all" -PSComputerName (Get-Content DomainControllers.txt) -AsJob -JobName IPConfig
```

```output
Id     Name          PSJobTypeName   State         HasMoreData   Location                Command
--     ----          -------------   -----         -----------   --------                -------
2      IpConfig      PSWorkflowJob   Completed     True          Server01, Server01...   Invoke-AsWorkflow
```

Cette commande utilise le `Invoke-AsWorkflow` flux de travail pour exécuter une commande ipconfig en tant que tâche de workflow sur les ordinateurs figurant dans le fichier DomainControllers.txt.

La commande utilise le `Expression` paramètre pour spécifier l’expression à exécuter.
Elle utilise le `PSComputerName` paramètre commun de flux de travail pour spécifier les noms des nœuds distants (ordinateurs cibles).

La commande utilise également les `AsJob` paramètres communs de flux de travail et `JobName` pour exécuter le workflow en tant que tâche en arrière-plan sur chaque ordinateur avec le nom de travail « ipconfig ».

La commande retourne un `ContainerParentJob` objet ( `System.Management.Automation.ContainerParentJob` ) qui contient les tâches de workflow sur chaque ordinateur.

## PARAMETERS

### -CommandName

Exécute l'applet de commande ou la fonction avancée spécifiée comme un workflow.
Entrez le nom de l’applet de commande ou de la fonction, tel que `Update-Help` , `Set-ExecutionPolicy` ou `Set-NetFirewallRule` .

```yaml
Type: System.String
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Expression

Spécifie l’expression que cette applet de commande exécute en tant que flux de travail.
Entrez l’expression sous la forme d’une chaîne, telle que `"ipconfig /all"` .
Si l'expression comprend des espaces ou des caractères spéciaux, placez l'expression entre guillemets.

```yaml
Type: System.String
Parameter Sets: Expression
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### Paramètres 

Spécifie les paramètres et les valeurs de paramètre de la commande spécifiée dans le `CommandName` paramètre.
Entrez une table de hachage dans laquelle chaque clé est un nom de paramètre et sa valeur est la valeur du paramètre, par exemple `@{ExecutionPolicy="AllSigned"}` .

Pour plus d’informations sur les tables de hachage, consultez [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Utilisé pour autoriser l’entrée de pipeline.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

### WorkflowCommonParameters

Cette applet de commande prend également en charge les paramètres communs spécifiques au flux de travail.
Pour plus d’informations, consultez [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md).

## ENTRÉES

### System.Object

Vous pouvez diriger n’importe quel objet vers le `InputObject` paramètre.

## SORTIES

### Aucun

Cette commande ne génère aucune sortie.
Toutefois, elle exécute le workflow, ce qui peut générer une sortie.

## REMARQUES

## LIENS CONNEXES

[New-PSWorkflowExecutionOption](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[New-PSWorkflowSession](../PSWorkflow/New-PSWorkflowSession.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_Workflow_Common_Parameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)
