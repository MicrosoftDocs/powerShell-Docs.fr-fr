---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 0c8c386ab376afde3d15fcd29b3f653b3f738f63
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "93205306"
---
# Enable-PSRemoting

## SYNOPSIS
Configure l'ordinateur pour recevoir des commandes à distance.

## SYNTAX

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Enable-PSRemoting` applet de commande configure l’ordinateur pour qu’il reçoive les commandes PowerShell à distance qui sont envoyées à l’aide de la technologie WS-Management.

La communication à distance PowerShell est activée par défaut sur Windows Server 2012. Vous pouvez utiliser `Enable-PSRemoting` pour activer la communication à distance PowerShell sur d’autres versions de Windows prises en charge et pour réactiver la communication à distance sur Windows Server 2012 si elle est désactivée.

Vous ne devez exécuter cette commande qu’une seule fois sur chaque ordinateur qui recevra des commandes. Vous n’avez pas besoin de l’exécuter sur les ordinateurs qui envoient uniquement des commandes. Étant donné que la configuration démarre les écouteurs, il est prudent de l’exécuter uniquement lorsque cela est nécessaire.

À compter de PowerShell 3,0, l' `Enable-PSRemoting` applet de commande peut activer la communication à distance PowerShell sur les versions client de Windows lorsque l’ordinateur se trouve sur un réseau public. Pour plus d'informations, consultez la description du paramètre **SkipNetworkProfileCheck** .

L' `Enable-PSRemoting` applet de commande effectue les opérations suivantes :

- Exécute l’applet de commande [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) , qui effectue les tâches suivantes :
  - Démarre le service WinRM.
  - Définit le type de démarrage du service WinRM sur automatique.
  - Crée un écouteur pour accepter les demandes sur n’importe quelle adresse IP.
  - Active une exception de pare-feu pour les communications WS-Management.
  - Inscrit les configurations de session **Microsoft. PowerShell** et **Microsoft. PowerShell. Workflow** , si elles ne sont pas déjà inscrites.
  - Inscrit la configuration de session **Microsoft. powershell32** sur les ordinateurs 64 bits, si elle n’est pas déjà inscrite.
  - Active toutes les configurations de session.
  - Modifie le descripteur de sécurité de toutes les configurations de session pour autoriser l’accès à distance.
- Redémarre le service WinRM pour que les modifications précédentes soient effectives.

Pour exécuter cette applet de commande sur la plateforme Windows, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur. Cela ne s’applique pas aux versions Linux ou MacOS de PowerShell.

> [!CAUTION]
> Sur les systèmes qui ont à la fois PowerShell 3,0 et PowerShell 2,0, n’utilisez pas PowerShell 2,0 pour exécuter les `Enable-PSRemoting` applets de commande et `Disable-PSRemoting` . Les commandes peuvent sembler réussir, mais la communication à distance n'est pas configurée correctement. Les commandes distantes et les tentatives ultérieures d’activation et de désactivation de la communication à distance sont susceptibles d’échouer.

## EXEMPLES

### Exemple 1 : configurer un ordinateur pour recevoir des commandes à distance

Cette commande configure l'ordinateur pour qu'il reçoive les commandes à distance.

```powershell
Enable-PSRemoting
```

### Exemple 2 : configurer un ordinateur pour qu’il reçoive des commandes distantes sans invite de confirmation

Cette commande configure l'ordinateur pour qu'il reçoive les commandes à distance.
Le paramètre **force** supprime les invites utilisateur.

```powershell
Enable-PSRemoting -Force
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

> [!NOTE]
> Le nom de la règle de pare-feu peut être différent selon la version de Windows. Utilisez l' `Get-NetFirewallRule` applet de commande pour répertorier les noms des règles sur votre système.

## PARAMETERS

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

Dans PowerShell 3,0, `Enable-PSRemoting` crée les exceptions de pare-feu suivantes pour les communications WS-Management.

Sur les versions serveur du système d’exploitation Windows, `Enable-PSRemoting` crée des règles de pare-feu pour les réseaux privés et de domaine qui autorisent l’accès à distance, et crée une règle de pare-feu pour les réseaux publics qui autorise l’accès à distance uniquement à partir d’ordinateurs situés dans le même sous-réseau local.

Sur les versions clientes du système d’exploitation Windows, `Enable-PSRemoting` PowerShell 3,0 crée des règles de pare-feu pour les réseaux privés et de domaine qui autorisent l’accès à distance illimité. Pour créer une règle de pare-feu pour les réseaux publics qui autorise l'accès à distance à partir du même sous-réseau local, utilisez le paramètre **SkipNetworkProfileCheck** .

Sur les versions client ou serveur du système d’exploitation Windows, pour créer une règle de pare-feu pour les réseaux publics qui supprime la restriction de sous-réseau local et autorise l’accès à distance, utilisez l' `Set-NetFirewallRule` applet de commande dans le module netsecurity pour exécuter la commande suivante : `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`

Dans PowerShell 2,0, `Enable-PSRemoting` crée les exceptions de pare-feu suivantes pour les communications WS-Management.

Sur les versions serveur du système d’exploitation Windows, il crée des règles de pare-feu pour tous les réseaux qui autorisent l’accès à distance.

Sur les versions clientes du système d’exploitation Windows, `Enable-PSRemoting` PowerShell 2,0 crée une exception de pare-feu uniquement pour les emplacements de réseau privé et de domaine. Pour réduire les risques de sécurité, `Enable-PSRemoting` ne crée pas de règle de pare-feu pour les réseaux publics sur les versions client de Windows. Lorsque l’emplacement réseau actuel est public, `Enable-PSRemoting` retourne le message suivant : impossible de vérifier l’état du pare-feu.

À compter de PowerShell 3,0, `Enable-PSRemoting` Active toutes les configurations de session en définissant la valeur de la propriété **Enabled** de toutes les configurations de session sur `$True` .

Dans PowerShell 2,0, `Enable-PSRemoting` supprime le paramètre **Deny_All** du descripteur de sécurité des configurations de session. Dans PowerShell 3,0, `Enable-PSRemoting` supprime les paramètres **Deny_All** et **Network_Deny_All** . Cela permet l’accès à distance aux configurations de session qui ont été réservées pour une utilisation locale.

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
