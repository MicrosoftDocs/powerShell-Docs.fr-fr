---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalUser
ms.openlocfilehash: 34210145bcddc8d9420552d637a6cd6e5f8e61cc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202230"
---
# Get-LocalUser

## SYNOPSIS
Obtient les comptes d’utilisateurs locaux.

## SYNTAX

### Valeur par défaut (par défaut)

```
Get-LocalUser [[-Name] <String[]>] [<CommonParameters>]
```

### SecurityIdentifier

```
Get-LocalUser [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## Description

L' `Get-LocalUser` applet de commande obtient les comptes d’utilisateurs locaux. Cette applet de commande obtient les comptes d’utilisateur intégrés par défaut, les comptes d’utilisateurs locaux que vous avez créés et les comptes locaux que vous avez connectés aux comptes Microsoft.

> [!NOTE]
> Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.

## EXEMPLES

### Exemple 1 : récupération d’un compte à l’aide de son nom

Cet exemple obtient un compte d’utilisateur nommé AdminContoso02.

```powershell
Get-LocalUser -Name "AdminContoso02"
```

```Output
Name             Enabled Description
----             ------- -----------
AdminContoso02   True    Description of this account.
```

### Exemple 2 : obtenir un compte connecté à un compte Microsoft

Cet exemple obtient un compte d’utilisateur qui est connecté à un compte Microsoft. Cet exemple utilise une valeur d’espace réservé pour le nom d’utilisateur d’un compte sur Outlook.com.

```powershell
Get-LocalUser -Name "MicrosoftAccount\username@Outlook.com"
```

```Output
Name                                    Enabled  Description
----                                    -------  -----------
MicrosoftAccount\username@outlook.com  True     Description of this account.
```

### Exemple 3 : obtenir un compte connecté à un compte Microsoft

Cet exemple obtient un compte d’utilisateur local qui a le SID spécifié.

```powershell
Get-LocalUser -SID S-1-5-21-9526073513-1762370368-3942940353-500
```

```Output
Name          Enabled Description
----          ------- -----------
Administrator True    Built-in account for administering the computer/domain
```

## PARAMETERS

### -Name

Spécifie un tableau de noms de comptes d’utilisateur que cette applet de commande obtient. Vous pouvez utiliser le caractère générique.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -SID

Spécifie un tableau d’ID de sécurité (SID) des comptes d’utilisateur que cette applet de commande obtient.

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. String, System. Security. principal. SecurityIdentifier

Vous pouvez diriger une chaîne ou un SID vers cette applet de commande.

## SORTIES

### System. Management. Automation. SecurityAccountsManager. LocalUser []

Cette applet de commande retourne les comptes d’utilisateurs locaux.

## REMARQUES

La propriété **PrincipalSource** sur les objets **LocalUser** , **LocalGroup** et **LocalPrincipal** décrit la source de l’objet. Les sources possibles sont les suivantes :

- Local
- Active Directory
- Groupe Azure Active Directory
- Compte Microsoft

**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows. Pour les versions antérieures, la propriété est vide.

## LIENS CONNEXES

[Disable-LocalUser](Disable-LocalUser.md)

[Enable-LocalUser](Enable-LocalUser.md)

[New-LocalUser](New-LocalUser.md)

[Remove-LocalUser](Remove-LocalUser.md)

[Rename-LocalUser](Rename-LocalUser.md)

[Set-LocalUser](Set-LocalUser.md)
