---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 7a1f7e2879b0eeefe8771a5e5a8bf763e48ff106
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201234"
---
# Set-TraceSource

## SYNOPSIS
Configure, démarre et arrête un suivi des composants PowerShell.

## SYNTAX

### optionsSet (par défaut)

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### removeAllListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### removeFileListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## Description

L’applet de commande **Set-TraceSource** configure, démarre et arrête une trace d’un composant PowerShell.
Vous pouvez l'utiliser pour spécifier quels composants seront tracés et où la sortie du suivi est envoyée.

## EXEMPLES

### Exemple 1 : tracer le composant ParameterBinding

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

Cette commande démarre le suivi pour le composant ParameterBinding de PowerShell.
Elle utilise le paramètre *Name* pour spécifier la source de suivi, le paramètre *option* pour sélectionner les événements de trace ExecutionFlow et le paramètre *PSHost* pour sélectionner l’écouteur hôte PowerShell, qui envoie la sortie vers la console.
Le paramètre *ListenerOption* ajoute les valeurs ProcessId et timestamp au préfixe du message de suivi.

### Exemple 2 : arrêter une trace

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

Cette commande arrête la trace du composant ParameterBinding de PowerShell.
Elle utilise le paramètre *Name* pour identifier le composant qui a été suivi et le paramètre *RemoveListener* pour identifier l’écouteur de suivi.

## PARAMETERS

### -Débogueur

Indique que l’applet de commande envoie la sortie de trace au débogueur.
Vous pouvez afficher la sortie dans n'importe quel débogueur en mode noyau ou en mode utilisateur, ou bien dans Microsoft Visual Studio.
Ce paramètre sélectionne également l'écouteur de suivi par défaut.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie un fichier auquel cette applet de commande envoie la sortie de trace.
Ce paramètre sélectionne également l'écouteur de suivi de fichier.
Si vous utilisez ce paramètre pour démarrer le suivi, utilisez le paramètre *RemoveFileListener* pour arrêter la trace.

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Indique que l’applet de commande remplace un fichier en lecture seule.
Utilisez avec le paramètre *filePath* .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListenerOption

Spécifie des données facultatives pour le préfixe de chaque message de trace dans la sortie.
Les valeurs valides pour ce paramètre sont :

- Aucun
- LogicalOperationStack
- DateTime
- Timestamp
- ProcessId
- ThreadId
- Pile des appels

None est la valeur par défaut.

Pour spécifier plusieurs options, séparez-les par des virgules, mais sans espaces, et placez-les entre guillemets, par exemple "ThreadID,ProcessID".

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie les composants qui sont suivis.
Entrez le nom de la source de suivi de chaque composant.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Option

Spécifie le type des événements qui sont suivis.
Les valeurs valides pour ce paramètre sont :

- Aucun
- Constructeur
- Dispose
- Finaliseur
- Méthode
- Propriété
- Délégués
- Événements
- Exception
- Verrouillage
- Erreur
- Erreurs
- Avertissement
- Commentaires
- WriteLine
- Données
- Étendue
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
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourne un objet représentant l’élément que vous utilisez.
Par défaut, cette applet de commande ne génère aucun résultat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

indique que cette applet de commande envoie la sortie de suivi à l’hôte PowerShell.
Ce paramètre sélectionne également l'écouteur de suivi de PSHost.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveFileListener

Arrête le suivi en supprimant l'écouteur de suivi de fichier associé au fichier spécifié.
Entrez le chemin d'accès et le nom du fichier de sortie du suivi.

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveListener

Arrête le suivi en supprimant l'écouteur de suivi.

Utilisez les valeurs suivantes avec *RemoveListener* :

- Pour supprimer PSHost (console), tapez `Host` .
- Pour supprimer le débogueur, tapez `Debug` .
- Pour supprimer tous les écouteurs de suivi, tapez `*` .

Pour supprimer l’écouteur de suivi de fichier, utilisez le paramètre *RemoveFileListener* .

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
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

### System.String

Vous pouvez diriger une chaîne qui contient un nom vers **Set-TraceSource** .

## SORTIES

### None ou System. Management. Automation. PSTraceSource

Quand vous utilisez le paramètre *PassThru* , **Set-TraceSource** génère un objet **System. Management. Automation. PSTraceSource** qui représente la session de trace.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

* Le suivi est une méthode que les développeurs utilisent pour déboguer et affiner les programmes. Pendant le suivi, le programme génère des messages détaillés sur chaque étape du traitement interne.

  Les applets de commande PowerShell Tracing sont conçues pour aider les développeurs PowerShell, mais elles sont disponibles pour tous les utilisateurs.
Ils vous permettent de surveiller presque tous les aspects de la fonctionnalité de PowerShell.

  Une source de suivi est la partie de chaque composant PowerShell qui gère le suivi et génère des messages de suivi pour le composant.
Pour suivre un composant, vous identifiez sa source de suivi.

  Un écouteur de suivi reçoit la sortie de la trace et l’affiche à l’utilisateur.
Vous pouvez choisir d’envoyer les données de trace à un débogueur en mode utilisateur ou en mode noyau, à la console, à un fichier ou à un écouteur personnalisé dérivé de la classe **System. Diagnostics. TraceListener** .

* Pour démarrer une trace, utilisez le paramètre *Name* pour spécifier une source de suivi et les paramètres *filePath* , *Debugger* ou *PSHost* pour spécifier un écouteur (une destination pour la sortie). Utilisez le paramètre *options* pour déterminer les types d’événements qui sont suivis et le paramètre *ListenerOption* pour configurer la sortie de trace.
* Pour modifier la configuration d’une trace, entrez une commande **Set-TraceSource** comme vous le feriez pour démarrer une trace. PowerShell reconnaît que la source de suivi est déjà en cours de suivi. Elle arrête le suivi, ajoute la nouvelle configuration, puis démarre ou redémarre le suivi.
* Pour arrêter une trace, utilisez le paramètre *RemoveListener* . Pour arrêter une trace qui utilise l’écouteur de fichiers (une trace démarrée à l’aide du paramètre *filePath* ), utilisez le paramètre *RemoveFileListener* . Quand vous supprimez l'écouteur, le suivi s'arrête.
* Pour déterminer les composants qui peuvent être suivis, utilisez Get-TraceSource. Les sources de suivi pour chaque module sont chargées automatiquement lorsque le composant est en cours d’utilisation, et elles s’affichent dans la sortie de la **récupération** de l’élément.

## LIENS CONNEXES

[Get-TraceSource](Get-TraceSource.md)

[Trace-Command](Trace-Command.md)
