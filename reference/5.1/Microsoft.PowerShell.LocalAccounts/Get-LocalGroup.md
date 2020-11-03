---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroup
ms.openlocfilehash: 2cd77c2766840527825b0ccf68abaac3c2ea6c16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202238"
---
# Get-LocalGroup

## SYNOPSIS
Obtient les groupes de sécurité locaux.

## SYNTAX

### Valeur par défaut (par défaut)

```
Get-LocalGroup [[-Name] <String[]>] [<CommonParameters>]
```

### SecurityIdentifier

```
Get-LocalGroup [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## Description
L’applet de commande **obtenir-LocalGroup** obtient les groupes de sécurité locaux dans le gestionnaire de comptes de sécurité.
Cette applet de commande obtient les groupes intégrés et les groupes de sécurité locaux par défaut que vous créez.

> [!NOTE]
> Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.

## EXEMPLES

### Exemple 1 : récupérer le groupe administrateurs

```
PS C:\> Get-LocalGroup -Name "Administrators"
Name           Description
----           -----------
Administrators Administrators have complete and unrestricted access to the computer/domain
```

Cette commande obtient le groupe Administrateurs local.
La commande affiche les propriétés du groupe dans la console.

## PARAMETERS

### -Name
Spécifie un tableau de noms de groupes de sécurité que cette applet de commande obtient.
Vous pouvez utiliser le caractère générique.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
Spécifie un tableau d’ID de sécurité (SID) des groupes de sécurité que cette applet de commande obtient.

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

### System. Management. Automation. SecurityAccountsManager. LocalGroup
Cette applet de commande retourne un groupe local.

## REMARQUES

* La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet. Les sources possibles sont les suivantes :

- Local
- Active Directory
- Groupe Azure Active Directory
- Compte Microsoft

**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows. Pour les versions antérieures, la propriété est vide.

## LIENS CONNEXES

[New-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroup](Remove-LocalGroup.md)

[Rename-LocalGroup](Rename-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
