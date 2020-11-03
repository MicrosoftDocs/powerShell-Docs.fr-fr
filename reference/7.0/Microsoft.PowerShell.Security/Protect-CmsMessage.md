---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: bca0f75ac371fe18d5a35f5c57572f415922d890
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201373"
---
# Protect-CmsMessage

## SYNOPSIS
Chiffre le contenu à l’aide du format de syntaxe de message de chiffrement.

## SYNTAX

### ByContent (par défaut)

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### ByPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### ByLiteralPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## Description

L' `Protect-CmsMessage` applet de commande chiffre le contenu à l’aide du format CMS (Cryptographic Message Syntax).

Les applets de commande CMS prennent en charge le chiffrement et le déchiffrement de contenu à l’aide du format IETF, comme documenté par [RFC5652](https://tools.ietf.org/html/rfc5652.html).

La norme de chiffrement CMS utilise le chiffrement à clé publique, où les clés utilisées pour chiffrer le contenu (la clé publique) et les clés utilisées pour déchiffrer le contenu (la clé privée) sont distinctes. Votre clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles. Si du contenu est chiffré avec cette clé publique, seule votre clé privée peut le déchiffrer. Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).

Avant de pouvoir exécuter l' `Protect-CmsMessage` applet de commande, vous devez disposer d’un certificat de chiffrement configuré.
Pour être reconnus dans PowerShell, les certificats de chiffrement requièrent un ID d’utilisation[améliorée](/windows/desktop/SecCrypto/eku)de la clé unique pour les identifier en tant que certificats de chiffrement de données (tels que les ID pour la signature de code et le courrier chiffré). Pour obtenir un exemple de certificat qui fonctionnerait pour le chiffrement de document, consultez l’exemple 1 de cette rubrique.

> [!NOTE]
> Cette applet de commande est disponible uniquement sur Windows.

## EXEMPLES

### Exemple 1 : créer un certificat pour le chiffrement du contenu

Avant de pouvoir exécuter l' `Protect-CmsMessage` applet de commande, vous devez créer un certificat de chiffrement. À l’aide du texte suivant, remplacez le nom de la ligne d’objet par votre nom, votre adresse de messagerie ou tout autre identificateur, puis enregistrez le certificat dans un fichier (tel que `DocumentEncryption.inf` , comme illustré dans cet exemple).

```powershell
# Create .INF file for certreq
{[Version]
Signature = "$Windows NT$"

[Strings]
szOID_ENHANCED_KEY_USAGE = "2.5.29.37"
szOID_DOCUMENT_ENCRYPTION = "1.3.6.1.4.1.311.80.1"

[NewRequest]
Subject = "cn=youralias@emailaddress.com"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT_KEY_ENCIPHERMENT_KEY_USAGE | CERT_DATA_ENCIPHERMENT_KEY_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"

[Extensions]
%szOID_ENHANCED_KEY_USAGE% = "{text}%szOID_DOCUMENT_ENCRYPTION%"
} | Out-File -FilePath DocumentEncryption.inf

# After you have created your certificate file, run the following command to add
# the certificate file to the certificate store. Now you are ready to encrypt and
# decrypt content with the next two examples.
certreq.exe -new DocumentEncryption.inf DocumentEncryption.cer
```

### Exemple 2 : chiffrer un message envoyé par courrier électronique

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

Dans l’exemple suivant, vous chiffrez un message, « Hello World », en le canalisant vers l’applet de commande, puis vous `Protect-CmsMessage` Enregistrez le message chiffré dans une variable. Le paramètre **to** utilise la valeur de la ligne d’objet dans le certificat.

### Exemple 3 : afficher les certificats de chiffrement de document

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

Pour afficher les certificats de chiffrement de document dans le fournisseur de certificats, vous pouvez ajouter le paramètre dynamique **DocumentEncryptionCert** de l’opérateur [« obtenir-ChildItem »](../Microsoft.PowerShell.Management/Get-ChildItem.md), disponible uniquement lorsque le fournisseur de certificats est chargé.

## PARAMETERS

### -Contenu

Spécifie un **PSObject** qui contient le contenu que vous souhaitez chiffrer. Par exemple, vous pouvez chiffrer le contenu d’un message d’événement, puis utiliser la variable contenant le message ( `$Event` , dans cet exemple) comme valeur du paramètre de **contenu** : `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` . Vous pouvez également utiliser l' `Get-Content` applet de commande pour obtenir le contenu d’un fichier, tel qu’un document Microsoft Word, et enregistrer le contenu dans une variable que vous utilisez comme valeur du paramètre de **contenu** .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByContent
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d’accès au contenu que vous souhaitez chiffrer. Contrairement au paramètre **Path** , la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

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

### -Fichier de journal

Spécifie le chemin d’accès et le nom de fichier d’un fichier auquel vous souhaitez envoyer le contenu chiffré.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès au contenu que vous souhaitez chiffrer.

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

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

## SORTIES

## REMARQUES

## LIENS CONNEXES

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Unprotect-CmsMessage](Unprotect-CmsMessage.md)
