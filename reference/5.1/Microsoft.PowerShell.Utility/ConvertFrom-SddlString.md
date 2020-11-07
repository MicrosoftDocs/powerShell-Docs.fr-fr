---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: dbb6263c628c08876f64335b420f76d5ecc8f59b
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344369"
---
# ConvertFrom-SddlString

## SYNOPSIS
Convertit une chaîne SDDL en objet personnalisé.

## SYNTAXE

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <Object>] [<CommonParameters>]
```

## DESCRIPTION

L' `ConvertFrom-SddlString` applet de commande convertit une chaîne de langage de définition de descripteur de sécurité en objet **PSCustomObject** personnalisé avec les propriétés suivantes : Owner, Group, DiscretionaryAcl, SystemAcl et RawDescriptor.

Les propriétés Owner, Group, DiscretionaryAcl et SystemAcl contiennent une représentation textuelle lisible des droits d’accès spécifiés dans une chaîne SDDL.

Cette applet de commande a été introduite dans PowerShell 5,0.

## EXEMPLES

### Exemple 1 : convertir les SDDL droits d’accès du système de fichiers en PSCustomObject

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

La première commande utilise l' `Get-Acl` applet de commande pour obtenir le descripteur de sécurité pour le dossier C:\Windows et l’enregistre dans la variable.

La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.

### Exemple 2 : convertir les SDDL droits d’accès du registre en PSCustomObject

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

La première commande utilise l' `Get-Acl` applet de commande pour obtenir le descripteur de sécurité de la clé HKLM : \ SOFTWARE\Microsoft\ et l’enregistre dans la variable.

La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.

Elle utilise le `-Type` paramètre pour spécifier que la chaîne SDDL représente un descripteur de sécurité du Registre.

### Exemple 3 : convertir les SDDL droits d’accès du registre en PSCustomObject à l’aide de ConvertFrom-SddlString avec et sans le `-Type` paramètre

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

La première commande utilise l' `Get-Acl` applet de commande pour obtenir le descripteur de sécurité de la clé HKLM : \ SOFTWARE\Microsoft\ et l’enregistre dans la variable.

La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.

Il n’utilise pas le `-Type` paramètre, de sorte que les droits d’accès indiqués pour le système de fichiers.

La troisième commande utilise l' `ConvertFrom-SddlString` applet de commande avec le `-Type` paramètre, de sorte que les droits d’accès retournés sont pour Registry.

### Exemple 4 : convertir Active Directory SDDL de droits d’accès en un PSCustomObject

```powershell
$user = [ADSI]"LDAP://CN=username,CN=Users,DC=domain,DC=com"
ConvertFrom-SddlString $user.psbase.ObjectSecurity.Sddl -Type ActiveDirectoryRights
```

La première commande utilise les interfaces de service Active Directory (ADSI) pour récupérer l’objet utilisateur et l’enregistre dans la variable.

La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.

Elle utilise le `-Type` paramètre pour spécifier que la chaîne SDDL représente un descripteur de sécurité Active Directory.

## PARAMÈTRES

### -SDDL

Spécifie la chaîne représentant le descripteur de sécurité dans la syntaxe SDDL.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Type

Spécifie le type de droits que représente la chaîne SDDL.

Les valeurs valides pour ce paramètre sont :

- FileSystemRights
- RegistryRights
- ActiveDirectoryRights
- MutexRights
- SemaphoreRights
- CryptoKeyRights
- EventWaitHandleRights

Par défaut, l’applet de commande utilise les droits du système de fichiers.

CryptoKeyRights et ActiveDirectoryRights ne sont pas pris en charge dans PowerShell Core.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne SDDL vers `ConvertFrom-SddlString` .

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Langage de définition du descripteur de sécurité](/windows/win32/secauthz/security-descriptor-definition-language)
