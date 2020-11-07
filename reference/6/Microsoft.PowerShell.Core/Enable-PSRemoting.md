---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 6dd0b6a997551aba0df2da666eb21dddeb2e1fcf
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344080"
---
# Enable-PSRemoting

## SYNOPSIS
Configure l'ordinateur pour recevoir des commandes à distance.

## SYNTAXE

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Enable-PSRemoting` applet de commande configure l’ordinateur pour qu’il reçoive les commandes PowerShell à distance qui sont envoyées à l’aide de la technologie WS-Management. La communication à distance PowerShell basée sur WS-Management n’est actuellement prise en charge que sur la plateforme Windows.

La communication à distance PowerShell est activée par défaut sur les plateformes Windows Server. Vous pouvez utiliser `Enable-PSRemoting` pour activer la communication à distance PowerShell sur d’autres versions de Windows prises en charge et pour réactiver la communication à distance si elle est désactivée.

Vous ne devez exécuter cette commande qu’une seule fois sur chaque ordinateur qui recevra des commandes. Vous n’avez pas besoin de l’exécuter sur les ordinateurs qui envoient uniquement des commandes. Étant donné que la configuration démarre les écouteurs pour accepter les connexions à distance, il est prudent de l’exécuter uniquement lorsque cela est nécessaire.

L’activation de la communication à distance PowerShell sur les versions client de Windows lorsque l’ordinateur se trouve sur un réseau public est normalement interdite, mais vous pouvez ignorer cette restriction à l’aide du paramètre **SkipNetworkProfileCheck** . Pour plus d'informations, consultez la description du paramètre **SkipNetworkProfileCheck**.

Plusieurs installations PowerShell peuvent coexister côte à côte sur un seul ordinateur. L’exécution `Enable-PSRemoting` configure un point de terminaison de communication à distance pour la version d’installation spécifique dans laquelle vous exécutez l’applet de commande. Par conséquent, si vous exécutez `Enable-PSRemoting` en exécutant powershell 6,2, un point de terminaison de communication à distance sera configuré pour exécuter powershell 6,2. Si vous exécutez `Enable-PSRemoting` en exécutant PowerShell 7-Preview, un point de terminaison de communication à distance sera configuré pour exécuter PowerShell 7-preview.

`Enable-PSRemoting` crée deux configurations de point de terminaison de communication à distance si nécessaire. Si les configurations de point de terminaison existent déjà, elles sont simplement vérifiées pour être activées. Les configurations créées sont identiques, mais ont des noms différents. Un nom simple correspondant à la version PowerShell qui héberge la session est utilisé. L’autre nom de configuration contient des informations plus détaillées sur la version de PowerShell qui héberge la session. Par exemple, lors `Enable-PSRemoting` de l’exécution dans powershell 6,2, vous obtiendrez deux points de terminaison configurés nommés **PowerShell. 6** , **PowerShell. 6.2.2**.
Cela vous permet de créer une connexion à la dernière version de l’hôte PowerShell 6 en utilisant le nom simple **PowerShell. 6**. Vous pouvez ou vous connecter à une version spécifique de l’hôte PowerShell en utilisant le nom plus long **PowerShell. 6.2.2**.

Pour utiliser les points de terminaison de communication à distance récemment activés, vous devez les spécifier par leur nom avec le paramètre **ConfigurationName** lors de la création d’une connexion à distance à l’aide des `Invoke-Command` applets de commande, `New-PSSession` , `Enter-PSSession` . Pour plus d’informations, consultez l’exemple 4.

L' `Enable-PSRemoting` applet de commande effectue les opérations suivantes :

- Exécute l’applet de commande [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) , qui effectue les tâches suivantes :
  - Démarre le service WinRM.
  - Définit le type de démarrage du service WinRM sur automatique.
  - Crée un écouteur pour accepter les demandes sur n’importe quelle adresse IP.
  - Active une exception de pare-feu pour les communications WS-Management.
  - Crée les configurations de point de terminaison de session de nom simple et long, si nécessaire.
  - Active toutes les configurations de session.
  - Modifie le descripteur de sécurité de toutes les configurations de session pour autoriser l’accès à distance.
- Redémarre le service WinRM pour que les modifications précédentes soient effectives.

Pour exécuter cette applet de commande sur la plateforme Windows, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur. Cette applet de commande n’est pas disponible dans les versions Linux ou MacOS de PowerShell.

> [!CAUTION]
> Cette applet de commande n’affecte pas les configurations de point de terminaison distant créées par Windows PowerShell.
> Il affecte uniquement les points de terminaison créés avec PowerShell version 6 et ultérieures. Pour activer et désactiver les points de terminaison de communication à distance PowerShell qui sont hébergés par Windows PowerShell, exécutez l' `Enable-PSRemoting` applet de commande à partir d’une session Windows PowerShell.

## EXEMPLES

### Exemple 1 : configurer un ordinateur pour recevoir des commandes à distance

Cette commande configure l'ordinateur pour qu'il reçoive les commandes à distance.

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### Exemple 2 : configurer un ordinateur pour qu’il reçoive des commandes distantes sans invite de confirmation

Cette commande configure l'ordinateur pour qu'il reçoive les commandes à distance.
Le paramètre **force** supprime les invites utilisateur.

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### Exemple 3 : autoriser l’accès à distance sur les clients

Cet exemple montre comment autoriser l’accès à distance à partir de réseaux publics sur des versions clientes du système d’exploitation Windows. Le nom de la règle de pare-feu peut être différent pour les différentes versions de Windows.
Utilisez `Get-NetFirewallRule` pour afficher une liste de règles. Avant d’activer la règle de pare-feu, affichez les paramètres de sécurité de la règle pour vérifier que la configuration est adaptée à votre environnement.

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

Par défaut, `Enable-PSRemoting` crée des règles de réseau qui autorisent l’accès à distance à partir de réseaux privés et de domaine. La commande utilise le paramètre **SkipNetworkProfileCheck** pour autoriser l'accès à distance à partir de réseaux publics dans le même sous-réseau local. La commande spécifie le paramètre **force** pour supprimer les messages de confirmation.

Le paramètre **SkipNetworkProfileCheck** n’affecte pas les versions serveur du système d’exploitation Windows, qui autorisent l’accès à distance à partir de réseaux publics dans le même sous-réseau local par défaut.

L' `Set-NetFirewallRule` applet de commande du module **netsecurity** ajoute une règle de pare-feu qui autorise l’accès à distance à partir de n’importe quel emplacement distant à partir de réseaux publics. Cela comprend les emplacements situés dans des sous-réseaux différents.

### Exemple 4 : créer une session à distance sur la configuration de point de terminaison récemment activée

Cet exemple montre comment activer la communication à distance PowerShell sur un ordinateur, rechercher les noms de points de terminaison configurés et créer une session à distance sur l’un des points de terminaison.

La première commande active la communication à distance PowerShell sur l’ordinateur.

La deuxième commande répertorie les configurations de point de terminaison.

La troisième commande crée une session PowerShell distante sur le même ordinateur, en spécifiant le point de terminaison **PowerShell. 6** par son nom. La session à distance sera hébergée avec la dernière version de PowerShell 6 (6.2.2).

La dernière commande accède à la `$PSVersionTable` variable dans la session à distance pour afficher la version de PowerShell qui héberge la session.

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

> [!NOTE]
> Le nom de la règle de pare-feu peut être différent selon la version de Windows. Utilisez l' `Get-NetFirewallRule` applet de commande pour répertorier les noms des règles sur votre système.

## PARAMÈTRES

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

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

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

### -SkipNetworkProfileCheck

Indique que cette applet de commande active la communication à distance sur les versions clientes du système d’exploitation Windows lorsque l’ordinateur se trouve sur un réseau public. Ce paramètre active une règle de pare-feu pour les réseaux publics. Celle-ci n'autorise l'accès à distance qu'à partir d'ordinateurs du même sous-réseau local.

Ce paramètre n’affecte pas les versions serveur du système d’exploitation Windows, qui, par défaut, ont une règle de pare-feu de sous-réseau local pour les réseaux publics. Si la règle de pare-feu de sous-réseau local est désactivée sur une version de serveur, `Enable-PSRemoting` réactivez-la, quelle que soit la valeur de ce paramètre.

Pour supprimer la restriction de sous-réseau local et activer l’accès à distance à partir de tous les emplacements sur les réseaux publics, utilisez l' `Set-NetFirewallRule` applet de commande dans le module **netsecurity** .

Ce paramètre a été introduit dans PowerShell 3,0.

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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System.String

Cette applet de commande retourne des chaînes qui décrivent ses résultats.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

Sur les versions serveur du système d’exploitation Windows, `Enable-PSRemoting` crée des règles de pare-feu pour les réseaux privés et de domaine qui autorisent l’accès à distance, et crée une règle de pare-feu pour les réseaux publics qui autorise l’accès à distance uniquement à partir d’ordinateurs situés dans le même sous-réseau local.

Sur les versions clientes du système d’exploitation Windows, `Enable-PSRemoting` crée des règles de pare-feu pour les réseaux privés et de domaine qui autorisent l’accès à distance illimité. Pour créer une règle de pare-feu pour les réseaux publics qui autorise l'accès à distance à partir du même sous-réseau local, utilisez le paramètre **SkipNetworkProfileCheck**.

Sur les versions client ou serveur du système d’exploitation Windows, pour créer une règle de pare-feu pour les réseaux publics qui supprime la restriction de sous-réseau local et autorise l’accès à distance, utilisez l' `Set-NetFirewallRule` applet de commande dans le module netsecurity pour exécuter la commande suivante : `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`

`Enable-PSRemoting` Active toutes les configurations de session en définissant la valeur de la propriété **Enabled** de toutes les configurations de session sur `$True` .

`Enable-PSRemoting` supprime les paramètres **Deny_All** et **Network_Deny_All** . Cela permet l’accès à distance aux configurations de session qui ont été réservées pour une utilisation locale.

## LIENS CONNEXES

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Disable-PSRemoting](Disable-PSRemoting.md)

[Fournisseur WSMan](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Remote](About/about_Remote.md)

[about_Session_Configurations](About/about_Session_Configurations.md)
