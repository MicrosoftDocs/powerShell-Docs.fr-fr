---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: d21765541fb849aed8dc37895c167c0ea34486a3
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692838"
---
# Set-Content

## SYNOPSIS
Écrit un nouveau contenu ou remplace le contenu existant dans un fichier.

## SYNTAXE

### Chemin d’accès (par défaut)

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### LiteralPath

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## Description

`Set-Content` est une applet de commande de traitement de chaîne qui écrit un nouveau contenu ou remplace le contenu d’un fichier. `Set-Content` remplace le contenu existant et diffère de l' `Add-Content` applet de commande qui ajoute le contenu à un fichier. Pour envoyer du contenu à `Set-Content` , vous pouvez utiliser le paramètre **value** sur la ligne de commande ou envoyer le contenu via le pipeline.

Si vous avez besoin de créer des fichiers ou des répertoires pour les exemples suivants, consultez [New-Item](New-Item.md).

## EXEMPLES

### Exemple 1 : remplacer le contenu de plusieurs fichiers dans un répertoire

Cet exemple remplace le contenu de plusieurs fichiers dans le répertoire actif.

```powershell
Get-ChildItem -Path .\Test*.txt
```

```Output
Test1.txt
Test2.txt
Test3.txt
```

```powershell
Set-Content -Path .\Test*.txt -Value 'Hello, World'
Get-Content -Path .\Test*.txt
```

```Output
Hello, World
Hello, World
Hello, World
```

L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour répertorier les fichiers **. txt** qui commencent par `Test*` dans le répertoire actif. L' `Set-Content` applet de commande utilise le paramètre **path** pour spécifier les `Test*.txt` fichiers. Le paramètre **value** fournit la chaîne de texte **Hello, World** qui remplace le contenu existant dans chaque fichier. L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier les `Test*.txt` fichiers et afficher le contenu de chaque fichier dans la console PowerShell.

### Exemple 2 : créer un fichier et écrire du contenu

Cet exemple crée un nouveau fichier et écrit la date et l’heure actuelles dans le fichier.

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

`Set-Content` utilise les paramètres de **chemin d’accès** et de **valeur** pour créer un nouveau fichier nommé **DateTime.txt** dans le répertoire actif. Le paramètre **value** utilise `Get-Date` pour connaître la date et l’heure actuelles.
`Set-Content` écrit l’objet **DateTime** dans le fichier sous la forme d’une chaîne. L' `Get-Content` applet de commande utilise le paramètre **path** pour afficher le contenu de **DateTime.txt** dans la console PowerShell.

### Exemple 3 : remplacer du texte dans un fichier

Cette commande remplace toutes les instances de Word dans un fichier existant.

```powershell
Get-Content -Path .\Notice.txt
```

```Output
Warning
Replace Warning with a new word.
The word Warning was replaced.
```

```powershell
(Get-Content -Path .\Notice.txt) |
    ForEach-Object {$_ -Replace 'Warning', 'Caution'} |
        Set-Content -Path .\Notice.txt
Get-Content -Path .\Notice.txt
```

```Output
Caution
Replace Caution with a new word.
The word Caution was replaced.
```

L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier le fichier **Notice.txt** dans le répertoire actif. La `Get-Content` commande est entourée de parenthèses afin que la commande se termine avant d’être envoyée au pipeline.

Le contenu du fichier **Notice.txt** est envoyé dans le pipeline à l' `ForEach-Object` applet de commande.
`ForEach-Object` utilise la variable automatique `$_` et remplace chaque occurrence de **Warning** par **prudence**. Les objets sont envoyés dans le pipeline à l’applet de commande `Set-Content` . `Set-Content` utilise le paramètre **path** pour spécifier le fichier **Notice.txt** et écrit le contenu mis à jour dans le fichier.

La dernière `Get-Content` applet de commande affiche le contenu du fichier mis à jour dans la console PowerShell.

### Exemple 4 : utiliser des filtres avec Set-Content

Vous pouvez spécifier un filtre pour l' `Set-Content` applet de commande. Lorsque vous utilisez des filtres pour qualifier le paramètre **path** , vous devez inclure un astérisque () de fin `*` pour indiquer le contenu du chemin d’accès.

La commande suivante permet de définir le contenu de tous les `*.txt` fichiers du `C:\Temp` répertoire à la **valeur** vide.

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## PARAMETERS

### -AsByteStream

Spécifie que le contenu doit être lu en tant que flux d’octets. Ce paramètre a été introduit dans PowerShell 6,0.

Un avertissement se produit quand vous utilisez le paramètre **AsByteStream** avec le paramètre **Encoding** . Le paramètre **AsByteStream** ignore tout encodage et la sortie est retournée en tant que flux d’octets.

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

### -Credential

> [!NOTE]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.
> Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

Spécifie le type de codage du fichier cible. La valeur par défaut est `utf8NoBOM`.

Encoding est un paramètre dynamique que le fournisseur FileSystem ajoute à `Set-Content` . Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).
- `bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).
- `bigendianutf32`: Encode au format UTF-32 à l’aide de l’ordre des octets de poids fort (Big-endian).
- `oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.
- `unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).
- `utf7`: Encode au format UTF-7.
- `utf8`: Encode au format UTF-8.
- `utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)
- `utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)
- `utf32`: Encode au format UTF-32.

À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ). Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

> [!NOTE]
> **UTF-7** _ n’est plus recommandé pour l’utilisation de. Dans PowerShell 7,1, un avertissement est écrit si vous spécifiez `utf7` pour le paramètre _ *Encoding**.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path**. Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés. Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Spécifie un filtre pour qualifier le paramètre **path** . Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge l’utilisation de filtres. Vous trouverez la syntaxe de la langue du filtre de **système de fichiers** dans [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).
Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Force l’applet de commande à définir le contenu d’un fichier, même si le fichier est en lecture seule. L'implémentation est différente d'un fournisseur à l'autre. Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).
Le paramètre **force** ne remplace pas les restrictions de sécurité.

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

### -Include

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path**. Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` . Les caractères génériques sont autorisés. Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

Spécifie un chemin d’accès à un ou plusieurs emplacements. La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoNewline

Les représentations sous forme de chaîne des objets d’entrée sont concaténées pour former la sortie. Aucun espace ou saut de chaîne n’est inséré entre les chaînes de sortie. Aucun saut de ligne n’est ajouté après la dernière chaîne de sortie.

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

### -PassThru

Retourne un objet qui représente le contenu. Par défaut, cette applet de commande ne génère aucun résultat.

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

### -Path

Spécifie le chemin d’accès de l’élément qui reçoit le contenu.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Stream

> [!NOTE]
> Ce paramètre est uniquement disponible sur Windows.

Spécifie un flux de données alternatif pour le contenu. Si le flux n’existe pas, cette applet de commande le crée. Les caractères génériques ne sont pas pris en charge.

**Stream** est un paramètre dynamique que le fournisseur **FileSystem** ajoute à `Set-Content` . Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.

Vous pouvez utiliser l' `Set-Content` applet de commande pour créer ou mettre à jour le contenu de tout autre flux de données, tel que `Zone.Identifier` . Toutefois, nous vous déconseillons d’éliminer les contrôles de sécurité qui bloquent les fichiers téléchargés à partir d’Internet. Si vous vérifiez qu’un fichier téléchargé est sûr, utilisez l' `Unblock-File` applet de commande.

Ce paramètre a été introduit dans PowerShell 3,0.

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

### -Value

Spécifie le nouveau contenu pour l'élément.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### System.Object

Vous pouvez diriger un objet qui contient la nouvelle valeur de l’élément vers `Set-Content` .

## SORTIES

### Aucune ou System.String

Quand vous utilisez le paramètre **PassThru** , `Set-Content` génère un objet **System. String** qui représente le contenu. Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

- Vous pouvez également faire référence à `Set-Content` par son alias intégré, `sc` .
  Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- `Set-Content` est conçu pour le traitement des chaînes. Si vous dirigez des objets qui ne sont pas des chaînes vers `Set-Content` , il convertit l’objet en chaîne avant de l’écrire. Pour écrire des objets dans des fichiers, utilisez `Out-File` .
- L' `Set-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Automatic_Variables. MD](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Add-Content](Add-Content.md)

[Clear-Content](Clear-Content.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-Content](Get-Content.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[New-Item](New-Item.md)
