---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-LocalGroupMember
ms.openlocfilehash: 06993c8f6618472f4809e37fbf83d298d13ae515
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202250"
---
# Add-LocalGroupMember

## SYNOPSIS
Ajoute des membres à un groupe local.

## SYNTAX

### Groupe

```
Add-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Default

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Add-LocalGroupMember` applet de commande ajoute des utilisateurs ou des groupes à un groupe de sécurité local. Tous les droits et les autorisations affectés à un groupe sont attribués à tous les membres de ce groupe.

Les membres du groupe Administrateurs sur un ordinateur local possèdent l’autorisation Contrôle total sur cet ordinateur. Limitez le nombre d’utilisateurs dans le groupe Administrateurs.

Si l’ordinateur est joint à un domaine, vous pouvez ajouter sur un ordinateur local des comptes d’utilisateurs, d’ordinateurs et de groupes à partir de ce domaine et de domaines approuvés.

> [!NOTE]
> Si l’ordinateur est joint à un domaine et que vous essayez d’ajouter un utilisateur local qui porte le même nom qu’un membre du domaine, il ajoute le membre du domaine.

## EXEMPLES

### Exemple 1 : ajouter des membres au groupe administrateurs

Cette commande ajoute plusieurs membres au groupe Administrateurs local. Les nouveaux membres incluent un compte d’utilisateur local, un compte Microsoft, un compte Azure Active Directory et un groupe de domaine. Cet exemple utilise une valeur d’espace réservé pour le nom d’utilisateur d’un compte sur Outlook.com.

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

## PARAMETERS

### -Group

Spécifie le groupe de sécurité auquel cette applet de commande ajoute des membres.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Membre

Spécifie un tableau d’utilisateurs ou de groupes que cette applet de commande ajoute à un groupe de sécurité. Vous pouvez spécifier des utilisateurs ou des groupes par nom, ID de sécurité (SID) ou objets **LocalPrincipal** .

```yaml
Type: Microsoft.PowerShell.Commands.LocalPrincipal[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie le nom du groupe de sécurité auquel cette applet de commande ajoute des membres.

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SID

Spécifie l’ID de sécurité du groupe de sécurité auquel cette applet de commande ajoute des membres.

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
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

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

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

### System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. principal. SecurityIdentifier

Vous pouvez diriger un principal local, une chaîne ou un SID vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.

La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet. Les sources possibles sont les suivantes :

- Local
- Active Directory
- Groupe Azure Active Directory
- Compte Microsoft

**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows. Pour les versions antérieures, la propriété est vide.

## LIENS CONNEXES

[Get-LocalGroupMember](Get-LocalGroupMember.md)

[New-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroupMember](Remove-LocalGroupMember.md)
