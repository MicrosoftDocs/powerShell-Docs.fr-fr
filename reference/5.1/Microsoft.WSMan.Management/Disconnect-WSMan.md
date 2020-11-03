---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 8e1a406b56d5e74ade438699847b80b0adab2a24
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208697"
---
# Disconnect-WSMan

## SYNOPSIS
Déconnecte le client du service WinRM sur un ordinateur distant.

## SYNTAX

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## Description
L’applet de commande Disconnect **-WSMan** déconnecte le client du service WinRM sur un ordinateur distant.
Si vous avez enregistré la session de WS-Management dans une variable, l’objet de session reste dans la variable, mais l’état de la session de WS-Management est fermé.
Vous pouvez utiliser cette applet de commande dans le contexte du fournisseur WSMan pour déconnecter le client du service WinRM sur un ordinateur distant.
Toutefois, vous pouvez également utiliser cette applet de commande pour vous déconnecter du service WinRM sur les ordinateurs distants avant de choisir le fournisseur WSMan.

Pour plus d'informations sur la façon de se connecter au service WinRM sur un ordinateur distant, consultez Connect-WSMan.

## EXEMPLES

### Exemple 1 : supprimer une connexion à un ordinateur distant

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

Cette commande supprime la connexion à l’ordinateur distant nommé SERVEUR01.

Cette applet de commande est généralement utilisée dans le contexte du fournisseur WSMan pour se déconnecter d'un ordinateur distant, dans ce cas l'ordinateur server01.
Toutefois, vous pouvez également utiliser **Disconnect-WSMan** pour supprimer les connexions aux ordinateurs distants avant de passer au fournisseur WSMan.
Ces connexions n’apparaissent pas dans la liste ComputerName.

## PARAMETERS

### -ComputerName
Spécifie l’ordinateur sur lequel exécuter l’opération de gestion.
La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.
Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.
L'ordinateur local est la valeur par défaut.
Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.
Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.

Vous ne pouvez pas vous déconnecter de l’hôte local.
Autrement dit, vous ne pouvez pas déconnecter la connexion par défaut à l’ordinateur local.
Toutefois, si vous créez une connexion distincte à l’ordinateur local, par exemple, en utilisant le nom de l’ordinateur.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
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

## LIENS CONNEXES

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

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
