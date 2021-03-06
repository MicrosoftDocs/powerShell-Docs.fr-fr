---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 4bbdab62168a7306bb02d0ac47b5513d23920814
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "93205794"
---
# ConvertFrom-SecureString

## SYNOPSIS
Convertit une chaîne sécurisée en chaîne standard chiffrée.

## SYNTAX

### Sécurisé (par défaut)

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### AsPlainText

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### Ouvrir

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## Description

L’applet de commande **ConvertFrom-SecureString** convertit une chaîne sécurisée ( **System. Security. SecureString** ) en une chaîne chiffrée standard ( **System. String** ). Contrairement à une chaîne sécurisée, une chaîne chiffrée standard peut être enregistrée dans un fichier pour une utilisation ultérieure. La chaîne standard chiffrée peut être reconvertie dans son format de chaîne sécurisée à l’aide de l’applet de commande `ConvertTo-SecureString` .

Si une clé de chiffrement est spécifiée à l'aide des paramètres **Key** ou **SecureKey** , l'algorithme de chiffrement AES (Advanced Encryption Standard) est utilisé. La clé spécifiée doit avoir une longueur égale à 128, 192 ou 256 bits, car ce sont les longueurs de clé prises en charge par l'algorithme de chiffrement AES. Si aucune clé n'est spécifiée, l'API de protection des données (DPAPI) Windows est utilisée pour chiffrer la représentation de chaîne standard.

> [!NOTE]
> Notez que, selon [dotnet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), le contenu d’une SecureString n’est pas chiffré sur les systèmes non-Windows.

## EXEMPLES

### Exemple 1 : créer une chaîne sécurisée

```powershell
$SecureString = Read-Host -AsSecureString
```

Cette commande crée une chaîne sécurisée à partir de caractères que vous tapez à l'invite de commandes. Après avoir entré la commande, tapez la chaîne que vous souhaitez stocker en tant que chaîne sécurisée. Un astérisque ( `*` ) s’affiche pour représenter chaque caractère que vous tapez.

### Exemple 2 : convertir une chaîne sécurisée en chaîne standard chiffrée

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

Cette commande convertit la chaîne sécurisée dans la `$SecureString` variable en une chaîne chiffrée standard. La chaîne standard chiffrée résultante est stockée dans la `$StandardString` variable.

### Exemple 3 : convertir une chaîne sécurisée en chaîne standard chiffrée avec une clé de 192 bits

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

Ces commandes utilisent l’algorithme Advanced Encryption Standard (AES) pour convertir la chaîne sécurisée stockée dans la `$SecureString` variable en chaîne standard chiffrée avec une clé de 192 bits. La chaîne standard chiffrée résultante est stockée dans la `$StandardString` variable.

La première commande stocke une clé dans la `$Key` variable. La clé est un tableau de 24 chiffres décimaux, chacun d’entre eux devant être inférieur à 256 pour tenir dans un seul octet non signé.

Étant donné que chaque chiffre décimal représente un seul octet (8 bits), la clé a 24 chiffres pour un total de 192 bits (8 x 24). Il s'agit d'une longueur de clé valide pour l'algorithme AES.

La deuxième commande utilise la clé de la `$Key` variable pour convertir la chaîne sécurisée en chaîne standard chiffrée.

### Exemple 4 : convertir directement une chaîne sécurisée en une chaîne de texte en clair

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## PARAMETERS

### -AsPlainText

Quand `ConvertFrom-SecureString` elle est définie, elle convertit les chaînes sécurisées en une chaîne de texte en clair déchiffrée en sortie.

Ce paramètre a été ajouté dans PowerShell 7,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsPlainText
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Clé

Spécifie la clé de chiffrement en tant que tableau d'octets.

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

Spécifie la clé de chiffrement en tant que chaîne sécurisée. La valeur de chaîne sécurisée est convertie en un tableau d'octets avant d'être utilisée comme clé.

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

### -SecureString

Spécifie la chaîne sécurisée à convertir en chaîne standard chiffrée.

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .
Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.Security.SecureString

Vous pouvez diriger un objet **SecureString** vers ConvertFrom-SecureString.

## SORTIES

### System.String

ConvertFrom-SecureString retourne un objet chaîne standard.

## REMARQUES

- Pour créer une chaîne sécurisée à partir de caractères tapés à l’invite de commandes, utilisez le paramètre **AsSecureString** de l’applet de commande `Read-Host` .
- Lorsque vous utilisez les paramètres **Key** ou **SecureKey** pour spécifier une clé, la longueur de la clé doit être correcte. Par exemple, une clé de 128 bits peut être spécifiée sous la forme d’un tableau d’octets de 16 chiffres décimaux.
  De même, les clés 192 bits et 256 bits correspondent aux tableaux d’octets de 24 et 32 chiffres décimaux, respectivement.
- Certains caractères, tels que les émoticônes, correspondent à plusieurs points de code dans la chaîne qui les contient. Évitez d’utiliser ces caractères, car ils peuvent provoquer des problèmes et des malentendus lorsqu’ils sont utilisés dans un mot de passe.

## LIENS CONNEXES

[ConvertTo-SecureString](ConvertTo-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)
