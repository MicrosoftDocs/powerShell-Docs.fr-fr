---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroup
ms.openlocfilehash: 6a2f921972fef1794581b301df6e7439e56c7f47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203625"
---
# Remove-LocalGroup

## SYNOPSIS
Supprime les groupes de sécurité locaux.

## SYNTAX

### InputObject

```
Remove-LocalGroup [-InputObject] <LocalGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Default

```
Remove-LocalGroup [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Remove-LocalGroup [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **Remove-LocalGroup** supprime les groupes de sécurité locaux.
Cette applet de commande supprime uniquement un groupe local.
Elle ne supprime pas les comptes d’utilisateur, les comptes d’ordinateurs ou les comptes de groupe qui appartiennent à ce groupe.
Vous ne pouvez pas récupérer un groupe supprimé.

Si vous supprimez un groupe, puis créez un autre groupe qui porte le même nom de groupe, vous devez définir de nouvelles autorisations pour le nouveau groupe.
Le nouveau groupe n’hérite pas des autorisations qui ont été affectées au groupe.

> [!NOTE]
> Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.

## EXEMPLES

### Exemple 1 : supprimer un groupe de sécurité

```
PS C:\> Remove-LocalGroup -Name "SecurityGroup04"
```

Cette commande supprime le groupe nommé SecurityGroup04.

## PARAMETERS

### -InputObject
Spécifie un tableau de groupes de sécurité que cette applet de commande supprime.
Pour obtenir des groupes, utilisez l’applet de commande Get-LocalGroup.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Spécifie un tableau de noms des groupes de sécurité que cette applet de commande supprime.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
Spécifie un tableau d’ID de sécurité (SID) des groupes de sécurité que cette applet de commande supprime.

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. principal. SecurityIdentifier
Vous pouvez diriger un groupe de sécurité, une chaîne ou un SID vers cette applet de commande.

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

* Cette applet de commande ne peut pas supprimer les groupes par défaut suivants :

- Administrateurs
- Opérateurs de sauvegarde
- Opérateurs de chiffrement
- Utilisateurs du modèle COM distribué
- Lecteurs des journaux d’événements
- Invités
- Administrateurs Hyper-V
- IIS_IUSRS
- Opérateurs de configuration réseau
- Utilisateurs du journal des performances
- Utilisateurs de l’Analyseur de performances
- Utilisateurs avec pouvoir
- Utilisateurs du Bureau à distance
- Utilisateurs de gestion à distance
- Duplicateur
- Utilisateurs
- WinRMRemoteWMIUsers__

* La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet. Les sources possibles sont les suivantes :

- Local
- Active Directory
- Groupe Azure Active Directory
- Compte Microsoft

**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows. Pour les versions antérieures, la propriété est vide.

## LIENS CONNEXES

[Get-LocalGroup](Get-LocalGroup.md)

[New-LocalGroup](New-LocalGroup.md)

[Rename-LocalGroup](Rename-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
