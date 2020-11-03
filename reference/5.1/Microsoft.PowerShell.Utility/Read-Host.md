---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 9017d2352f1d2735f21343f4c1194c5e97ce2848
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "93205250"
---
# Read-Host

## SYNOPSIS
Lit une ligne d'entrée de la console.

## SYNTAX

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## Description

L' `Read-Host` applet de commande lit une ligne d’entrée à partir de la console. Vous pouvez l'utiliser pour inviter un utilisateur à saisir une entrée. Comme vous pouvez enregistrer l'entrée sous la forme d'une chaîne sécurisée, vous pouvez utiliser cette applet de commande pour inviter les utilisateurs à entrer des données de sécurité, telles que des mots de passe, ainsi que des données partagées.

## EXEMPLES

### Exemple 1 : enregistrer l’entrée de la console dans une variable

Cet exemple affiche la chaîne « Veuillez entrer votre âge : » en tant qu’invite. Quand une valeur est entrée et que la touche entrée est enfoncée, la valeur est stockée dans la `$Age` variable.

```powershell
$Age = Read-Host "Please enter your age"
```

### Exemple 2 : enregistrer l’entrée de la console en tant que chaîne sécurisée

Cet exemple affiche la chaîne « Entrez un mot de passe : » en tant qu’invite. Quand une valeur est entrée, des astérisques ( `*` ) apparaissent sur la console à la place de l’entrée. Lorsque la touche entrée est enfoncée, la valeur est stockée sous la forme d’un objet **SecureString** dans la `$pwd_secure_string` variable.

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## PARAMETERS

### -AsSecureString

Indique que l’applet de commande affiche des astérisques ( `*` ) à la place des caractères que l’utilisateur tape comme entrée. Lorsque vous utilisez ce paramètre, la sortie de l' `Read-Host` applet de commande est un objet **SecureString** ( **System. Security. SecureString** ).

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

### -Invite

Spécifie le texte de l'invite.
Tapez une chaîne.
Si la chaîne inclut des espaces, mettez-la entre guillemets.
PowerShell ajoute un signe deux-points ( `:` ) au texte que vous entrez.

```yaml
Type: System.Object
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

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. String ou System. Security. SecureString

Si le paramètre **AsSecureString** est utilisé, `Read-Host` retourne une **SecureString** . Sinon, une chaîne est retournée.

## REMARQUES

## LIENS CONNEXES

[Clear-Host](../microsoft.powershell.core/clear-host.md)

[Get-Host](Get-Host.md)

[Write-Host](Write-Host.md)

[ConvertFrom-SecureString](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
