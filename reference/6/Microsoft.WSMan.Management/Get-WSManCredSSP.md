---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 814be4153687268123114b4036b640eeb0f0da71
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200834"
---
# Get-WSManCredSSP

## SYNOPSIS
Obtient la configuration liée au fournisseur CredSSP (Credential Security Support Provider) pour le client.

## SYNTAX

```
Get-WSManCredSSP [<CommonParameters>]
```

## Description
L’applet de commande **obtenir-WSManCredSSP** obtient la configuration liée au fournisseur de prise en charge de la sécurité des informations d’identification du client et du serveur.
La sortie indique si l'authentification CredSSP (Credential Security Support Provider) est activée ou désactivée.
Cette applet de commande affiche également les informations de configuration pour la stratégie **AllowFreshCredentials** de CredSSP.

Lorsque vous utilisez l’authentification CredSSP, les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées.
Ce type d’authentification est conçu pour les commandes qui créent une session à distance à partir d’une autre session à distance.
Par exemple, si vous souhaitez exécuter une tâche en arrière-plan sur un ordinateur distant, utilisez ce type d’authentification.

L'applet de commande effectue les actions suivantes :

- Obtient le paramètre CredSSP WS-Management sur le client ( **\<localhost|computername\> \Client\Auth\CredSSP** ).
- Obtient le paramètre de stratégie CredSSP Windows **AllowFreshCredentials** .
- Obtient le paramètre CredSSP WS-Management sur le serveur ( **\<localhost|computername\> \Service\Auth\CredSSP** ).

ATTENTION : l’authentification CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.
Cette pratique augmente le risque de sécurité lié à l'opération distante.
Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.

## EXEMPLES

### Exemple 1 : afficher la configuration CredSSP

```
PS C:\> Get-WSManCredSSP
```

Cette commande affiche les informations de configuration CredSSP pour le client et le serveur.

La sortie indique si cet ordinateur est configuré ou non pour CredSSP.

Si l'ordinateur est configuré pour CredSSP, la sortie est la suivante :

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

Si l'ordinateur n'est pas configuré pour CredSSP, la sortie est la suivante :

`The machine is not configured to allow delegating fresh credentials.`

## PARAMETERS

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Cette applet de commande n’accepte aucune entrée.

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

* Pour désactiver l'authentification CredSSP, utilisez l'applet de commande Disable-WSManCredSSP. Pour activer l'authentification CredSSP, utilisez l'applet de commande Enable-WSManCredSSP.

## LIENS CONNEXES

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
