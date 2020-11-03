---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: d4d0b6cf71ac1f856d66639bccd1fce8ab91ccc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204729"
---
# Set-AuthenticodeSignature

## SYNOPSIS
Ajoute une signature [Authenticode](/windows-hardware/drivers/install/authenticode) à un script PowerShell ou à un autre fichier.

## SYNTAX

### ByPath (par défaut)

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByContent

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Set-AuthenticodeSignature` applet de commande ajoute une signature Authenticode à n’importe quel fichier qui prend en charge le package d’interface de sujet (SIP).

Dans un fichier de script PowerShell, la signature prend la forme d’un bloc de texte qui indique la fin des instructions qui sont exécutées dans le script. S'il existe une signature dans le fichier lors de l'exécution de cette applet de commande, cette signature est supprimée.

## EXEMPLES

### Exemple 1 : signer un script à l’aide d’un certificat du magasin de certificats local

Ces commandes récupèrent un certificat de signature de code auprès du fournisseur de certificats PowerShell et l’utilisent pour signer un script PowerShell.

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

La première commande utilise l' `Get-ChildItem` applet de commande et le fournisseur de certificats PowerShell pour récupérer les certificats dans le `Cert:\CurrentUser\My` sous-répertoire du magasin de certificats. Le `Cert:` lecteur est le lecteur exposé par le fournisseur de certificats. Le paramètre **CodeSigningCert** , qui est pris en charge uniquement par le fournisseur de certificats, limite les certificats récupérés à ceux avec l’autorité de signature de code. La commande stocke le résultat dans la `$cert` variable.

La deuxième commande utilise l' `Set-AuthenticodeSignature` applet de commande pour signer le `PSTestInternet2.ps1` script. Elle utilise le paramètre **filePath** pour spécifier le nom du script et le paramètre **Certificate** pour spécifier que le certificat est stocké dans la `$cert` variable.

> [!NOTE]
> L’utilisation du paramètre **CodeSigningCert** avec `Get-ChildItem` renvoie uniquement les certificats qui ont une autorité de signature de code et qui contiennent une clé privée. S’il n’y a pas de clé privée, les certificats ne peuvent pas être utilisés pour la signature.

### Exemple 2 : signer un script à l’aide d’un certificat à partir d’un fichier PFX

Ces commandes utilisent l' `Get-PfxCertificate` applet de commande pour charger un certificat de signature de code. Ensuite, utilisez-le pour signer un script PowerShell.

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

La première commande utilise l' `Get-PfxCertificate` applet de commande pour charger le certificat C:\Test\MySign.pfx dans la `$cert` variable.

La deuxième commande utilise `Set-AuthenticodeSignature` pour signer le script. Le paramètre **filePath** de `Set-AuthenticodeSignature` spécifie le chemin d’accès au fichier de script en cours de signature et le paramètre **CERT** passe la `$cert` variable contenant le certificat à `Set-AuthenticodeSignature` .

Si le fichier de certificat est protégé par un mot de passe, PowerShell vous invite à entrer le mot de passe.

### Exemple 3 : ajouter une signature qui comprend l’autorité racine

Cette commande ajoute une signature numérique qui inclut l'autorité racine dans la chaîne d'approbation, et elle est signée par un serveur d'horodatage tiers.

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

La commande utilise le paramètre **filePath** pour spécifier le script en cours de signature et le paramètre **Certificate** pour spécifier le certificat qui est enregistré dans la `$cert` variable. Elle utilise le paramètre **IncludeChain** pour inclure toutes les signatures dans la chaîne d’approbation, y compris l’autorité racine. Elle utilise également le paramètre **TimeStampServer** pour ajouter un horodatage à la signature.
Cela empêche l'échec du script quand le certificat expire.

## PARAMETERS

### -Certificat

Spécifie le certificat qui sera utilisé pour signer le script ou le fichier. Entrez une variable qui stocke un objet qui représente le certificat ou une expression qui obtient le certificat.

Pour rechercher un certificat, utilisez `Get-PfxCertificate` ou utilisez l' `Get-ChildItem` applet de commande dans le lecteur de certificat `Cert:` . Si le certificat n’est pas valide ou n’a pas d' `code-signing` autorité, la commande échoue.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie le chemin d'accès à un fichier qui est en cours de signature.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

Permet à l'applet de commande d'ajouter une signature à un fichier en lecture seule. Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HashAlgorithm

Spécifie l'algorithme de hachage que Windows utilise pour calculer la signature numérique du fichier.

Pour PowerShell 3,0, la valeur par défaut est SHA256, qui est l’algorithme de hachage par défaut de Windows. Pour PowerShell 2,0, la valeur par défaut est SHA1. Les fichiers qui sont signés avec un algorithme de hachage différent peuvent ne pas être reconnus sur d'autres systèmes. Les algorithmes pris en charge dépendent de la version du système d’exploitation.

Pour obtenir la liste des valeurs possibles, consultez [struct HashAlgorithmName](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeChain

Détermine les certificats de la chaîne d'approbation des certificats qui sont inclus dans la signature numérique.
**NotRoot** est la valeur par défaut.

Les valeurs autorisées sont :

- Signataire : comprend uniquement le certificat du signataire.
- NotRoot : comprend tous les certificats dans la chaîne de certificats, à l’exception de l’autorité racine.
- All : comprend tous les certificats dans la chaîne de certificats.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimestampServer

Utilise le serveur d'horodatage spécifié pour ajouter un horodatage à la signature. Tapez l'URL du serveur d'horodatage sous forme de chaîne.

L'horodatage représente l'heure exacte à laquelle le certificat a été ajouté au fichier. Un horodatage empêche le script d'échouer si le certificat expire, car les utilisateurs et programmes peuvent vérifier que le certificat était valide au moment de la signature.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d'accès à un fichier qui est en cours de signature. Contrairement à **FilePath** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

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

### -SourcePathOrExtension

Chemin du fichier ou type de fichier du contenu pour lequel la signature numérique est ajoutée. Ce paramètre est utilisé avec le **contenu** où le contenu du fichier est passé en tant que tableau d’octets.

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Contenu

Contenu d’un fichier sous la forme d’un tableau d’octets pour lequel la signature numérique est ajoutée. Ce paramètre doit être utilisé avec le paramètre **SourcePathOrExtension** . Le contenu du fichier doit être au format Unicode (UTF-16LE).

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
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

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient le chemin d’accès du fichier vers `Set-AuthenticodeSignature` .

## SORTIES

### System. Management. Automation. signature

## REMARQUES

## LIENS CONNEXES

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Get-PfxCertificate](Get-PfxCertificate.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)
