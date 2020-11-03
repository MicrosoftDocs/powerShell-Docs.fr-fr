---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/register-wmievent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-WmiEvent
ms.openlocfilehash: be29ce6376dea7686c0c063cc5528fbc7d840a9d
ms.sourcegitcommit: 41b072f0b6046d619b0e7f758982783fb648a3d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2020
ms.locfileid: "93205810"
---
# Register-WmiEvent

## SYNOPSIS
S'abonne à un événement Windows Management Instrumentation (WMI).

## SYNTAX

### classe (par défaut)

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Class] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### query

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Query] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## Description

L' `Register-WmiEvent` applet de commande s’abonne aux événements Windows Management Instrumentation (WMI) sur l’ordinateur local ou sur un ordinateur distant.

Lorsque l'événement WMI abonné se déclenche, il est ajouté à la file d'attente des événements dans votre session locale, même si l'événement se produit sur un ordinateur distant. Pour récupérer des événements dans la file d’attente d’événements, utilisez l’applet de commande `Get-Event` .

Vous pouvez utiliser les paramètres de `Register-WmiEvent` pour vous abonner à des événements sur des ordinateurs distants et pour spécifier les valeurs de propriété des événements qui peuvent vous aider à identifier l’événement dans la file d’attente. Vous pouvez également utiliser le paramètre **action** pour spécifier les actions à entreprendre lorsqu’un événement abonné est déclenché.

Lorsque vous vous abonnez à un événement, un abonné est ajouté à votre session. Pour obtenir les abonnés aux événements dans la session, utilisez l'applet de commande `Get-EventSubscriber`. Pour annuler l'abonnement, utilisez l'applet de commande `Unregister-Event`, ce qui supprime l'abonné aux événements de la session.

Les nouvelles applets de commande Common Information Model (CIM), ont introduit Windows PowerShell 3,0, effectuent les mêmes tâches que les applets de commande WMI. Les applets de commande CIM sont conformes aux normes WS-Management (WSMan) et à la norme CIM, qui permet aux cmdlets d’utiliser les mêmes techniques pour gérer les ordinateurs qui exécutent le système d’exploitation Windows et ceux qui exécutent d’autres systèmes d’exploitation. Au lieu d’utiliser `Register-WmiEvent` , envisagez d’utiliser l’applet [de commande Register-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) .

## EXEMPLES

### Exemple 1 : s’abonner à des événements générés par une classe

Cette commande s’abonne aux événements générés par la classe **Win32_ProcessStartTrace** . Cette classe déclenche un événement à chaque démarrage d'un processus.

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
```

### Exemple 2 : s’abonner aux événements de création d’un processus

Cette commande utilise une requête pour s'abonner aux événements de création de l'instance Win32_process.

```powershell
$wmiParameters = @{
  Query = "select * from __instancecreationevent within 5 where targetinstance isa 'win32_process'"
  SourceIdentifier = "WMIProcess"
  MessageData = "Test 01"
  TimeOut = 500
}
Register-WmiEvent @wmiParameters
```

### Exemple 3 : utiliser une action pour répondre à un événement

Cet exemple montre comment utiliser une action pour répondre à un événement. Dans ce cas, lorsqu’un processus démarre, toutes les `Start-Process` commandes de la session active sont écrites dans un fichier XML.

```powershell
$action = { Get-History | where { $_.commandline -like "*start-process*" } | export-cliXml "commandHistory.clixml" }
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

```Output
Id    Name            State      HasMoreData   Location  Command
--    ----            -----      -----------   --------  -------
1     ProcessStarted  NotStarted False                   get-history | where {...
```

Quand vous utilisez le paramètre d' **action** , `Register-WmiEvent` retourne une tâche en arrière-plan qui représente l’action d’événement. Vous pouvez utiliser les applets de commande **Job** , telles que `Get-Job` et `Receive-Job` , pour gérer la tâche d’événement.

Pour plus d'informations, consultez about_Jobs.

### Exemple 4 : s’inscrire pour des événements sur un ordinateur distant

Cet exemple inscrit des événements sur l'ordinateur distant Server01.

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "Start" -Computername Server01
Get-Event -SourceIdentifier "Start"
```

WMI retourne les événements à l'ordinateur local et les stocke dans la file d'attente des événements dans la session active. Pour récupérer les événements, exécutez une `Get-Event` commande locale.

## PARAMETERS

### -Action

Spécifie les commandes qui gèrent les événements. Les commandes dans le paramètre **action** s’exécutent quand un événement est déclenché au lieu d’envoyer l’événement à la file d’attente d’événements. Placez les commandes entre accolades ( `{}` ) pour créer un bloc de script.

La valeur de l' **action** peut inclure `$Event` les `$EventSubscriber` variables automatiques,,, `$Sender` `$EventArgs` et `$Args` , qui fournissent des informations sur l’événement au bloc de script de l' **action** . Pour plus d'informations, consultez about_Automatic_Variables.

Lorsque vous spécifiez une action, `Register-WmiEvent` retourne un objet de tâche d’événement qui représente cette action. Vous pouvez utiliser les applets de commande qui contiennent le nom du **travail** (les applets de commande **Job** ) pour gérer la tâche d’événement.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Classe

Spécifie l'événement auquel vous vous abonnez. Entrez la classe WMI qui génère les événements. Une **classe** ou un paramètre de **requête** est requis dans chaque commande.

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Spécifie le nom de l’ordinateur sur lequel la commande s’exécute. La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, l'adresse IP ou le nom de domaine complet de l'ordinateur. Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point ( `.` ) ou localhost.

Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell. Vous pouvez utiliser le paramètre **ComputerName** même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Suivant

Indique que cette applet de commande envoie des événements pour cet abonnement à la session sur l’ordinateur local.
Utilisez ce paramètre lorsque vous vous inscrivez aux événements sur un ordinateur distant ou dans une session à distance.

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

### -MaxTriggerCount

Spécifie le nombre maximal de déclencheurs.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

Spécifie toutes les données supplémentaires à associer à cet abonnement aux événements. La valeur de ce paramètre apparaît dans la propriété **MessageData** de tous les événements associés à cet abonnement.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Espace de noms

Spécifie l'espace de noms de la classe WMI.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query

Spécifie une requête dans Langage de requêtes WMI (WQL) (WQL) qui identifie la classe d’événements WMI, par exemple : `select * from __InstanceDeletionEvent` .

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Spécifie un nom que vous sélectionnez pour l'abonnement. Le nom que vous sélectionnez doit être unique dans la session active. La valeur par défaut est le GUID affecté par Windows PowerShell.

La valeur de ce paramètre apparaît dans la valeur de la propriété **SourceIdentifier** de l'objet d'abonné et de tous les objets d'événements associés à cet abonnement.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Indique que cette applet de commande masque l’abonnement aux événements. Utilisez ce paramètre lorsque l'abonnement actuel fait partie d'un mécanisme d'inscription d'événement plus complexe et qu'il ne doit pas être découvert indépendamment.

Pour afficher ou annuler un abonnement qui a été créé à l’aide du paramètre **SupportEvent** , spécifiez le paramètre **force** des `Get-EventSubscriber` applets de commande et `Unregister-Event` .

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

### -Timeout

Spécifie la durée pendant laquelle Windows PowerShell attend la fin de cette commande.

La valeur par défaut, 0 (zéro), indique qu'aucun délai d'attente n'est défini et fait attendre Windows PowerShell indéfiniment.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: TimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

Pour utiliser cette applet de commande dans Windows Vista ou une version ultérieure du système d’exploitation Windows, démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.

Les événements, les abonnements aux événements et la file d'attente d'événements existent uniquement dans la session active. Si vous fermez cette session, la file d'attente d'événements est ignorée et l'abonnement aux événements est annulé.

## LIENS CONNEXES
