---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: 9257c0a1829cc9cc85029f7c6fdc8e61b0ed7e56
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205370"
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

```
PS C:\> New-PSTransportOption
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

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable. The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.
PS C:\> $t = New-PSTransportOption -MaxSessions 40

The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Register-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list. The output shows that the value of the **MaxShells** property of the session configuration is 40.
PS C:\> Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
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

Cet exemple montre comment utiliser un objet d’options de transport pour définir des options de configuration de session.

### Exemple 3 : définition d’une option de transport

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport option object. The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds). The command saves the transport objects object in the $t variable.
PS C:\> $t = New-PSTransportOption -IdleTimeoutSec 3600

The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Set-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer. The command uses the **ConfigurationName** property to specify the ITTasks session configuration. The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session. If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.
PS C:\> $s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks

The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list. The output shows that the session has an idle time-out of one hour (360,000 milliseconds).
PS C:\> $s | Format-List -Property *
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

Cette commande montre l'effet de la définition d'une option de transport dans une configuration de session sur les sessions qui utilisent la configuration de session.

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
