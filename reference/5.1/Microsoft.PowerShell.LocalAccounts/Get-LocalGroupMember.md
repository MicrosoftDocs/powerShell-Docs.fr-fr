---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroupMember
ms.openlocfilehash: 200368c5d13bd027302ad824533e6c187906ed0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202233"
---
# Get-LocalGroupMember

## SYNOPSIS
Obtient les membres d’un groupe local.

## SYNTAX

### Valeur par défaut (par défaut)

```
Get-LocalGroupMember [[-Member] <String>] [-Name] <String> [<CommonParameters>]
```

### Groupe

```
Get-LocalGroupMember [-Group] <LocalGroup> [[-Member] <String>] [<CommonParameters>]
```

### SecurityIdentifier

```
Get-LocalGroupMember [[-Member] <String>] [-SID] <SecurityIdentifier> [<CommonParameters>]
```

## Description
L’applet de commande **obtenir-LocalGroupMember** obtient les membres d’un groupe local.

> [!NOTE]
> Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.

## EXEMPLES

### Exemple 1 : récupération de tous les membres du groupe administrateurs

```
PS C:\> Get-LocalGroupMember -Group "Administrators"
ObjectClass Name                    PrincipalSource
----------- ----                    ---------------
User        CONTOSOPC\Administrator Local
User        CONTOSOPC\LocalAdmin    Local
```

Cette commande obtient tous les membres du groupe Administrateurs local.

## PARAMETERS

### -Group
Spécifie le groupe de sécurité à partir duquel cette applet de commande obtient des membres.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Membre
Spécifie un utilisateur ou un groupe que cette applet de commande obtient d’un groupe de sécurité.
Vous pouvez spécifier des utilisateurs ou des groupes par nom ou ID de sécurité (SID).
Spécifiez les chaînes SID dans S-R-I-S-S.
. .
HH:MM:SS.
Vous pouvez utiliser des caractères génériques.
Si vous ne spécifiez pas ce paramètre, l’applet de commande obtient tous les membres du groupe.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Spécifie le nom du groupe de sécurité à partir duquel cette applet de commande obtient des membres.

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
Spécifie l’ID de sécurité du groupe de sécurité à partir duquel cette applet de commande obtient des membres.

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. principal. SecurityIdentifier
Vous pouvez diriger un groupe local, une chaîne ou un SID vers cette applet de commande.

## SORTIES

### Microsoft. SecurityAccountsManager. LocalPrincipal
Cette applet de commande retourne les principaux locaux.

## REMARQUES

* La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet. Les sources possibles sont les suivantes :

- Local
- Active Directory
- Groupe Azure Active Directory
- Compte Microsoft

**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows. Pour les versions antérieures, la propriété est vide.

## LIENS CONNEXES

[Add-LocalGroupMember](Add-LocalGroupMember.md)

[New-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroupMember](Remove-LocalGroupMember.md)
