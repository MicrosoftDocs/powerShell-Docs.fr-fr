---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: c0eed3d571cfb243c3f0ba4d0a4b7ddfaf4f04fb
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205526"
---
# Disconnect-PSSession

## SYNOPSIS
Se déconnecte d'une session.

## SYNTAX

### Session (par défaut)

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Nom

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Disconnect-PSSession` applet de commande déconnecte une session PowerShell (« PSSession »), telle qu’une session démarrée à l’aide `New-PSSession` de l’applet de commande, à partir de la session active. Par conséquent, la session PSSession est dans un état déconnecté. Vous pouvez vous connecter à la session PSSession déconnectée à partir de la session active ou d'une autre session sur l'ordinateur local ou sur un autre ordinateur.

L' `Disconnect-PSSession` applet de commande déconnecte uniquement les sessions PSSession ouverts qui sont connectés à la session active. `Disconnect-PSSession` Impossible de déconnecter les sessions PSSession rompus ou fermés, ou le sessions PSSession interactif a démarré à l’aide de l’applet de commande `Enter-PSSession` et ne peut pas déconnecter les sessions PSSession qui sont connectés à d’autres sessions.

Pour vous reconnecter à une session PSSession déconnectée, utilisez les `Connect-PSSession` applets de commande ou `Receive-PSSession` .

Quand une session PSSession est déconnectée, les commandes de la session continuent à s'exécuter jusqu'à ce qu'elles se terminent, sauf si la session PSSession arrive à expiration ou que les commandes de la session PSSession sont bloquées par une mémoire tampon de sortie saturée. Pour modifier le délai d'inactivité, utilisez le paramètre **IdleTimeoutSec** . Pour modifier le mode de mise en mémoire tampon de sortie, utilisez le paramètre **OutputBufferingMode** . vous pouvez également utiliser le paramètre **InDisconnectedSession** de l' `Invoke-Command` applet de commande pour exécuter une commande dans une session déconnectée.

Pour plus d'informations sur la fonctionnalité Sessions déconnectées, consultez [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).

Cette applet de commande est introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : déconnecter une session par nom

Cette commande déconnecte la session PSSession UpdateSession sur l'ordinateur Server01 de la session active. La commande utilise le paramètre **Name** pour identifier la session PSSession.

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

La sortie indique que la tentative de déconnexion a réussi. L'état de session est Disconnected et la disponibilité est None, ce qui indique que la session n'est pas occupée et peut être reconnectée.

### Exemple 2 : déconnecter une session d’un ordinateur spécifique

Cette commande déconnecte la session PSSession ITTask sur l'ordinateur Server12 de la session active.
La session ITTask a été créée dans la session active et se connecte à l'ordinateur Server12. La commande utilise l' `Get-PSSession` applet de commande pour accéder à la session et `Disconnect-PSSession` à l’applet de commande pour la déconnecter.

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

La `Disconnect-PSSession` commande utilise le paramètre **OutputBufferingMode** pour définir le mode de sortie sur **Drop** . Ce paramètre garantit que le script qui s'exécute dans la session peut continuer de s'exécuter même si la mémoire tampon de la sortie de session est saturée. Comme le script écrit sa sortie dans un rapport sur un partage de fichiers, une autre sortie peut être perdue sans conséquence.

La commande utilise également le paramètre **IdleTimeoutSec** pour étendre le délai d'inactivité de la session à 24 heures. Ce paramètre laisse le temps à cet administrateur ou à d'autres administrateurs de se reconnecter à la session pour vérifier que le script s'est exécuté et résoudre les problèmes si nécessaire.

### Exemple 3 : utilisation de plusieurs sessions PSSession sur plusieurs ordinateurs

Cette série de commandes montre comment l' `Disconnect-PSSession` applet de commande peut être utilisée dans un scénario d’entreprise. Dans ce cas, un nouveau technicien démarre un script dans une session sur un ordinateur distant et rencontre un problème. Le technicien se déconnecte de la session afin qu'un responsable plus expérimenté puisse s'y connecter et résoudre le problème.

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

Le technicien commence par la création de sessions sur plusieurs ordinateurs distants et l'exécution d'un script dans chaque session. La première commande utilise l' `New-PSSession` applet de commande pour créer la session ITTask sur trois ordinateurs distants. La commande enregistre les sessions dans la variable $s. La deuxième commande utilise le paramètre **filePath** de l' `Invoke-Command` applet de commande pour exécuter un script dans les sessions de la variable $s.

Le script en cours d'exécution sur l'ordinateur Srv1 génère des erreurs inattendues. Le technicien contacte son responsable et lui demande de l'aide. Le responsable dirige le technicien à se déconnecter de la session pour qu’il puisse l’examiner. La deuxième commande utilise l' `Get-PSSession` applet de commande pour récupérer la session ITTask sur l’ordinateur Srv1 et l' `Disconnect-PSSession` applet de commande pour la déconnecter. Cette commande n’affecte pas les sessions ITTask sur les autres ordinateurs.

La troisième commande utilise l' `Get-PSSession` applet de commande pour récupérer les sessions ITTask. La sortie indique que les sessions ITTask sur les ordinateurs Srv2 et Srv30 n'ont pas été affectées par la commande de déconnexion.

Le gestionnaire ouvre une session sur son ordinateur privé, se connecte à son réseau d’entreprise, démarre PowerShell et utilise l' `Get-PSSession` applet de commande pour accéder à la session ITTask sur l’ordinateur Srv1. Il utilise les informations d'identification du technicien pour accéder à la session.

Ensuite, le gestionnaire utilise l' `Connect-PSSession` applet de commande pour se connecter à la session ITTask sur l’ordinateur Srv1. La commande enregistre la session dans la variable $s.

Le gestionnaire utilise l' `Invoke-Command` applet de commande pour exécuter des commandes de diagnostic dans la session dans la `$s` variable. Il réalise que le script a échoué, car il n'a pas trouvé de répertoire requis.
Le gestionnaire utilise la `MkDir` fonction pour créer le répertoire, puis il redémarre le `Get-PatchStatus.ps1` script et se déconnecte de la session. Le responsable signale ses conclusions au technicien, suggère qu’il se reconnecte à la session pour effectuer les tâches et lui demande d’ajouter une commande au `Get-PatchStatus.ps1` script qui crée le répertoire requis s’il n’existe pas.

### Exemple 4-modifier la valeur du délai d’attente pour une session PSSession

Cet exemple montre comment corriger la valeur de la propriété **IdleTimeout** d'une session pour pouvoir la déconnecter.

La propriété du délai d'inactivité d'une session est essentielle pour les sessions déconnectées, car elle détermine la durée pendant laquelle une session déconnectée est conservée avant sa suppression. Vous pouvez définir l'option de délai d'inactivité quand vous créez une session et quand vous la déconnectez. Les valeurs par défaut pour le délai d’inactivité d’une session sont définies dans la `$PSSessionOption` variable de préférence sur l’ordinateur local et dans la configuration de session sur l’ordinateur distant. Les valeurs définies pour la session sont prioritaires sur les valeurs définies dans la configuration de session, mais les valeurs de session ne peuvent pas dépasser les quotas définis dans la configuration de la session, tels que la valeur **MaxIdleTimeoutMs** .

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
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
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

La première commande utilise l' `New-PSSessionOption` applet de commande pour créer un objet d’option de session. Elle utilise le paramètre **IdleTimeout** pour définir un délai d'inactivité de 48 heures (172800000 millisecondes). La commande enregistre l'objet d'options de session dans la variable $Timeout.

La deuxième commande utilise l' `New-PSSession` applet de commande pour créer la session ITTask sur l’ordinateur SERVEUR01. La commande enregistre la session dans la variable $s. La valeur du paramètre **SessionOption** est le délai d'inactivité de 48 heures dans la variable $Timeout.

La troisième commande déconnecte la session ITTask dans la variable $s. La commande échoue, car la valeur de délai d'inactivité de la session dépasse le quota **MaxIdleTimeoutMs** dans la configuration de session. Comme le délai d'inactivité n'est pas utilisé tant que la session n'est pas déconnectée, cette violation peut passer inaperçue pendant que la session est en cours d'utilisation.

La quatrième commande utilise l' `Invoke-Command` applet de commande pour exécuter une `Get-PSSessionConfiguration` commande pour la configuration de session Microsoft. PowerShell sur l’ordinateur SERVEUR01. La commande utilise l' `Format-List` applet de commande pour afficher toutes les propriétés de la configuration de session dans une liste. La sortie indique que la propriété **MaxIdleTimeoutMS** , qui établit la valeur **IdleTimeout** maximale autorisée pour les sessions qui utilisent la configuration de session, est de 43,2 millions millisecondes (12 heures).

La cinquième commande obtient les valeurs d'option de la session dans la variable $s. Les valeurs de nombreuses options de session sont des propriétés de la propriété **ConnectionInfo** de la propriété d' **instance d’exécution** de la session. La sortie indique que la valeur de la propriété **IdleTimeout** de la session est 172,8 millions millisecondes (48 heures), ce qui viole le quota **MaxIdleTimeoutMs** de 12 heures dans la configuration de session. Pour résoudre ce conflit, vous pouvez utiliser le paramètre **ConfigurationName** pour sélectionner une autre configuration de session ou utiliser le paramètre **IdleTimeout** pour réduire le délai d’inactivité de la session.

La sixième commande déconnecte la session. Elle utilise le paramètre **IdleTimeoutSec** pour affecter au délai d'inactivité la valeur maximale de 12 heures.

La septième commande obtient la valeur de la propriété **IdleTimeout** de la session déconnectée, qui est mesurée en millisecondes. La sortie confirme que la commande a réussi.

## PARAMETERS

### -Id

Se déconnecte de sessions avec l'ID de session spécifié. Tapez un ou plusieurs ID (séparés par des virgules) ou utilisez l'opérateur de plage (..) pour spécifier une plage d'ID.

Pour obtenir l’ID d’une session, utilisez l' `Get-PSSession` applet de commande. L'ID d'instance est stocké dans la propriété **ID** de la session.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IdleTimeoutSec

Modifie la valeur de délai d'inactivité de la session PSSession déconnectée. Entrez une valeur en secondes. La valeur minimale est 60 (1 minute).

Le délai d'inactivité détermine la durée pendant laquelle la session PSSession déconnectée est conservée sur l'ordinateur distant. Quand le délai expire, la session PSSession est supprimée.

Les sessions PSSession déconnectées sont considérées comme inactives dès qu'elles sont déconnectées, même si elles comprennent des commandes en cours d'exécution.

La valeur par défaut pour le délai d'inactivité d'une session est définie par la valeur de la propriété **IdleTimeoutMs** de la configuration de session. La valeur par défaut est égale à 7 200 000 millisecondes (2 heures).

La valeur de ce paramètre est prioritaire sur la valeur de la propriété **IdleTimeout** de la variable de préférence $PSSessionOption et la valeur de délai d'inactivité par défaut dans la configuration de session. Toutefois, cette valeur ne peut pas dépasser la valeur de la propriété **MaxIdleTimeoutMs** de la configuration de session. La valeur par défaut de **MaxIdleTimeoutMs** est 12 heures (43200000 millisecondes).

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

### -InstanceId

Se déconnecte de sessions avec les ID d'instance spécifiés.

L'ID d'instance est un GUID qui identifie une session sur un ordinateur local ou distant. L'ID d'instance est unique, même entre plusieurs sessions sur plusieurs ordinateurs.

Pour obtenir l’ID d’instance d’une session, utilisez l’applet de commande `Get-PSSession` . L’ID d’instance est stocké dans la propriété **InstanceID** de la session.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Se déconnecte de sessions avec les noms conviviaux spécifiés. Les caractères génériques sont autorisés.

Pour obtenir le nom convivial d’une session, utilisez l' `Get-PSSession` applet de commande. Le nom convivial est stocké dans la propriété **Name** de la session.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Session

Se déconnecte de sessions PSSession spécifiées. Entrez les objets PSSession, tels que ceux que l’applet de commande `New-PSSession` retourne. Vous pouvez également diriger un objet PSSession vers `Disconnect-PSSession` .

L' `Get-PSSession` applet de commande peut obtenir toutes les sessions PSSession qui se terminent sur un ordinateur distant, y compris les sessions PSSession qui sont déconnectés et les sessions PSSession qui sont connectés à d’autres sessions sur d’autres ordinateurs. `Disconnect-PSSession` déconnecte uniquement PSSession qui sont connectés à la session active. Si vous dirigez d’autres sessions PSSession vers `Disconnect-PSSession` , la `Disconnect-PSSession` commande échoue.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ThrottleLimit

Définit la limite de limitation pour la `Disconnect-PSSession` commande.

Le seuil de limitation correspond au nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande. Si vous omettez ce paramètre ou entrez la valeur 0, la valeur par défaut 32 est utilisée.

La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

Détermine comment la sortie de la commande est gérée dans la session déconnectée quand la mémoire tampon de la sortie est saturée. La valeur par défaut est **Block** .

Si la commande de la session déconnectée retourne une sortie et que la mémoire tampon de la sortie se remplit, la valeur de ce paramètre détermine en réalité si la commande continue de s'exécuter pendant que la session est déconnectée. La valeur **Block** suspend la commande jusqu'à ce que la session soit rouverte. La valeur **Drop** permet l'exécution de la commande, même si des données peuvent être perdues. Quand vous utilisez la valeur **Drop** , redirigez la sortie de la commande vers un fichier sur disque.

Les valeurs autorisées sont :

- **Bloquer** : lorsque la mémoire tampon de sortie est pleine, l’exécution est suspendue jusqu’à ce que la mémoire tampon soit désactivée.
- **Drop** : lorsque la mémoire tampon de sortie est pleine, l’exécution se poursuit. Quand une nouvelle sortie est enregistrée, la sortie la plus ancienne est supprimée.
- **Aucun** : aucun mode de mise en mémoire tampon de sortie n’est spécifié. La valeur de la propriété **OutputBufferingMode** de la configuration de session est utilisée pour la session déconnectée.

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](./About/about_CommonParameters.md).

## ENTRÉES

### System. Management. Automation. instances d’exécution. PSSession

Vous pouvez diriger une session vers `Disconnect-PSSession` .

## SORTIES

### System. Management. Automation. instances d’exécution. PSSession

`Disconnect-PSSession` retourne un objet qui représente la session déconnectée.

## REMARQUES

- L' `Disconnect-PSSession` applet de commande fonctionne uniquement lorsque les ordinateurs locaux et distants exécutent PowerShell 3,0 ou une version ultérieure.
- Si vous utilisez l' `Disconnect-PSSession` applet de commande sur une session déconnectée, la commande n’a aucun effet sur la session et elle ne génère pas d’erreurs.
- Les sessions de bouclage déconnectées ayant des jetons de sécurité interactifs (ceux créés avec le paramètre **EnableNetworkAccess** ) peuvent être reconnectées uniquement à partir de l'ordinateur sur lequel la session a été créée. Cette restriction protège l'ordinateur contre tout accès malveillant.
- Quand vous déconnectez une session PSSession, l'état de session est **Disconnected** et la disponibilité est **None** .

  La valeur de la propriété **State** dépend de la session active. Par conséquent, la valeur **Disconnected** signifie que la session PSSession n'est pas connectée à la session active. Toutefois, cela ne signifie pas que la session PSSession est déconnectée de toutes les sessions. Elle peut être connectée à une autre session. Pour déterminer si vous pouvez vous connecter ou vous reconnecter à la session, utilisez la propriété **Availability** .

  Une propriété **Availability** avec la valeur **None** signifie que vous pouvez vous connecter à la session. La valeur **Busy** indique que vous ne pouvez pas vous connecter à la session PSSession, car elle est connectée à une autre session.

  Pour plus d’informations sur les valeurs de la propriété **State** des sessions, consultez [énumération RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).

  Pour plus d’informations sur les valeurs de la propriété **Availability** des sessions, consultez [énumération RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).

## LIENS CONNEXES

[Connect-PSSession](Connect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Receive-PSSession](Receive-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

[about_Remote_Disconnected_Sessions](About/about_Remote_Disconnected_Sessions.md)
