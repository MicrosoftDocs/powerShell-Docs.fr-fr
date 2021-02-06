---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: afc08b263d75f8a728ce6d64cc7ede0a639df196
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595494"
---
# Trace-Command

## SYNOPSIS
Configure et démarre un suivi de la commande ou de l'expression spécifiée.

## SYNTAXE

### expressionSet (par défaut)

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### commandSet

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## Description
L' `Trace-Command` applet de commande configure et démarre une trace de l’expression ou de la commande spécifiée.
Elle fonctionne comme Set-TraceSource, si ce n'est qu'elle s'applique uniquement à la commande spécifiée.

## EXEMPLES

### Exemple 1 : suivre le traitement des métadonnées, la liaison de paramètre et une expression

Cet exemple démarre une trace du traitement des métadonnées, de la liaison de paramètres et de la création et de la destruction des applets de commande de l' `Get-Process Notepad` expression.

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

Elle utilise le paramètre **Name** pour spécifier les sources de suivi, le paramètre **expression** pour spécifier la commande et le paramètre **PSHost** pour envoyer la sortie vers la console. Comme elle ne spécifie pas d’options de suivi ni d’options d’écouteur, la commande utilise les valeurs par défaut :

- Tout pour les options de suivi
- Aucun pour les options d’écouteur

### Exemple 2 : suivre les actions des opérations ParameterBinding

Cet exemple effectue le suivi des actions des opérations **ParameterBinding** de PowerShell pendant qu’il traite une `Get-Alias` expression qui accepte les entrées du pipeline.

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

Dans `Trace-Command` , le paramètre **InputObject** passe un objet à l’expression en cours de traitement au cours de la trace.

La première commande stocke la chaîne `i*` dans la `$A` variable. La deuxième commande utilise l' `Trace-Command` applet de commande avec la source de suivi ParameterBinding. Le paramètre **PSHost** envoie la sortie vers la console.

L’expression en cours de traitement est `Get-Alias $Input` , où la `$Input` variable est associée au paramètre **InputObject** . Le paramètre **InputObject** passe la variable `$A` à l’expression. En effet, la commande en cours de traitement pendant la trace est `Get-Alias -InputObject $A" or "$A | Get-Alias` .

## PARAMETERS

### -ArgumentList

Spécifie les paramètres et les valeurs de paramètre pour la commande faisant l'objet d'un suivi. L'alias d'**ArgumentList** est **Args**. Cette fonctionnalité est particulièrement utile pour déboguer des paramètres dynamiques.

Pour plus d’informations sur le comportement de **argumentlist**, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

Spécifie une commande qui est en cours de traitement au cours du suivi.

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Débogueur

Indique que l’applet de commande envoie la sortie de trace au débogueur. Vous pouvez afficher la sortie dans n'importe quel débogueur en mode noyau ou en mode utilisateur, ou dans Visual Studio. Ce paramètre sélectionne également l'écouteur de suivi par défaut.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Expression

Spécifie l'expression qui est en cours de traitement au cours du suivi. Mettez l’expression entre accolades ( `{}` ).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie un fichier auquel l’applet de commande envoie la sortie de trace. Ce paramètre sélectionne également l'écouteur de suivi de fichier.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur. Utilisé avec le paramètre **filePath** . Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie l’entrée de l’expression en cours de traitement au cours de la trace. Vous pouvez entrer une variable qui représente l'entrée que l'expression accepte ou passer un objet via le pipeline.

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

### -ListenerOption

Spécifie des données facultatives pour le préfixe de chaque message de trace dans la sortie. Les valeurs valides pour ce paramètre sont :

- None
- LogicalOperationStack
- DateTime
- Timestamp
- ProcessId
- ThreadId
- Pile des appels

**None** est la valeur par défaut.

Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "ThreadID,ProcessID".

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie un tableau de composants PowerShell suivis. Entrez le nom de la source de suivi de chaque composant. Les caractères génériques sont autorisés. Pour rechercher les sources de suivi sur votre ordinateur, tapez `Get-TraceSource` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Option

Détermine le type des événements qui font l'objet d'un suivi. Les valeurs valides pour ce paramètre sont :

- None
- Constructeur
- Dispose
- Finaliseur
- Méthode
- Propriété
- Délégués
- Événements
- Exception
- Verrouillage
- Error
- Erreurs
- Avertissement
- Commentaires
- WriteLine
- Données
- Scope (Étendue)
- ExecutionFlow
- Assert
- Tous

« All » est la valeur par défaut.

Les valeurs suivantes sont des combinaisons d'autres valeurs :

- ExecutionFlow : (Constructor, dispose, Finalizer, Method, Delegates, Events et Scope)
- Données : (Constructor, dispose, Finalizer, Property, verbose et WriteLine)
- Erreurs : (erreur et exception).

Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "Constructor,Dispose".

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

Indique que l’applet de commande envoie la sortie de suivi à l’hôte PowerShell. Ce paramètre sélectionne également l'écouteur de suivi de PSHost.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
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

Vous pouvez diriger les objets qui représentent l’entrée vers l’expression vers `Trace-Command` .

## SORTIES

### System. Management. Automation. PSObject

Retourne le suivi de la commande dans le flux de débogage.

## REMARQUES

- Le suivi est une méthode que les développeurs utilisent pour déboguer et affiner les programmes. Pendant le suivi, le programme génère des messages détaillés sur chaque étape du traitement interne.

- Les applets de commande PowerShell Tracing sont conçues pour aider les développeurs PowerShell, mais elles sont disponibles pour tous les utilisateurs. Elles vous permettent de surveiller quasiment chaque aspect de la fonctionnalité de l'interpréteur de commandes.

- Pour rechercher les composants PowerShell activés pour le suivi, tapez `Get-Help Get-TraceSource` .

  Une source de suivi est la partie de chaque composant PowerShell qui gère le suivi et génère des messages de suivi pour le composant. Pour suivre un composant, vous identifiez sa source de suivi.

  Un écouteur de suivi reçoit la sortie de la trace et l’affiche à l’utilisateur. Vous pouvez choisir d’envoyer les données de trace à un débogueur en mode utilisateur ou en mode noyau, à l’hôte ou à la console, à un fichier ou à un écouteur personnalisé dérivé de la classe **System. Diagnostics. TraceListener** .

- Lorsque vous utilisez le jeu de paramètres commandSet, PowerShell traite la commande comme elle serait traitée dans un pipeline. Par exemple, la découverte de commande n'est pas répétée pour chaque objet entrant.

- Les noms des paramètres **Name**, **expression**, **option** et **Command** sont facultatifs. Si vous omettez les noms de paramètres, les valeurs des paramètres sans nom doivent apparaître dans cet ordre : **nom**, **expression**, **option** ou **nom**, **commande**, **option**. Si vous incluez les noms de paramètres, les paramètres peuvent apparaître dans tout ordre.

## LIENS CONNEXES

[Get-TraceSource](Get-TraceSource.md)

[Measure-Command](Measure-Command.md)

[Set-TraceSource](Set-TraceSource.md)

