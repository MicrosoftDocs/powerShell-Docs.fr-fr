---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 5563413400abd28ce376265970631ad1206ca518
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685261"
---
# Read-Host

## SYNOPSIS
Lit une ligne d'entrée de la console.

## SYNTAX

### AsString (par défaut)

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### AsSecureString

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## Description

L' `Read-Host` applet de commande lit une ligne d’entrée à partir de la console. Vous pouvez l'utiliser pour inviter un utilisateur à saisir une entrée. Comme vous pouvez enregistrer l'entrée sous la forme d'une chaîne sécurisée, vous pouvez utiliser cette applet de commande pour inviter les utilisateurs à entrer des données de sécurité, telles que des mots de passe, ainsi que des données partagées.

> [!NOTE]
> `Read-Host` a une limite de 1022 caractères qu’il peut accepter comme entrée d’un utilisateur.

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

### Exemple 3 : entrée de masque et sous forme de chaîne en texte brut

Cet exemple affiche la chaîne « Entrez un mot de passe : » en tant qu’invite. Quand une valeur est entrée, des astérisques ( `*` ) apparaissent sur la console à la place de l’entrée. Lorsque la touche entrée est enfoncée, la valeur est stockée sous la forme d’un objet **chaîne** en texte clair dans la `$pwd_string` variable.

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## PARAMETERS

### -AsSecureString

Indique que l’applet de commande affiche des astérisques ( `*` ) à la place des caractères que l’utilisateur tape comme entrée. Lorsque vous utilisez ce paramètre, la sortie de l' `Read-Host` applet de commande est un objet **SecureString** (**System. Security. SecureString**).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsSecureString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaskInput

Indique que l’applet de commande affiche des astérisques ( `*` ) à la place des caractères que l’utilisateur tape comme entrée. Lorsque vous utilisez ce paramètre, la sortie de l' `Read-Host` applet de commande est un objet **String** .
Cela vous permet de demander en toute sécurité un mot de passe qui est retourné sous forme de texte brut au lieu de **SecureString**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Invite

Spécifie le texte de l'invite. Tapez une chaîne. Si la chaîne inclut des espaces, mettez-la entre guillemets. PowerShell ajoute un signe deux-points ( `:` ) au texte que vous entrez.

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

Si le paramètre **AsSecureString** est utilisé, `Read-Host` retourne une **SecureString**. Sinon, une chaîne est retournée.

## REMARQUES

## LIENS CONNEXES

[Clear-Host](../microsoft.powershell.core/clear-host.md)

[Get-Host](Get-Host.md)

[Write-Host](Write-Host.md)

[ConvertFrom-SecureString](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
