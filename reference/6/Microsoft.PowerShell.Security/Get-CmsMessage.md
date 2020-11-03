---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: 30e70549b648f7fb63bb250744cf52f0979c201f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203781"
---
# Get-CmsMessage

## SYNOPSIS
Obtient le contenu qui a été chiffré à l’aide du format de syntaxe de message de chiffrement.

## SYNTAX

### ByContent

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### ByPath

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### ByLiteralPath

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## Description

L' `Get-CmsMessage` applet de commande obtient le contenu qui a été chiffré à l’aide du format CMS (Cryptographic Message Syntax).

Les applets de commande CMS prennent en charge le chiffrement et le déchiffrement de contenu à l’aide du format IETF pour la protection par chiffrement des messages, comme indiqué par [RFC5652](https://tools.ietf.org/html/rfc5652).

La norme de chiffrement CMS utilise le chiffrement à clé publique, où les clés utilisées pour chiffrer le contenu (la clé publique) et les clés utilisées pour déchiffrer le contenu (la clé privée) sont distinctes. Votre clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles. Si du contenu est chiffré avec cette clé publique, seule votre clé privée peut le déchiffrer. Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).

`Get-CmsMessage` Obtient le contenu qui a été chiffré au format CMS. Il ne déchiffre pas ou n’annule pas la protection du contenu. Vous pouvez exécuter cette applet de commande pour obtenir le contenu que vous avez chiffré en exécutant l’applet de commande `Protect-CmsMessage` . Vous pouvez spécifier le contenu que vous souhaitez déchiffrer sous forme de chaîne ou le chemin d’accès au contenu chiffré. Vous pouvez diriger les résultats de `Get-CmsMessage` vers pour `Unprotect-CmsMessage` déchiffrer le contenu, à condition que vous disposiez d’informations sur le certificat de chiffrement de document qui a été utilisé pour chiffrer le contenu.

> [!NOTE]
> Cette applet de commande est disponible uniquement sur Windows.

## EXEMPLES

### Exemple 1 : recevoir du contenu chiffré

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg.Content
```

```Output
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMBFWxlZWhv
bG1AbGljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYP5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNXmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPRwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84AHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1AtDj7nSJc=
-----END CMS-----
```

Cette commande obtient le contenu chiffré situé dans C:\Users\Test\Documents\PowerShell\Future_Plans.txt.

### Exemple 2 : contenu chiffré de canal à Unprotect-CmsMessage

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

Cette commande envoie les résultats de l' `Get-CmsMessage` applet de commande de l’exemple 1 à `Unprotect-CmsMessage` , pour déchiffrer le message et le lire en texte brut. Dans ce cas, la valeur du paramètre **to** est la valeur de la ligne subject du certificat de chiffrement. Le message déchiffré « essayez la nouvelle commande Break All » est le résultat.

## PARAMETERS

### -Contenu

Spécifie une chaîne chiffrée ou une variable contenant une chaîne chiffrée.

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d’accès au contenu chiffré que vous souhaitez obtenir. Contrairement au paramètre **Path** , la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n'est interprété en tant que caractère générique. Si le chemin d’accès comprend des caractères d’échappement, mettez-les entre guillemets simples.
Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères entourés comme des caractères d’échappement.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès au contenu chiffré que vous souhaitez déchiffrer.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

## REMARQUES

## LIENS CONNEXES

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Protect-CmsMessage](Protect-CmsMessage.md)

[Unprotect-CmsMessage](Unprotect-CmsMessage.md)
