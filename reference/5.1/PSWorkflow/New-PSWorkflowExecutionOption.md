---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSWorkflow
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowexecutionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowExecutionOption
ms.openlocfilehash: db5d19396f555a41ad14552823c57f3b11c79321
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205430"
---
# New-PSWorkflowExecutionOption

## SYNOPSIS

Crée un objet qui contient les options de configuration de session pour les sessions de workflow.

## SYNTAX

```
New-PSWorkflowExecutionOption [-PersistencePath <String>] [-MaxPersistenceStoreSizeGB <Int64>]
 [-PersistWithEncryption] [-MaxRunningWorkflows <Int32>] [-AllowedActivity <String[]>]
 [-OutOfProcessActivity <String[]>] [-EnableValidation] [-MaxDisconnectedSessions <Int32>]
 [-MaxConnectedSessions <Int32>] [-MaxSessionsPerWorkflow <Int32>] [-MaxSessionsPerRemoteNode <Int32>]
 [-MaxActivityProcesses <Int32>] [-ActivityProcessIdleTimeoutSec <Int32>]
 [-RemoteNodeSessionIdleTimeoutSec <Int32>] [-SessionThrottleLimit <Int32>]
 [-WorkflowShutdownTimeoutMSec <Int32>] [<CommonParameters>]
```

## Description

L' `New-PSWorkflowExecutionOption` applet de commande crée un objet qui contient des options avancées pour les configurations de session de workflow, c’est-à-dire des configurations de session conçues pour exécuter des flux de travail Windows PowerShell Workflow.

Vous pouvez utiliser l’objet **PSWorkflowExecutionOption** qui `New-PSWorkflowExecutionOption` génère comme valeur du paramètre **SessionTypeOption** des applets de commande qui créent ou modifient une configuration de session, comme `Register-PSSessionConfiguration` les `Set-PSSessionConfiguration` applets de commande et.

Chaque paramètre de l' `New-PSWorkflowExecutionOption` applet de commande représente une propriété de l’objet d’option de configuration de session de workflow que l’applet de commande retourne. Si vous omettez un paramètre, l'applet de commande crée l'objet avec une valeur par défaut pour la propriété.

L' `New-PSWorkflowExecutionOption` applet de commande fait partie de la fonctionnalité de flux de travail Windows PowerShell.

Vous pouvez également ajouter des paramètres communs de workflow à cette commande. Pour plus d’informations sur les paramètres communs de workflow, consultez [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md).

Cette applet de commande est introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : créer un objet d’options de workflow

```powershell
New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
```

```Output
SessionThrottleLimit                       : 100
PersistencePath                            : C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell\WF\PS
MaxPersistenceStoreSizeGB                  : 10
PersistWithEncryption                      : False
MaxRunningWorkflows                        : 30
AllowedActivity                            : {PSDefaultActivities}
OutOfProcessActivity                       : {InlineScript}
EnableValidation                           : True
MaxDisconnectedSessions                    : 200
MaxConnectedSessions                       : 100
MaxSessionsPerWorkflow                     : 10
MaxSessionsPerRemoteNode                   : 5
MaxActivityProcesses                       : 5
ActivityProcessIdleTimeoutSec              : 60
RemoteNodeSessionIdleTimeoutSec            : 60
WorkflowShutdownTimeoutMSec                : 500
```

Cette commande utilise la `New-PSWorkflowExecutionOption` cmdlet pour augmenter la valeur de **MaxSessionsPerWorkflow** à 10 et réduire la valeur de **MaxDisconnectedSessions** à 200.

La sortie illustre l'objet retourné par l'applet de commande.

### Exemple 2 : utilisation d’un objet d’options de workflow

```powershell
# Create a Workflow Options object and save it in a variable
$wo = New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
# Create the ITWorkflow session configuration
Register-PSSessionConfiguration -Name ITWorkflows -SessionTypeOption $wo -Force
```

```Output
    WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=ITWorkflows}                  ITWorkflows
```

```powershell
Get-PSSessionConfiguration ITWorkflows | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITWorkflows
MaxConcurrentCommandsPerShell : 1000
allowedactivity               : PSDefaultActivities
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
maxsessionsperworkflow        : 10
lang                          : en-US
sessionconfigurationdata      : <SessionConfigurationData>
                                    <Param Name='PrivateData'>
                                        <PrivateData>
                                            <ParamName='enablevalidation' Value='True'/>
                                            <Param Name='allowedactivity'Value='PSDefaultActivities' />
                                            <Param Name='outofprocessactivity' Value='InlineScript'/>
                                            <Param Name='maxdisconnectedsessions' Value='200' />
                                            <ParamName='maxsessionsperworkflow' Value='10'/>
                                        </PrivateData>
                                    </Param>
                                </SessionConfigurationData>
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 25
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
outofprocessactivity          : InlineScript
SDKVersion                    : 2
Name                          : ITWorkflows
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
enablevalidation              : True
Enabled                       : True
maxdisconnectedsessions       : 200
MaxShellsPerUser              : 25
Permission                    :
```

Les deux premières commandes créent un nouvel objet de configuration de session et l’inscrivent.

La troisième commande utilise l' `Get-PSSessionConfiguration` applet de commande pour obtenir la configuration de session ITWorkflows et le `Format-List` pour afficher toutes les propriétés de la configuration de session dans une liste. La sortie montre les options de flux de travail dans la configuration de session. Plus précisément, la configuration de session a une propriété **MaxSessionsPerWorkflow** avec la valeur 10 et une propriété **MaxDisconnectedSessions** avec la valeur 200.

## PARAMETERS

### -ActivityProcessIdleTimeoutSec

Détermine la durée pendant laquelle chaque processus hôte d'activité est maintenu une fois que le processus est devenu inactif. Quand le délai expire, le processus se ferme.

Entrez une valeur en secondes. La valeur par défaut est 60.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowedActivity

Spécifie les activités autorisées à s'exécuter dans la session.

Entrez les noms d’activité qualifiés par un espace de noms, tels que `Microsoft.Powershell.HyperV.Activities.*` .
Les caractères génériques sont pris en charge. La valeur par défaut, **PSDefaultActivities** , inclut les activités Windows Workflow Foundation intégrées et les activités qui représentent les applets de commande Windows PowerShell principales.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: PSDefaultActivities
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableValidation

Vérifie que toutes les activités de workflow dans la session sont incluses dans la liste des activités autorisées.

La valeur par défaut est True. Pour désactiver la validation, utilisez le format de commande suivant : `-EnableValidation:$false` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxActivityProcesses

Spécifie le nombre maximal de processus qui peuvent être créés dans la session pour prendre en charge des activités de workflow. La valeur par défaut est 5.

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

### -MaxConnectedSessions

Spécifie le nombre maximal de sessions à distance qui sont dans un état opérationnel. Ce quota est appliqué aux sessions connectées à tous les nœuds distants (ordinateurs cibles). La valeur par défaut est 100.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxDisconnectedSessions

Spécifie le nombre maximal de sessions à distance qui sont dans un état déconnecté. Ce quota est appliqué aux sessions connectées à tous les nœuds distants (ordinateurs cibles). La valeur par défaut est 1000.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1000
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxPersistenceStoreSizeGB

Spécifie la taille maximale, en gigaoctets, du magasin de persistance alloué aux workflows exécutés dans la session. Quand la taille est dépassée, le magasin de persistance est développé pour enregistrer toutes les données persistantes, mais un avertissement s'affiche et un message est écrit dans le journal des événements du workflow. La valeur par défaut est 10.

Le magasin de persistance contient des données pour toutes les tâches de workflow. La possibilité de stocker des données permet la reprise des tâches sans perte d'état.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxRunningWorkflows

Spécifie le nombre maximal de workflows qui peuvent s'exécuter simultanément dans la session.
La valeur par défaut est 30.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 30
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxSessionsPerRemoteNode

Spécifie le nombre maximal de sessions qui peuvent être connectées à chaque nœud distant (ordinateur cible). La valeur par défaut est 5.

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

### -MaxSessionsPerWorkflow

Spécifie le nombre maximal de sessions qui peuvent être créées pour prendre en charge chaque workflow. La valeur par défaut est 5.

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

### -OutOfProcessActivity

Détermine les activités autorisées (spécifiées par le paramètre **AllowedActivities** ) qui sont exécutées hors processus. La valeur par défaut est **InlineScript** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineScript
Accept pipeline input: False
Accept wildcard characters: False
```

### -PersistencePath

Spécifie l'emplacement sur le disque où sont stockés l'état et les données de workflow. Le stockage de l'état et des données de workflow permet la suspension et la reprise des workflows, et une récupération suite à des interruptions et des défaillances du réseau.

La valeur par défaut est `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PersistWithEncryption

Indique que le flux de travail chiffre les données dans le magasin de persistance. Envisagez d'utiliser cette fonctionnalité lors du stockage de données de persistance dans un partage réseau.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteNodeSessionIdleTimeoutSec

Spécifie la durée pendant laquelle une session qui est connectée à un nœud distant (ordinateur cible) est maintenue si elle est inactive.

Entrez une valeur en secondes. La valeur par défaut est 60.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionThrottleLimit

Spécifie le nombre d'opérations créées pour prendre en charge tous les workflows démarrés dans la session. La valeur par défaut est 100.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkflowShutdownTimeoutMSec

Spécifie la durée pendant laquelle la session est maintenue une fois que tous les workflows dans la session sont suspendus de force. Quand le délai arrive à expiration, Windows PowerShell ferme la session, même si tous les workflows ne sont pas encore suspendus.

Entrez une valeur en millisecondes.
La valeur par défaut est 500.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 500
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. Commands. PSWorkflowExecutionOption

## REMARQUES

Quand la valeur maximale définie par une option est dépassée, la commande pour créer une autre instance dans la session échoue, sauf indication dans la description du paramètre. Par exemple, si la valeur de **MaxConnectedSessions** est 100, la commande pour créer la 101è session sur un nœud distant (ordinateur cible) échoue.

Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options. En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.

En particulier, les propriétés des configurations de sessions qui comprennent un objet **PSWorkflowExecutionOptions** varient en fonction des valeurs d'option de workflow. Par exemple, si la configuration de session inclut un objet **PSWorkflowExecutionOptions** qui définit une valeur autre que par défaut pour la propriété **SessionThrottleLimit** , la configuration de session a une propriété **SessionThrottleLimit** . Sinon, elle ne l'a pas.

## LIENS CONNEXES

[New-PSWorkflowSession](New-PSWorkflowSession.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)
