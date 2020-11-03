---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 1c8cde77d16452c9488ce3af62e8b5f761213c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202049"
---
# Rename-Computer

## SYNOPSIS
Renomme un ordinateur.

## SYNTAX

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Rename-Computer` applet de commande renomme l’ordinateur local ou un ordinateur distant.
Elle renomme un ordinateur dans chaque commande.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : renommer l’ordinateur local

Cette commande renomme l’ordinateur local en, puis le `Server044` redémarre pour que la modification soit effective.

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### Exemple 2 : renommer un ordinateur distant

Cette commande renomme l' `Srv01` ordinateur en `Server001` . L’ordinateur n’est pas redémarré.

Le paramètre **DomainCredential** spécifie les informations d’identification d’un utilisateur qui a l’autorisation de renommer des ordinateurs dans le domaine.

Le paramètre **force** supprime l’invite de confirmation.

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## PARAMETERS

### -ComputerName

Renomme l’ordinateur distant spécifié.
La valeur par défaut est l'ordinateur local.

Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ordinateur distant.
Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point ( `.` ) ou `localhost` .

Ce paramètre ne s’appuie pas sur la communication à distance PowerShell.
Vous pouvez utiliser le paramètre **ComputerName** de `Rename-Computer` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DomainCredential

Spécifie un compte d’utilisateur qui a l’autorisation de se connecter au domaine.
Des informations d’identification explicites sont requises pour renommer un ordinateur qui est joint à un domaine.

Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .

Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter à l’ordinateur spécifié par le paramètre **ComputerName** , utilisez le paramètre **LocalCredential** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

### -LocalCredential

Spécifie un compte d’utilisateur qui a l’autorisation de se connecter à l’ordinateur spécifié par le paramètre **ComputerName** . La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que `User01` ou `Domain01\User01` , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .

Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter au domaine, utilisez le paramètre **DomainCredential** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### -NewName

Spécifie un nouveau nom pour l’ordinateur.
Ce paramètre est obligatoire.

Les noms standard peuvent contenir des lettres ( `a-z` ), ( `A-Z` ), des nombres ( `0-9` ) et des traits d’Union ( `-` ), mais pas d’espaces ni de points ( `.` ). Le nom ne peut pas être entièrement composé de chiffres et ne peut pas comporter plus de 63 caractères.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourne les résultats de la commande.
Sinon, cette applet de commande ne génère aucune sortie.

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

### -Restart

Indique que cette applet de commande redémarre l’ordinateur qui a été renommé.
Un redémarrage est souvent nécessaire pour que le changement devienne effectif.

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

### -WsmanAuthentication

Spécifie le mécanisme utilisé pour authentifier les informations d’identification de l’utilisateur lorsque cette applet de commande utilise le protocole WSMan. Les valeurs valides pour ce paramètre sont :

- **De base**
- **CredSSP**
- **Par défaut**
- **Digest**
- **Kerberos**
- **Prescrit**

La valeur par défaut est **Default** .

Pour plus d’informations sur les valeurs de ce paramètre, consultez [énumération AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!WARNING]
> L’authentification CredSSP (Credential Security Service Provider), dans laquelle les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées, est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.
> Ce mécanisme augmente le risque de sécurité lié à l'opération distante.
> Si l’ordinateur distant est compromis, les informations d’identification qui lui sont transmises peuvent être utilisées pour contrôler > la session réseau.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: None
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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### Aucun

Cette applet de commande n’a pas de paramètres qui acceptent une entrée par valeur.
Toutefois, vous pouvez diriger les valeurs des propriétés **ComputerName** et **NewName** des objets vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. Commands. ComputerChangeInfo

Cette applet de commande retourne un objet **ComputerChangeInfo** , si vous spécifiez le paramètre **PassThru** .
Sinon, elle ne retourne aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)

