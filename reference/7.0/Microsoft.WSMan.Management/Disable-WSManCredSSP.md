---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 3202e21b5f002610557f827f3a5f65659dec6823
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201706"
---
# Disable-WSManCredSSP

## SYNOPSIS
Désactive l’authentification CredSSP sur un ordinateur.

## SYNTAX

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## Description
L’applet de commande **Disable-WSManCredSSP** désactive l’authentification CredSSP (Credential Security Support Provider) sur un client ou sur un ordinateur serveur.
Lorsque l’authentification CredSSP est utilisée, les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées.

Utilisez cette applet de commande pour désactiver CredSSP sur le client en spécifiant le client dans le paramètre *role* .
Cette applet de commande effectue les actions suivantes :

- Désactive CredSSP sur le client. Cette applet de commande définit le paramètre WS-Management **\<localhost|computername\> \Client\Auth\CredSSP** sur false.
- Supprime tout paramètre WSMan/* de la stratégie Windows CredSSP **AllowFreshCredentials** sur le client.

Utilisez cette applet de commande pour désactiver CredSSP sur le serveur en spécifiant le serveur dans le *rôle* .
Cette applet de commande effectue l’action suivante :

- Désactive CredSSP sur le serveur. Cette applet de commande définit le paramètre WS-Management **\<localhost|computername\> \Service\Auth\CredSSP** sur false.

ATTENTION : l’authentification CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.
Cette pratique augmente le risque de sécurité lié à l'opération distante.
Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

## EXEMPLES

### Exemple 1 : désactiver CredSSP sur un client

```
PS C:\> Disable-WSManCredSSP -Role Client
```

Cette commande désactive CredSSP sur le client, ce qui empêche la délégation aux serveurs.

### Exemple 2 : désactiver CredSSP sur un serveur

```
PS C:\> Disable-WSManCredSSP -Role Server
```

Cette commande désactive CredSSP sur le serveur, ce qui empêche la délégation des clients.

## PARAMETERS

### -Rôle
Spécifie s’il faut désactiver CredSSP en tant que client ou serveur.
Les valeurs acceptables pour ce paramètre sont : client et serveur.

Si vous spécifiez client, cette applet de commande effectue les actions suivantes :

- Désactive CredSSP sur le client. Cette applet de commande définit WS-Management affecter la valeur false à **\<localhost|computername\> \Client\Auth\CredSSP** .
- Supprime tout paramètre WSMan/* de la stratégie Windows CredSSP **AllowFreshCredentials** sur le client.

Si vous spécifiez Server, cette applet de commande effectue l’action suivante :

- Désactive CredSSP sur le serveur. Cette applet de commande définit le paramètre WS-Management **\<localhost|computername\> \Service\Auth\CredSSP** sur false.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
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
Cette applet de commande ne génère aucune sortie.

## REMARQUES

* Pour activer l'authentification CredSSP, utilisez l'applet de commande Enable-WSManCredSSP.

*

## LIENS CONNEXES

[Connect-WSMan](Connect-WSMan.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
