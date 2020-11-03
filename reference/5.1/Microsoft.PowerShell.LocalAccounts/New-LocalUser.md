---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalUser
ms.openlocfilehash: d83f3ad12481df0849ff2fe3f61d553a9ffdcdde
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203622"
---
# New-LocalUser

## SYNOPSIS

Crée un compte d’utilisateur local.

## SYNTAX

### Mot de passe (par défaut)

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> -Password <SecureString> [-PasswordNeverExpires]
 [-UserMayNotChangePassword] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Nopassword

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> [-NoPassword] [-UserMayNotChangePassword] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `New-LocalUser` applet de commande crée un compte d’utilisateur local. Cette applet de commande crée un compte d’utilisateur local ou un compte d’utilisateur local qui est connecté à un compte Microsoft.

> [!NOTE]
> Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.

## EXEMPLES

### Exemple 1 : créer un compte d’utilisateur

```
PS C:\> New-LocalUser -Name "User02" -Description "Description of this account." -NoPassword
Name    Enabled  Description
----    -------  -----------
User02  True     Description of this account.
```

Cette commande crée un compte d’utilisateur local et ne spécifie pas les paramètres de **AccountExpires dans** ou **de mot de passe** . Par conséquent, le compte n’expire pas ou n’a pas de mot de passe par défaut.

### Exemple 2 : créer un compte d’utilisateur avec un mot de passe

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> New-LocalUser "User03" -Password $Password -FullName "Third User" -Description "Description of this account."
Name    Enabled  Description
----    -------  -----------
User03  True     Description of this account.
```

La première commande vous invite à entrer un mot de passe à l’aide de l’applet de commande `Read-Host` . La commande stocke le mot de passe en tant que chaîne sécurisée dans la `$Password` variable.

La deuxième commande crée un compte d’utilisateur local à l’aide du mot de passe stocké dans `$Password` . La commande spécifie un nom d’utilisateur, un nom complet et une description pour le compte d’utilisateur.

## PARAMETERS

### -AccountExpires dans

Spécifie à quel moment le compte d’utilisateur expire. Pour obtenir un objet **DateTime** , utilisez l' `Get-Date` applet de commande.
Si vous ne spécifiez pas ce paramètre, le compte n’expire pas.

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -AccountNeverExpires

Indique que le compte n’expire pas.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### Description

Spécifie un commentaire pour le compte d’utilisateur.
La longueur maximale est de 48 caractères.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Désactivé

Indique que cette applet de commande crée le compte d’utilisateur comme étant désactivé.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FullName

Spécifie le nom complet du compte d’utilisateur. Le nom complet est différent du nom d’utilisateur du compte d’utilisateur.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie le nom d’utilisateur du compte d’utilisateur.

Si vous créez un compte d’utilisateur local pour le système local, le nom d’utilisateur peut contenir jusqu’à 20 caractères majuscules ou minuscules. Un nom d’utilisateur ne peut pas contenir les caractères suivants :

`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`

Un nom d’utilisateur ne peut pas être composé uniquement de points `.` ou d’espaces.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Nopassword

Indique que le compte d’utilisateur n’a pas de mot de passe.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoPassword
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Mot de passe

Spécifie un mot de passe pour le compte d’utilisateur. Vous pouvez utiliser `Read-Host -GetCredential` , `Get-Credential` ou `ConvertTo-SecureString` pour créer un objet **SecureString** pour le mot de passe.

Si vous omettez les paramètres **mot de passe** et **nopassword** , vous `New-LocalUser` invite à entrer le mot de passe du nouvel utilisateur.

```yaml
Type: System.Security.SecureString
Parameter Sets: Password
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PasswordNeverExpires

Indique si le mot de passe expire.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Password
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UserMayNotChangePassword

Indique que l’utilisateur ne peut pas modifier le mot de passe du compte d’utilisateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System. String, System. DateTime, System. Boolean, System. Security. SecureString

Vous pouvez diriger une chaîne, un objet **DateTime** , une valeur booléenne ou une chaîne sécurisée vers cette applet de commande.

## SORTIES

### System. Management. Automation. SecurityAccountsManager. LocalUser

Cette applet de commande retourne un objet **LocalUser** .
Cet objet fournit des informations sur le compte d’utilisateur.

## REMARQUES

- Un nom d’utilisateur ne peut pas être identique à un autre nom d’utilisateur ou de groupe sur l’ordinateur. Un nom d’utilisateur ne peut pas être composé uniquement de points `.` ou d’espaces. Un nom d’utilisateur peut contenir jusqu’à 20 caractères majuscules ou minuscules. Un nom d’utilisateur ne peut pas contenir les caractères suivants :

`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`

- Un mot de passe peut contenir jusqu’à 127 caractères.
- La propriété **PrincipalSource** est une propriété des objets **LocalUser** , **LocalGroup** et **LocalPrincipal** qui décrit la source de l’objet. Les sources possibles sont les suivantes :

  - Local
  - Active Directory
  - Groupe Azure Active Directory
  - Compte Microsoft

> [!NOTE]
> **PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows. Pour les versions antérieures, la propriété est vide.

## LIENS CONNEXES

[Disable-LocalUser](Disable-LocalUser.md)

[Enable-LocalUser](Enable-LocalUser.md)

[Get-LocalUser](Get-LocalUser.md)

[Remove-LocalUser](Remove-LocalUser.md)

[Rename-LocalUser](Rename-LocalUser.md)

[Set-LocalUser](Set-LocalUser.md)
