---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-7.x&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: 63d979f1d48da4805111b77c5d1c68d7fc4d0fac
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201894"
---
# Unprotect-CmsMessage

## SYNOPSIS
Déchiffre le contenu qui a été chiffré à l’aide du format de syntaxe de message de chiffrement.

## SYNTAX

### ByWinEvent (par défaut)

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### ByContent

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### ByPath

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## Description

L' `Unprotect-CmsMessage` applet de commande déchiffre le contenu qui a été chiffré à l’aide du format CMS (Cryptographic Message Syntax).

Les applets de commande CMS prennent en charge le chiffrement et le déchiffrement de contenu à l’aide du format standard IETF pour la protection par chiffrement des messages, comme indiqué par [RFC5652](https://tools.ietf.org/html/rfc5652).

La norme de chiffrement CMS utilise le chiffrement à clé publique, où les clés utilisées pour chiffrer le contenu (la clé publique) et les clés utilisées pour déchiffrer le contenu (la clé privée) sont distinctes. Votre clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles. Si du contenu est chiffré avec cette clé publique, seule votre clé privée peut le déchiffrer. Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).

`Unprotect-CmsMessage` déchiffre le contenu qui a été chiffré au format CMS. Vous pouvez exécuter cette applet de commande pour déchiffrer le contenu que vous avez chiffré en exécutant l’applet de commande `Protect-CmsMessage` . Vous pouvez spécifier le contenu que vous souhaitez déchiffrer sous forme de chaîne, le numéro d’ID d’enregistrement du journal des événements de chiffrement ou le chemin d’accès au contenu chiffré. L' `Unprotect-CmsMessage` applet de commande retourne le contenu déchiffré.

> [!NOTE]
> Cette applet de commande est disponible uniquement sur Windows.

## EXEMPLES

### Exemple 1 : déchiffrer un message

Dans l’exemple suivant, vous déchiffrez le contenu qui se trouve dans le chemin d’accès littéral `C:\Users\Test\Documents\PowerShell` . Pour la valeur du paramètre requis **pour** , cet exemple utilise l’empreinte numérique du certificat qui a été utilisé pour effectuer le chiffrement. Le message déchiffré « essayez la nouvelle commande Break All » est le résultat.

```powershell
$parameters = @{
  LiteralPath = "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
  To = '0f 8j b1 ab e0 ce 35 1d 67 d2 f2 6f a2 d2 00 cl 22 z9 m9 85'
}
Unprotect-CmsMessage -LiteralPath @parameters
```

```Output
Try the new Break All command
```

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
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -EventLogRecord

Spécifie un ID d’enregistrement de journal des événements qui représente une opération de chiffrement CMS.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByWinEvent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -IncludeContext

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

### -LiteralPath

Spécifie le chemin d’accès au contenu chiffré que vous souhaitez déchiffrer. Contrairement au paramètre **Path** , la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n'est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 0
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
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -To

Spécifie un ou plusieurs destinataires de message CMS, identifiés dans l’un des formats suivants :

- Un certificat réel (tel que récupéré auprès du fournisseur de certificats).
- Chemin d’accès au fichier contenant le certificat.
- Chemin d’accès à un répertoire contenant le certificat.
- Empreinte numérique du certificat (utilisé pour rechercher dans le magasin de certificats).
- Nom du sujet du certificat (utilisé pour rechercher dans le magasin de certificats).

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Diagnostics. Eventing. Reader. EventLogRecord ou System. String

Vous pouvez diriger un objet contenant du contenu chiffré vers `Unprotect-CmsMessage` .

## SORTIES

### System.String

Message non chiffré.

## REMARQUES

## LIENS CONNEXES

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Protect-CmsMessage](Protect-CmsMessage.md)
