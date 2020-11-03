---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: e2b78a2062ac551b76c0a1b6b31d721bfefcf3bd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204022"
---
# Get-Content

## SYNOPSIS
Obtient le contenu de l'élément à l'emplacement spécifié.

## SYNTAX

### Chemin d’accès (par défaut)

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-UseTransaction] [-Delimiter <String>] [-Wait] [-Raw]
 [-Encoding <FileSystemCmdletProviderEncoding>] [-Stream <String>] [<CommonParameters>]
```

### LiteralPath

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-UseTransaction] [-Delimiter <String>] [-Wait] [-Raw]
 [-Encoding <FileSystemCmdletProviderEncoding>] [-Stream <String>] [<CommonParameters>]
```

## Description

L' `Get-Content` applet de commande obtient le contenu de l’élément à l’emplacement spécifié par le chemin d’accès, tel que le texte d’un fichier ou le contenu d’une fonction. Pour les fichiers, le contenu est lu une ligne à la fois et retourne une collection d’objets, chacun d’eux représentant une ligne de contenu.

À compter de PowerShell 3,0, `Get-Content` peut également obtenir un nombre spécifié de lignes à partir du début ou de la fin d’un élément.

## EXEMPLES

### Exemple 1 : obtenir le contenu d’un fichier texte

Cet exemple obtient le contenu d’un fichier dans le répertoire actif. Le `LineNumbers.txt` fichier contient 100 lignes au format, **il s’agit de la ligne X** et est utilisé dans plusieurs exemples.

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

Les valeurs de tableau 1-100 sont envoyées par le pipeline à l’applet de commande `ForEach-Object` . `ForEach-Object` utilise un bloc de script avec l' `Add-Content` applet de commande pour créer le `LineNumbers.txt` fichier. La variable `$_` représente les valeurs de tableau lorsque chaque objet est envoyé vers le pipeline. L' `Get-Content` applet de commande utilise le paramètre **path** pour spécifier le `LineNumbers.txt` fichier et afficher le contenu dans la console PowerShell.

### Exemple 2 : limiter le nombre de lignes retournées par Get-Content

Cette commande obtient les cinq premières lignes d’un fichier. Le paramètre **totalCount** est utilisé pour obtenir les cinq premières lignes de contenu. Cet exemple utilise le `LineNumbers.txt` fichier créé dans l’exemple 1.

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### Exemple 3 : obtenir une ligne spécifique de contenu à partir d’un fichier texte

Cette commande obtient un nombre spécifique de lignes à partir d’un fichier, puis affiche uniquement la dernière ligne de ce contenu. Le paramètre **totalCount** obtient les 25 premières lignes de contenu. Cet exemple utilise le `LineNumbers.txt` fichier créé dans l’exemple 1.

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

La `Get-Content` commande est placée entre parenthèses afin que la commande se termine avant de passer à l’étape suivante. `Get-Content`retourne un tableau de lignes, ce qui vous permet d’ajouter la notation d’index après la parenthèse pour récupérer un numéro de ligne spécifique. Dans ce cas, l' `[-1]` index spécifie le dernier index dans le tableau retourné de 25 lignes récupérées.

### Exemple 4 : obtenir la dernière ligne d’un fichier texte

Cette commande obtient la première ligne et la dernière ligne de contenu à partir d’un fichier. Cet exemple utilise le `LineNumbers.txt` fichier créé dans l’exemple 1.

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

Cet exemple utilise l' `Get-Item` applet de commande pour démontrer que vous pouvez diriger des fichiers vers le `Get-Content` paramètre. Le paramètre **tail** obtient la dernière ligne du fichier. Cette méthode est plus rapide que la récupération de toutes les lignes et l’utilisation de la `[-1]` notation d’index.

### Exemple 5 : récupérer le contenu d’un flux de données de remplacement

Cet exemple décrit comment utiliser le paramètre **Stream** pour obtenir le contenu d’un flux de données de remplacement pour les fichiers stockés sur un volume NTFS Windows. Dans cet exemple, l' `Set-Content` applet de commande est utilisée pour créer un exemple de contenu dans un fichier nommé `Stream.txt` .

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

Le paramètre **Stream** est un paramètre dynamique du [fournisseur FileSystem](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).
Par défaut `Get-Content` , récupère uniquement les données du flux principal ou `$DATA` . Les **flux** peuvent être utilisés pour stocker des données masquées telles que des attributs, des paramètres de sécurité ou d’autres données.

### Exemple 6 : récupérer du contenu brut

Dans cet exemple, les commandes récupèrent le contenu d’un fichier sous la forme d’une chaîne, au lieu d’un tableau de chaînes. Par défaut, sans le paramètre dynamique **RAW** , le contenu est retourné sous la forme d’un tableau de chaînes délimitées par des sauts de ligne. Cet exemple utilise le `LineNumbers.txt` fichier qui a été créé dans l’exemple
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### Exemple 7 : utiliser des filtres avec Get-Content

Vous pouvez spécifier un filtre pour l' `Get-Content` applet de commande. Lorsque vous utilisez des filtres pour qualifier le paramètre **path** , vous devez inclure un astérisque () de fin `*` pour indiquer le contenu du chemin d’accès.

La commande suivante obtient le contenu de tous les `*.log` fichiers du `C:\Temp` répertoire.

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### Exemple 8 : obtenir le contenu d’un fichier sous la forme d’un tableau d’octets

Cet exemple montre comment obtenir le contenu d’un fichier en tant `[byte[]]` qu’objet unique.

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -Encoding Byte -Raw
Get-Member -InputObject $bytearray
```

```Output
   TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

La première commande utilise le paramètre **Encoding** pour récupérer le flux d’octets à partir du fichier.
Le paramètre **RAW** garantit que les octets sont retournés en tant que `[System.Byte[]]` . Si le paramètre **RAW** est absent, la valeur de retour est un flux d’octets, qui est interprété par PowerShell comme `[System.Object[]]` .

## PARAMETERS

### -Path

Spécifie le chemin d’accès à un élément où `Get-Content` obtient le contenu. Les caractères génériques sont autorisés. Les chemins d'accès doivent être ceux des éléments et non des conteneurs. Par exemple, vous devez spécifier un chemin d'accès à un ou plusieurs fichiers et non à un répertoire.

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

### -LiteralPath

Spécifie un chemin d’accès à un ou plusieurs emplacements. La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ReadCount

Spécifie le nombre de lignes de contenu envoyées simultanément via le pipeline. La valeur par défaut est 1.
La valeur 0 (zéro) envoie tout le contenu à la fois.

Ce paramètre ne modifie pas le contenu affiché, mais il affecte le temps requis pour afficher le contenu. À mesure que la valeur de **ReadCount** augmente, le temps nécessaire pour retourner la première ligne augmente, tandis que le temps total requis pour l’opération diminue. Cela peut faire une différence perceptible dans les éléments volumineux.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -TotalCount

Spécifie le nombre de lignes à partir du début d’un fichier ou d’un autre élément. La valeur par défaut est -1 (toutes les lignes).

Vous pouvez utiliser le nom du paramètre **totalCount** ou ses alias, **First** ou **Head** .

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Fin

Spécifie le nombre de lignes à partir de la fin d’un fichier ou d’un autre élément. Vous pouvez utiliser le nom du paramètre de **fin** ou son alias, **Last** . Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
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

### -Include

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `"*.txt"` . Les caractères génériques sont autorisés. Le paramètre **include** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

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

### -Exclude

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération.
La valeur de ce paramètre qualifie le paramètre **Path** .

Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .
Les caractères génériques sont autorisés.

Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

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

### -Force

**Force** remplacera un attribut en lecture seule ou créera des répertoires pour compléter un chemin d’accès de fichier. Le paramètre **force** ne tente pas de modifier les autorisations de fichier ou de remplacer les restrictions de sécurité.

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
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Délimiteur

Spécifie le délimiteur utilisé par `Get-Content` pour diviser le fichier en objets pendant la lecture. La valeur par défaut est `\n` , le caractère de fin de ligne. Lors de la lecture d’un fichier texte, `Get-Content` retourne une collection d’objets String, chacun d’entre eux se terminant par un caractère de fin de ligne. Lorsque vous entrez un délimiteur qui n’existe pas dans le fichier, `Get-Content` retourne la totalité du fichier sous la forme d’un objet unique, non délimité.

Vous pouvez utiliser ce paramètre pour fractionner un fichier volumineux en fichiers plus petits en spécifiant un séparateur de fichiers comme délimiteur. Le délimiteur est conservé (il n'est pas supprimé) et devient le dernier élément de chaque section du fichier.

Le **délimiteur** est un paramètre dynamique que le fournisseur **FileSystem** ajoute à l’applet de commande `Get-Content` . Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.

> [!NOTE]
> Actuellement, lorsque la valeur du paramètre **Delimiter** est une chaîne vide, `Get-Content` ne retourne rien. Il s'agit d'un problème connu. Pour forcer `Get-Content` à retourner la totalité du fichier sous la forme d’une chaîne unique et délimitée. Entrez une valeur qui n’existe pas dans le fichier.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

Conserve le fichier ouvert une fois que toutes les lignes existantes ont été générées. En attente, `Get-Content` vérifie le fichier une fois par seconde et génère de nouvelles lignes le cas échéant. Vous pouvez interrompre l' **attente** en appuyant sur **Ctrl + C** . L’attente se termine également si le fichier est supprimé, auquel cas une erreur sans fin d’achèvement est signalée.

**Wait** est un paramètre dynamique que le fournisseur FileSystem ajoute à l' `Get-Content` applet de commande. Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers. **Wait** ne peut pas être combiné avec **RAW** .

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

### -RAW

Ignore les caractères de saut de ligne et retourne tout le contenu d’un fichier dans une chaîne avec les nouvelles lignes conservées. Par défaut, les caractères de saut de ligne dans un fichier sont utilisés comme délimiteurs pour séparer l’entrée dans un tableau de chaînes. Ce paramètre a été introduit dans PowerShell 3,0.

**RAW** est un paramètre dynamique que le fournisseur **FileSystem** ajoute à l' `Get-Content` applet de commande. ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.

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

### -Encoding

Spécifie le type de codage du fichier cible. La valeur par défaut est `Default`.

Les valeurs acceptables pour ce paramètre sont les suivantes :

- `Ascii` Utilise le jeu de caractères ASCII (7 bits).
- `BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).
- `BigEndianUTF32` Utilise UTF-32 avec l’ordre des octets de poids fort (Big-endian).
- `Byte` Encode un jeu de caractères en une séquence d’octets.
- `Default` Utilise l’encodage qui correspond à la page de codes active du système (généralement ANSI).
- `Oem` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.
- `String` Identique à `Unicode`.
- `Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).
- `Unknown` Identique à `Unicode`.
- `UTF7` Utilise UTF-7.
- `UTF8` Utilise UTF-8.
- `UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).

L’encodage est un paramètre dynamique que le fournisseur **FileSystem** ajoute à l’applet de commande `Get-Content` .
Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers.

Lors de la lecture et de l’écriture dans des fichiers binaires, utilisez la valeur **Byte** pour le paramètre dynamique **Encoding** et la valeur 0 pour le paramètre **readCount** . Une valeur **readCount** de 0 lit le fichier entier en une seule opération de lecture et le convertit en un seul objet (PSObject). La valeur **readCount** par défaut, 1, lit un octet dans chaque opération de lecture et convertit chaque octet en un objet distinct, ce qui provoque des erreurs quand vous utilisez l' `Set-Content` applet de commande pour écrire les octets dans un fichier.

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stream

Obtient le contenu du flux de fichiers NTFS alternatif spécifié du fichier. Entrez le nom du flux.
Les caractères génériques ne sont pas pris en charge.

**Stream** est un paramètre dynamique que le fournisseur **FileSystem** ajoute à l' `Get-Content` applet de commande.
Ce paramètre fonctionne uniquement dans les lecteurs du système de fichiers sur les systèmes Windows. Ce paramètre a été introduit dans Windows PowerShell 3.0.

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

### -UseTransaction

Inclut la commande dans la transaction active. Ce paramètre est uniquement valide au cours d’une transaction. Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.Int64, System.String[], System.Management.Automation.PSCredential

Vous pouvez diriger le nombre de lectures, le nombre total, les chemins d’accès ou les informations d’identification vers `Get-Content` .

## SORTIES

### System. Byte, System. String

`Get-Content` retourne des chaînes ou des octets. Le type de sortie dépend du type de contenu que vous spécifiez en tant qu’entrée.

## REMARQUES

L' `Get-Content` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour récupérer les fournisseurs dans votre session, utilisez l' `Get-PSProvider` applet de commande. Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Add-Content](Add-Content.md)

[Clear-Content](Clear-Content.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-PSProvider](Get-PSProvider.md)

[Set-Content](Set-Content.md)
