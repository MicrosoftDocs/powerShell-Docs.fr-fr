---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: 794146b1b347ad547c3283383aca32662d6433ca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205033"
---
# Get-PfxCertificate

## SYNOPSIS
Obtient des informations sur les fichiers de certificat PFX sur l’ordinateur.

## SYNTAX

### ByPath (par défaut)

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### ByLiteralPath

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## Description

L' `Get-PfxCertificate` applet de commande obtient un objet représentant chaque fichier de certificat pfx spécifié.
Un fichier PFX contient à la fois le certificat et une clé privée.

## EXEMPLES

### Exemple 1 : obtenir un certificat PFX

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

Cette commande obtient des informations sur le fichier de certificat test. pfx sur le système.

### Exemple 2 : obtenir un certificat PFX à partir d’un ordinateur distant

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

Cette commande obtient un fichier de certificat PFX de l’ordinateur distant SERVEUR01. Il utilise `Invoke-Command` pour exécuter une `Get-PfxCertificate` commande à distance.

Lorsque le fichier de certificat PFX n’est pas protégé par un mot de passe, la valeur du paramètre d' **authentification** de `Invoke-Command` doit être CredSSP.

## PARAMETERS

### -FilePath

Spécifie le chemin d’accès complet au fichier PFX du fichier sécurisé. Si vous spécifiez une valeur pour ce paramètre, il n’est pas nécessaire de taper `-FilePath` au niveau de la ligne de commande.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Chemin d’accès complet au fichier PFX du fichier sécurisé. Contrairement à **FilePath** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoPromptForPassword

Supprime la demande d’un mot de passe.

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

### -Mot de passe

Spécifie un mot de passe requis pour accéder à un `.pfx` fichier de certificat.

Ce paramètre a été introduit dans PowerShell 6,1.

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

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

Vous pouvez diriger une chaîne qui contient un chemin d’accès de fichier vers `Get-PfxCertificate` .

## SORTIES

### System.Security.Cryptography.X509Certificates.X509Certificate2

`Get-PfxCertificate` retourne un objet pour chaque certificat qu’il obtient.

## REMARQUES

Lorsque vous utilisez la `Invoke-Command` cmdlet pour exécuter une `Get-PfxCertificate` commande à distance et que le fichier de certificat pfx n’est pas protégé par un mot de passe, la valeur du paramètre d' **authentification** de `Invoke-Command` doit être CredSSP.

## LIENS CONNEXES

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

