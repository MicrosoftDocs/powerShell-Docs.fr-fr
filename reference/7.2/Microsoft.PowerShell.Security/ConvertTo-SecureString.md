---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: 0f95f66bdd13fd57f71823f2d44a28a1323d0d15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596728"
---
# ConvertTo-SecureString

## SYNOPSIS
Convertit des chaînes de texte brut ou chiffrées en chaînes sécurisées.

## SYNTAXE

### Sécurisé (par défaut)

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### Texte brut

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### Ouvrir

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## Description

L' `ConvertTo-SecureString` applet de commande convertit les chaînes standard chiffrées en chaînes sécurisées. Cette commande peut également convertir du texte brut en chaînes sécurisées. Il est utilisé avec `ConvertFrom-SecureString` et `Read-Host` . La chaîne sécurisée créée par l’applet de commande peut être utilisée avec des applets de commande ou des fonctions qui requièrent un paramètre de type **SecureString**. La chaîne sécurisée peut être reconvertie en une chaîne chiffrée standard à l’aide de l’applet de commande `ConvertFrom-SecureString` . Cela permet de la stocker dans un fichier pour une utilisation ultérieure.

Si la chaîne standard en cours de conversion a été chiffrée à `ConvertFrom-SecureString` l’aide d’une clé spécifiée, la même clé doit être fournie comme valeur du paramètre **Key** ou **SecureKey** de l’applet de commande `ConvertTo-SecureString` .

> [!NOTE]
> Notez que, selon [dotnet](/dotnet/api/system.security.securestring#remarks), le contenu d’une SecureString n’est pas chiffré sur les systèmes non-Windows.

## EXEMPLES

### Exemple 1 : convertir une chaîne sécurisée en chaîne chiffrée

Cet exemple montre comment créer une chaîne sécurisée à partir de l'entrée utilisateur, convertir la chaîne sécurisée en chaîne standard chiffrée, puis convertir la chaîne cryptée standard en chaîne sécurisée.

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

La première commande utilise le paramètre **AsSecureString** de l' `Read-Host` applet de commande pour créer une chaîne sécurisée. Une fois que vous avez entré la commande, tous les caractères que vous tapez sont convertis en une chaîne sécurisée, puis enregistrés dans la `$Secure` variable.

La deuxième commande affiche le contenu de la `$Secure` variable. Étant donné que la `$Secure` variable contient une chaîne sécurisée, PowerShell affiche uniquement le type **System. Security. SecureString** .

La troisième commande utilise l' `ConvertFrom-SecureString` applet de commande pour convertir la chaîne sécurisée dans la `$Secure` variable en une chaîne chiffrée standard. Elle enregistre le résultat dans la `$Encrypted` variable.

La quatrième commande affiche la chaîne chiffrée dans la valeur de la `$Encrypted` variable.

La cinquième commande utilise l' `ConvertTo-SecureString` applet de commande pour convertir la chaîne standard chiffrée dans la `$Encrypted` variable en une chaîne sécurisée. Elle enregistre le résultat dans la `$Secure2` variable.
La sixième commande affiche la valeur de la `$Secure2` variable. Le type SecureString indique que la commande a réussi.

### Exemple 2 : créer une chaîne sécurisée à partir d’une chaîne chiffrée dans un fichier

Cet exemple montre comment créer une chaîne sécurisée à partir d'une chaîne chiffrée standard qui est enregistrée dans un fichier.

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

La première commande utilise le paramètre **AsSecureString** de l' `Read-Host` applet de commande pour créer une chaîne sécurisée. Une fois que vous avez entré la commande, tous les caractères que vous tapez sont convertis en une chaîne sécurisée, puis enregistrés dans la `$Secure` variable.

La deuxième commande utilise l' `ConvertFrom-SecureString` applet de commande pour convertir la chaîne sécurisée dans la `$Secure` variable en une chaîne chiffrée standard à l’aide de la clé spécifiée. Le contenu est enregistré dans la `$Encrypted` variable.

La troisième commande utilise un opérateur de pipeline ( `|` ) pour envoyer la valeur de la `$Encrypted` variable à l’applet de commande `Set-Content` , qui enregistre la valeur dans le fichier Encrypted.txt.

La quatrième commande utilise l' `Get-Content` applet de commande pour récupérer la chaîne standard chiffrée dans le fichier Encrypted.txt. La commande utilise un opérateur de pipeline pour envoyer la chaîne chiffrée à l’applet de commande `ConvertTo-SecureString` , qui la convertit en une chaîne sécurisée à l’aide de la clé spécifiée.
Les résultats sont enregistrés dans la `$Secure2` variable.

### Exemple 3 : convertir une chaîne de texte brut en chaîne sécurisée

Cette commande convertit la chaîne de texte brut `P@ssW0rD!` en une chaîne sécurisée et stocke le résultat dans la `$Secure_String_Pwd` variable. Pour utiliser le paramètre **AsPlainText** , le paramètre **force** doit également être inclus dans la commande.

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> Vous devez éviter d’utiliser des chaînes de texte brut dans le script ou à partir de la ligne de commande. Le texte brut peut apparaître dans les journaux des événements et les journaux d’historique des commandes.

## PARAMETERS

### -AsPlainText

Spécifie une chaîne de texte brut à convertir en chaîne sécurisée. Les applets de commande de chaîne sécurisée protègent du texte confidentiel. Le texte est chiffré pour rester confidentiel et il est supprimé de la mémoire de l'ordinateur après son utilisation. Si vous utilisez ce paramètre pour fournir du texte brut en entrée, le système ne peut pas protéger cette entrée de cette manière. Pour utiliser ce paramètre, vous devez également spécifier le paramètre **force** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Confirme que vous comprenez les implications de l’utilisation du paramètre **AsPlainText** et que vous souhaitez quand même l’utiliser.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Key

Spécifie la clé de chiffrement utilisée pour convertir la chaîne sécurisée d’origine dans la chaîne chiffrée standard. Les longueurs de clé valides sont 16, 24 et 32 octets.

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecureKey

Spécifie la clé de chiffrement utilisée pour convertir la chaîne sécurisée d’origine dans la chaîne chiffrée standard. La clé doit être fournie au format d'une chaîne sécurisée. La chaîne sécurisée est convertie en un tableau d’octets à utiliser comme clé. Les longueurs de clé sécurisée valides sont 8, 12 et 16 points de code.

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Chaîne

Spécifie la chaîne à convertir en chaîne sécurisée.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne chiffrée standard vers `ConvertTo-SecureString` .

## SORTIES

### System.Security.SecureString

`ConvertTo-SecureString` retourne un objet **SecureString** .

## REMARQUES

Certains caractères, tels que les émoticônes, correspondent à plusieurs points de code dans la chaîne qui les contient. Évitez d’utiliser ces caractères, car ils peuvent provoquer des problèmes et des malentendus lorsqu’ils sont utilisés dans un mot de passe.

## LIENS CONNEXES

[ConvertFrom-SecureString](ConvertFrom-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)
