---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 916b0ca30240002949b947b857b257214ea9ca1a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204661"
---
# Export-Clixml

## SYNOPSIS
Crée une représentation XML d'un ou plusieurs objets et la stocke dans un fichier.

## SYNTAX

### ByPath (par défaut)

```
Export-Clixml [-Path] <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Clixml -LiteralPath <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Export-Clixml` applet de commande crée une représentation XML Common Language Infrastructure (CLI) d’un ou de tous les objets et le stocke dans un fichier. Vous pouvez ensuite utiliser l' `Import-Clixml` applet de commande pour recréer l’objet enregistré en fonction du contenu de ce fichier.
Pour plus d’informations sur l’interface CLI, consultez [indépendance du langage](/dotnet/standard/language-independence).

Cette applet de commande est semblable à `ConvertTo-Xml` , à ceci près que `Export-Clixml` stocke les données XML résultantes dans un fichier. `ConvertTo-XML` retourne le code XML, ce qui vous permet de continuer à le traiter dans PowerShell.

Une utilisation intéressante de `Export-Clixml` sur les ordinateurs Windows consiste à exporter les informations d’identification et à sécuriser les chaînes en toute sécurité au format XML. Pour obtenir un exemple, consultez l’exemple 3.

## EXEMPLES

### Exemple 1 : exporter une chaîne dans un fichier XML

Cet exemple crée un fichier XML qui stocke dans le répertoire actif, une représentation de la chaîne qu' **il s’agit d’un test** .

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

La chaîne qu' **il s’agit d’un test** est envoyée dans le pipeline. `Export-Clixml` utilise le paramètre **path** pour créer un fichier XML nommé `sample.xml` dans le répertoire actif.

### Exemple 2 : exporter un objet dans un fichier XML

Cet exemple montre comment exporter un objet vers un fichier XML, puis créer un objet en important le contenu XML du fichier.

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

L' `Get-Acl` applet de commande obtient le descripteur de sécurité du `Test.txt` fichier. Il envoie l’objet dans le pipeline pour lui transmettre le descripteur de sécurité `Export-Clixml` . La représentation XML de l’objet est stockée dans un fichier nommé `FileACL.xml` .

L' `Import-Clixml` applet de commande crée un objet à partir du code XML dans le `FileACL.xml` fichier. Ensuite, il enregistre l’objet dans la `$fileacl` variable.

### Exemple 3 : chiffrer un objet d’informations d’identification exporté sur Windows

Dans cet exemple, étant donné les informations d’identification que vous avez stockées dans la `$Credential` variable en exécutant l' `Get-Credential` applet de commande, vous pouvez exécuter l' `Export-Clixml` applet de commande pour enregistrer les informations d’identification sur le disque.

> [!IMPORTANT]
> `Export-Clixml` exporte uniquement les informations d’identification chiffrées sur Windows. Sur les systèmes d’exploitation autres que Windows, tels que macOS et Linux, les informations d’identification sont exportées sous forme de texte brut stocké en tant que tableau de caractères Unicode. Cela fournit un certain brouillage, mais ne fournit pas de chiffrement.

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

L' `Export-Clixml` applet de commande chiffre les objets d’informations d’identification à l’aide de l' [API de protection des données](/previous-versions/windows/apps/hh464970(v=win.10))Windows. Le chiffrement garantit que seul votre compte d’utilisateur sur cet ordinateur peut déchiffrer le contenu de l’objet d’informations d’identification.
Le `CLIXML` fichier exporté ne peut pas être utilisé sur un autre ordinateur ou un autre utilisateur.

Dans l’exemple, le fichier dans lequel les informations d’identification sont stockées est représenté par `TestScript.ps1.credential` . Remplacez **TestScript** par le nom du script avec lequel vous chargez les informations d’identification.

Vous envoyez l’objet d’informations d’identification dans le pipeline à `Export-Clixml` et l’enregistrez dans le chemin d’accès, `$Credxmlpath` , que vous avez spécifié dans la première commande.

Pour importer automatiquement les informations d’identification dans votre script, exécutez les deux commandes finales. Exécutez `Import-Clixml` pour importer l’objet d’informations d’identification sécurisé dans votre script. Cette importation élimine le risque d’exposer les mots de passe en texte brut dans votre script.

### Exemple 4 : exportation d’un objet d’informations d’identification sur Linux ou macOS

Dans cet exemple, nous créons un **PSCredential** dans la `$Credential` variable à l’aide de l’applet de commande `Get-Credential` . Ensuite, nous utilisons `Export-Clixml` pour enregistrer les informations d’identification sur le disque.

> [!IMPORTANT]
> `Export-Clixml` exporte uniquement les informations d’identification chiffrées sur Windows. Sur les systèmes d’exploitation autres que Windows, tels que macOS et Linux, les informations d’identification sont exportées sous forme de texte brut stocké en tant que tableau de caractères Unicode. Cela fournit un certain brouillage, mais ne fournit pas de chiffrement.

```powershell
PS> $Credential = Get-Credential

PowerShell credential request
Enter your credentials.
User: User1
Password for user User1: ********

PS> $Credential | Export-Clixml ./cred2.xml
PS> Get-Content ./cred2.xml

...
    <Props>
      <S N="UserName">User1</S>
      <SS N="Password">700061007300730077006f0072006400</SS>
    </Props>
...

PS> 'password' | Format-Hex -Encoding unicode

                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
0000000000000000 70 00 61 00 73 00 73 00 77 00 6F 00 72 00 64 00 p a s s w o r d
```

La sortie de `Get-Content` dans cet exemple a été tronquée pour se concentrer sur les informations d’identification dans le fichier XML. Notez que la valeur de texte brut du mot de passe est stockée dans le fichier XML sous la forme d’un tableau de caractères Unicode, comme démontré par `Format-Hex` . La valeur est donc encodée, mais pas chiffrée.

## PARAMETERS

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

### -Profondeur

Spécifie le nombre de niveaux d'objets contenus inclus dans la représentation XML. La valeur par défaut est `2`.

La valeur par défaut peut être remplacée par le type d’objet dans les `Types.ps1xml` fichiers. Pour plus d’informations, consultez [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Spécifie le type de codage du fichier cible. La valeur par défaut est `utf8NoBOM`.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).
- `bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).
- `oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.
- `unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).
- `utf7`: Encode au format UTF-7.
- `utf8`: Encode au format UTF-8.
- `utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)
- `utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)
- `utf32`: Encode au format UTF-32.

À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ). Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

Indique à l'applet de commande d'effacer l'attribut de lecture seule du fichier de sortie, si nécessaire. L'applet de commande tente de réinitialiser l'attribut de lecture seule à la fin de l'exécution de la commande.

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

### -InputObject

Spécifie l'objet à convertir. Entrez une variable contenant les objets, ou tapez une commande ou une expression qui obtient ces objets. Vous pouvez également diriger les objets vers `Export-Clixml` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d'accès du fichier où sera stockée la représentation XML de l'objet. Contrairement à **path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Indique que l’applet de commande ne remplace pas le contenu d’un fichier existant. Par défaut, si un fichier existe dans le chemin d’accès spécifié, `Export-Clixml` remplace le fichier sans avertissement.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d'accès du fichier où sera stockée la représentation XML de l'objet.

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

### System. Management. Automation. PSObject

Vous pouvez effectuer un pipeline de n’importe quel objet vers `Export-Clixml` .

## SORTIES

### System. IO. FileInfo

`Export-Clixml` crée un fichier qui contient le XML.

## REMARQUES

## LIENS CONNEXES

[ConvertTo-Html](ConvertTo-Html.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[Export-Csv](Export-Csv.md)

[Import-Clixml](Import-Clixml.md)

[Join-Path](../Microsoft.PowerShell.Management/Join-Path.md)

[Stocker en toute sécurité les informations d’identification sur le disque](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[Utiliser PowerShell pour transmettre des informations d’identification à des systèmes hérités](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[Windows.Security.Cryptography.DataProtection](/uwp/api/windows.security.cryptography.dataprotection)
