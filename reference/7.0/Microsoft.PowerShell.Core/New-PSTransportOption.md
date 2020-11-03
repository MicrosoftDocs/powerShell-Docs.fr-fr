---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: b8493931e6390dfb6a3c4becb5a9f51d79df0574
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205533"
---
# New-PSTransportOption

## SYNOPSIS
Crée un objet qui contient des options avancées pour une configuration de session.

## SYNTAX

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## Description

L'applet de commande **New-PSTransportOption** crée un objet qui contient des options de transport pour les configurations de sessions.
Vous pouvez utiliser l’objet comme valeur du paramètre *TransportOption* des applets de commande qui créent ou modifient une configuration de session, comme les applets de commande Register-PSSessionConfiguration et Set-PSSessionConfiguration.

Vous pouvez également modifier les paramètres d'option de transport en modifiant les valeurs des propriétés de configuration de session dans le lecteur WSMan:.
Pour plus d’informations, consultez fournisseur WSMan.

Les options de configuration de session représentent les valeurs de session définies côté serveur ou la fin de la réception d’une connexion à distance.
L’extrémité côté client ou d’envoi de la connexion peut définir des valeurs d’option de session lors de la création de la session, ou lorsque le client se déconnecte de la session ou se reconnecte.
Sauf indication contraire, en cas de conflit des valeurs des paramètres, les valeurs côté client sont prioritaires.
Toutefois, les valeurs côté client ne peuvent pas dépasser les valeurs maximales et les quotas définis dans la configuration de session.

Sans paramètres, **New-PSTransportOption** génère un objet d’option de transport qui a des valeurs NULL pour toutes les options.
Si vous omettez un paramètre, l'objet a une valeur null pour la propriété représentée par le paramètre.
Une valeur NULL n’affecte pas la configuration de session.

Pour plus d’informations sur les options de session, consultez New-PSSessionOption.
Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : générer une option de transport par défaut

```powershell
New-PSTransportOption
```

```Output
ProcessIdleTimeoutSec           :
MaxIdleTimeoutSec               :
MaxSessions                     :
MaxConcurrentCommandsPerSession :
MaxSessionsPerUser              :
MaxMemoryPerSessionMB           :
MaxProcessesPerSession          :
MaxConcurrentUsers              :
IdleTimeoutSec                  :
OutputBufferingMode             :
```

Cette commande exécute la commande **New-PSTransportOption** sans paramètres.
La sortie indique que l’applet de commande génère un objet d’option de transport qui a des valeurs NULL pour toutes les propriétés.

### Exemple 2 : accéder aux options de configuration de session

Cet exemple montre comment utiliser un objet d’options de transport pour définir des options de configuration de session.

```powershell
$t = New-PSTransportOption -MaxSessions 40
Register-PSSessionConfiguration -Name ITTasks -TransportOption $t
Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITTasks
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 40
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 2
Name                          : ITTasks
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
Enabled                       : True
MaxShellsPerUser              : 25
Permission                    :
```

La première commande utilise l'applet de commande **New-PSTransportOption** pour créer un objet d'options de transport, qu'elle enregistre dans la variable $t. La commande utilise le paramètre *MaxSessions* pour augmenter le nombre maximal de sessions à 40.

La deuxième commande utilise l'applet de commande **Register-PSSessionConfiguration** pour créer la configuration de session ITTasks. La commande utilise le paramètre *TransportOption* pour spécifier l'objet d'options de transport dans la variable $t.

La troisième commande utilise l’applet de commande Get-PSSessionConfiguration pour obtenir les configurations de session ITTasks et l’applet de commande Format-List pour afficher toutes les propriétés de l’objet de configuration de session dans une liste. La sortie indique que la valeur de la propriété **MaxShells** de la configuration de session est 40.

### Exemple 3 : définition d’une option de transport

Cette commande montre l'effet de la définition d'une option de transport dans une configuration de session sur les sessions qui utilisent la configuration de session.

```powershell
$t = New-PSTransportOption -IdleTimeoutSec 3600
Set-PSSessionConfiguration -Name ITTasks -TransportOption $t
$s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks
$s | Format-List -Property *
```

```Output
State                  : Opened
IdleTimeout            : 3600000
OutputBufferingMode    : Block
ComputerName           : localhost
ConfigurationName      : ITTasks
InstanceId             : 4110c3f5-68ea-40fa-9bbf-04a433dbb02d
Id                     : 1
Name                   : MyITTasks
Availability           : Available
ApplicationPrivateData : {PSVersionTable}
Runspace               : System.Management.Automation.RemoteRunspace
```

La première commande utilise l'applet de commande **New-PSTransportOption** pour créer un objet d'options de transport. La commande utilise le paramètre *IdleTimeoutSec* pour affecter une heure (3 600 secondes) à la valeur de propriété **IdleTimeoutSec** de l'objet. La commande enregistre l'objet d'options de transport dans la variable $t.

La deuxième commande utilise l’applet de commande Set-PSSessionConfiguration pour modifier les options de transport de la configuration de session ITTasks. La commande utilise le paramètre *TransportOption* pour spécifier l'objet d'options de transport dans la variable $t.

La troisième commande utilise l’applet de commande New-PSSession pour créer la session MyITTasks sur l’ordinateur local. La commande utilise la propriété **ConfigurationName** pour spécifier la configuration de session ITTasks. La commande enregistre la session dans la variable $s. Notez que la commande n’utilise pas le paramètre *SessionOption* de **New-PSSession** pour définir un délai d’inactivité personnalisé pour la session. Si c’est le cas, la valeur du délai d’inactivité définie dans l’option de session est prioritaire sur le délai d’inactivité défini dans la configuration de session.

La quatrième commande utilise l’applet de commande Format-List pour afficher toutes les propriétés de la session dans la variable $s dans une liste. La sortie indique que la session a un délai d’inactivité d’une heure (360 000 millisecondes).

## PARAMETERS

### -IdleTimeoutSec

Détermine la durée pendant laquelle chaque session reste ouverte si l’ordinateur distant ne reçoit pas de communication de l’ordinateur local.
Cela comprend le signal de pulsation.
Quand le délai expire, la session se ferme.

La valeur du délai d’inactivité revêt une importance particulière lorsque l’utilisateur a l’intention de se déconnecter et de se reconnecter à une session.
L'utilisateur ne peut se reconnecter que si la session n'a pas expiré.

Le paramètre *IdleTimeoutSec* correspond à la propriété **IdleTimeoutMs** d'une configuration de session.

Entrez une valeur en secondes.
La valeur par défaut est 7 200 (2 heures).
La valeur minimale est 60 (1 minute).
La valeur maximale est la valeur de la propriété **IdleTimeout** des objets Shell dans la configuration WSMan ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` ).
La valeur par défaut est égale à 7 200 000 millisecondes (2 heures).

Si une valeur de délai d’inactivité est définie dans les options de session et dans la configuration de session, la valeur définie dans les options de session est prioritaire, mais elle ne peut pas dépasser la valeur de la propriété **MaxIdleTimeoutMs** de la configuration de session.
Pour définir la valeur de la propriété **MaxIdleTimeoutMs** , utilisez le paramètre *MaxIdleTimeoutSec* .

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxConcurrentCommandsPerSession

Limite le nombre de commandes qui peuvent s’exécuter simultanément dans chaque session à la valeur spécifiée.
La valeur par défaut est 1000.

Le paramètre *MaxConcurrentCommandsPerSession* correspond à la propriété **MaxConcurrentCommandsPerShell** d’une configuration de session.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxConcurrentUsers

Limite le nombre d’utilisateurs qui peuvent exécuter des commandes simultanément dans chaque session à la valeur spécifiée.
La valeur par défaut est 5.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxIdleTimeoutSec

Limite le délai d’inactivité défini pour chaque session à la valeur spécifiée.
La valeur par défaut est \[ int \] :: MaxValue (~ 25 jours).

La valeur du délai d’inactivité revêt une importance particulière lorsque l’utilisateur a l’intention de se déconnecter et de se reconnecter à une session.
L'utilisateur ne peut se reconnecter que si la session n'a pas expiré.

Le paramètre *MaxIdleTimeoutSec* correspond à la propriété **MaxIdleTimeoutMs** d’une configuration de session.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxMemoryPerSessionMB

Limite la mémoire utilisée par chaque session à la valeur spécifiée.
Entrez une valeur en mégaoctets.
La valeur par défaut est 1 024 mégaoctets (1 Go).

Le paramètre *MaxMemoryPerSessionMB* correspond à la propriété **MaxMemoryPerShellMB** d’une configuration de session.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxProcessesPerSession

Limite le nombre de processus exécutés dans chaque session à la valeur spécifiée.
La valeur par défaut est 15.

Le paramètre *MaxProcessesPerSession* correspond à la propriété **MaxProcessesPerShell** d’une configuration de session.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxSessions

Limite le nombre de sessions qui utilisent la configuration de session.
La valeur par défaut est 25.

Le paramètre *maxsessions* correspond à la propriété **MaxShells** d’une configuration de session.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxSessionsPerUser

Limite le nombre de sessions qui utilisent la configuration de session et s'exécutent avec les informations d'identification d'un utilisateur donné à la valeur spécifiée.
La valeur par défaut est 25.

Lorsque vous spécifiez cette valeur, pensez que de nombreux utilisateurs peuvent utiliser les informations d’identification d’un utilisateur exécuter en tant qu’utilisateur.

Le paramètre *MaxSessionsPerUser* correspond à la propriété **MaxShellsPerUser** d’une configuration de session.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OutputBufferingMode

Détermine comment la sortie de la commande est gérée dans des sessions déconnectées quand la mémoire tampon de sortie est pleine.
Les valeurs valides pour ce paramètre sont :

- Bloquer.
Quand la mémoire tampon de sortie est pleine, l'exécution est suspendue jusqu'à ce que la mémoire tampon soit effacée.
- Drop.
Quand la mémoire tampon de sortie est pleine, l'exécution se poursuit.
Quand une nouvelle sortie est enregistrée, la sortie la plus ancienne est supprimée.
- Aucun.
Aucun mode de mise en mémoire tampon de sortie n'est spécifié.

La valeur par défaut de la propriété **OutputBufferingMode** des sessions est Block.

```yaml
Type: System.Nullable`1[System.Management.Automation.Runspaces.OutputBufferingMode]
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProcessIdleTimeoutSec

Limite le délai d’attente pour chaque processus hôte à la valeur spécifiée.
La valeur par défaut, 0, signifie qu’il n’y a aucune valeur de délai d’attente pour le processus.

D’autres configurations de sessions ont des valeurs de délai d’attente par processus.
Par exemple, la configuration de session **Microsoft. PowerShell. Workflow** a une valeur de délai d’attente par processus de 28800 secondes (8 heures).

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. Commands. WSManConfigurationOption

## REMARQUES

- Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options. En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.

## LIENS CONNEXES

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)
