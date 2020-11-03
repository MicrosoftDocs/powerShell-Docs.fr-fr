---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: 570355eb1f793cbdd7a8a87fdcba312cce0113ca
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "93206201"
---
# Set-WSManQuickConfig

## SYNOPSIS
Configure l'ordinateur local pour la gestion à distance.

## SYNTAX

### Tous

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## Description

L' `Set-WSManQuickConfig` applet de commande configure l’ordinateur pour recevoir des commandes à distance PowerShell qui sont envoyées à l’aide de la technologie Web Services for Management (WS-Management).

`Set-WSManQuickConfig` effectue les actions suivantes :

- Vérifie si le service WinRM est en cours d’exécution. Si le service WinRM n’est pas en cours d’exécution, le service est démarré.
- Définit le type de démarrage du service WinRM sur Automatique.
- Crée un écouteur pour accepter les demandes sur n’importe quelle adresse IP. Le transport par défaut est **http** .
- Active une exception de pare-feu pour le trafic WinRM.

Pour exécuter `Set-WSManQuickConfig` , démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

## EXEMPLES

### Exemple 1 : activer la gestion à distance de l’ordinateur local via HTTP

Cet exemple définit la configuration requise pour activer la gestion à distance de l’ordinateur local. Par défaut, cette commande crée un écouteur WS-Management sur **http** .

```powershell
Set-WSManQuickConfig
```

### Exemple 2 : activer la gestion à distance de l’ordinateur local via HTTPs

Cet exemple définit la configuration requise pour activer la gestion à distance de l’ordinateur local. Le paramètre **UseSSL** spécifie que le **protocole HTTPS** est utilisé pour communiquer avec l’ordinateur.

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> **Https** nécessite une configuration manuelle. Pour plus d’informations, consultez la description du paramètre **UseSSL** .

## PARAMETERS

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipNetworkProfileCheck

Configure les versions du client Windows pour la communication à distance lorsque l’ordinateur se trouve sur un réseau public. Ce paramètre active une règle de pare-feu pour les réseaux publics. Celle-ci n'autorise l'accès à distance qu'à partir d'ordinateurs du même sous-réseau local.

Ce paramètre n’a aucun effet sur les versions serveur de Windows, qui, par défaut, ont une règle de pare-feu de sous-réseau local pour les réseaux publics. Si la règle de pare-feu de sous-réseau local est désactivée sur la version serveur de Windows, `Enable-PSRemoting` réactivez-la, quelle que soit la valeur de ce paramètre.

Pour supprimer la restriction de sous-réseau local et activer l’accès à distance à partir de tous les emplacements sur les réseaux publics, utilisez l' `Set-NetFirewallRule` applet de commande dans le module **netsecurity** .

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Spécifie que le protocole protocole SSL (SSL) est utilisé pour établir une connexion à l’ordinateur distant. Par défaut, SSL n’est pas utilisé.

WS-Management chiffre tout le contenu PowerShell transmis sur le réseau. Le paramètre **UseSSL** vous permet de spécifier la protection supplémentaire du protocole HTTPS au lieu de http. Si vous utilisez ce paramètre et que le protocole SSL n’est pas disponible sur le port utilisé pour la connexion, la commande échoue.

**Https** requiert la configuration manuelle de WinRM et des règles de pare-feu. Pour plus d’informations, consultez [Comment : configurer WINRM pour HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

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

Cette applet de commande n’accepte aucune entrée.

## SORTIES

### Aucun

Cette applet de commande ne génère pas de sortie.

## REMARQUES

## LIENS CONNEXES

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-PSRemoting](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Procédure : configurer WINRM pour HTTPs](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Test-WSMan](Test-WSMan.md)
