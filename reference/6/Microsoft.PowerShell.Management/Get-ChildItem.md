---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: 14b1c5d0f37301a5312f37a115f0abc1c7b5990e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204461"
---
# Get-ChildItem

## SYNOPSIS

Obtient les éléments et les éléments enfants dans un ou plusieurs emplacements spécifiés

## SYNTAX

### Items (valeur par défaut)

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### LiteralItems

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## Description

L' `Get-ChildItem` applet de commande obtient les éléments dans un ou plusieurs emplacements spécifiés. Si l’élément est un conteneur, elle obtient les éléments qui se trouvent à l’intérieur du conteneur, appelés éléments enfants. Vous pouvez utiliser le paramètre **recurse** pour récupérer des éléments dans tous les conteneurs enfants et utiliser le paramètre **Depth** pour limiter le nombre de niveaux à recurse.

`Get-ChildItem` n’affiche pas les répertoires vides. Lorsqu’une `Get-ChildItem` commande inclut les paramètres **Depth** ou **recurse** , les répertoires vides ne sont pas inclus dans la sortie.

Les emplacements sont exposés aux `Get-ChildItem` fournisseurs PowerShell. Un emplacement peut être un répertoire du système de fichiers, une ruche du registre ou un magasin de certificats. Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## EXEMPLES

### Exemple 1 : obtenir des éléments enfants à partir d’un répertoire de système de fichiers

Cet exemple obtient les éléments enfants d’un répertoire de système de fichiers. Les noms de fichiers et de sous-répertoires sont affichés. Pour les emplacements vides, la commande ne retourne aucune sortie et retourne à l’invite de commandes PowerShell.

L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le répertoire `C:\Test` .
`Get-ChildItem` affiche les fichiers et les répertoires dans la console PowerShell.

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

Par défaut `Get-ChildItem` répertorie le mode ( **attributs** ), **LastWriteTime** , la taille de fichier ( **longueur** ) et le **nom** de l’élément. Les lettres de la propriété **mode** peuvent être interprétées comme suit :

- `l` lien
- `d` Directory
- `a` archiver
- `r` (lecture seule)
- `h` masquer
- `s` (système).

Pour plus d’informations sur les indicateurs de mode, consultez [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression).

### Exemple 2 : obtenir les noms des éléments enfants dans un répertoire

Cet exemple répertorie uniquement les noms des éléments d’un répertoire.

L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le répertoire `C:\Test` . Le paramètre **Name** retourne uniquement les noms de fichiers ou de répertoires à partir du chemin d’accès spécifié.

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### Exemple 3 : récupérer des éléments enfants dans le répertoire et les sous-répertoires actifs

Cet exemple affiche les fichiers **. txt** qui se trouvent dans le répertoire actif et ses sous-répertoires.

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier `C:\Test\*.txt` . **Path** utilise le `*` caractère générique astérisque () pour spécifier tous les fichiers avec l’extension de nom de fichier `.txt` . Le paramètre **recurse** recherche dans le répertoire du **chemin d’accès** ses sous-répertoires, comme indiqué dans les en-têtes **Directory :** . Le paramètre **force** affiche les fichiers masqués, tels que, `hiddenfile.txt` qui ont le mode **h** .

### Exemple 4 : récupérer des éléments enfants à l’aide du paramètre include

Dans cet exemple, `Get-ChildItem` le paramètre **include** est utilisé pour rechercher des éléments spécifiques dans le répertoire spécifié par le paramètre **path** .

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le répertoire **C:\test** . Le paramètre **path** contient un caractère générique d’astérisque ( `*` ) de fin pour spécifier le contenu du répertoire.
Le paramètre **include** utilise un `*` caractère générique astérisque () pour spécifier tous les fichiers portant l’extension de nom de fichier **. txt** .

Lorsque le paramètre **include** est utilisé, le paramètre **path** a besoin d’un caractère générique astérisque ( `*` ) de fin pour spécifier le contenu du répertoire. Par exemple : `-Path C:\Test\*`.

- Si le paramètre **recurse** est ajouté à la commande, l’astérisque ( `*` ) de fin dans le paramètre **path** est facultatif. Le paramètre **recurse** obtient les éléments du répertoire du **chemin d’accès** et de ses sous-répertoires. Par exemple : `-Path C:\Test\ -Recurse -Include *.txt`
- Si un astérisque () de fin `*` n’est pas inclus dans le paramètre **path** , la commande ne retourne aucune sortie et retourne à l’invite PowerShell. Par exemple : `-Path C:\Test\`.

### Exemple 5 : récupérer des éléments enfants à l’aide du paramètre Exclude

La sortie de l’exemple affiche le contenu du répertoire **C:\Test\Logs** . La sortie est une référence pour les autres commandes qui utilisent les paramètres **Exclude** et **recurse** .

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le répertoire `C:\Test\Logs` .
Le paramètre **Exclude** utilise le `*` caractère générique astérisque () pour spécifier tous les fichiers ou répertoires qui commencent par **un** ou **un** sont exclus de la sortie.

Lorsque le paramètre **Exclude** est utilisé, un astérisque ( `*` ) de fin dans le paramètre **path** est facultatif. Par exemple, `-Path C:\Test\Logs` ou `-Path C:\Test\Logs\*`.

- Si un astérisque () de fin `*` n’est pas inclus dans le paramètre **path** , le contenu du paramètre **path** est affiché. Les noms de fichiers ou de sous-répertoires qui correspondent à la valeur du paramètre **Exclude** sont des exceptions.
- Si un astérisque () de fin `*` est inclus dans le paramètre **path** , la commande parcourt les sous-répertoires du paramètre **path** . Les noms de fichiers ou de sous-répertoires qui correspondent à la valeur du paramètre **Exclude** sont des exceptions.
- Si le paramètre **recurse** est ajouté à la commande, la sortie de récursivité est la même que le paramètre **path** inclue ou non un astérisque de fin ( `*` ).

### Exemple 6 : obtenir les clés de Registre à partir d’une ruche du Registre

Cet exemple obtient toutes les clés de Registre à partir de `HKEY_LOCAL_MACHINE\HARDWARE` .

`Get-ChildItem` utilise le paramètre **path** pour spécifier la clé de Registre `HKLM:\HARDWARE` . Le chemin d’accès et le niveau supérieur des clés de registre de la ruche s’affichent dans la console PowerShell.

Pour plus d’informations, consultez [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md).

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

La première commande affiche le contenu de la `HKLM:\HARDWARE` clé de registre. Le paramètre **Exclude** indique `Get-ChildItem` à de ne pas retourner les sous-clés qui commencent par `D*` . Actuellement, le paramètre **Exclude** ne fonctionne que sur les sous-clés, et non sur les propriétés Item.

### Exemple 7 : récupération de tous les certificats avec l’autorité de signature de code

Cet exemple obtient chaque certificat dans le lecteur du certificat PowerShell **:** qui dispose de l’autorité de signature de code.

L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier le fournisseur **CERT :** . Le paramètre **recurse** recherche le répertoire spécifié par le **chemin d’accès** et ses sous-répertoires. Le paramètre **CodeSigningCert** obtient uniquement les certificats qui ont une autorité de signature de code.

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

Pour plus d’informations sur le fournisseur de certificats et le lecteur Cert :, consultez [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).

### Exemple 8 : récupérer des éléments à l’aide du paramètre DEPTH

Cet exemple affiche les éléments d’un répertoire et de ses sous-répertoires. Le paramètre **Depth** détermine le nombre de niveaux de sous-répertoires à inclure dans la récursivité. Les répertoires vides sont exclus de la sortie.

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

L' `Get-ChildItem` applet de commande utilise le paramètre **path** pour spécifier **C:\Parent** . Le paramètre **Depth** spécifie deux niveaux de récursivité. `Get-ChildItem` affiche le contenu du répertoire spécifié par le paramètre **path** et les deux niveaux des sous-répertoires.

### Exemple 9 : obtention d’informations sur les liens physiques

Dans PowerShell 6,2, une autre vue a été ajoutée pour obtenir des informations sur les liens physiques.

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

## Paramètres

### -Attributs

Obtient les fichiers et les dossiers avec les attributs spécifiés. Ce paramètre prend en charge tous les attributs et vous permet de spécifier des combinaisons complexes d'attributs.

Par exemple, pour obtenir les fichiers non-système (pas les répertoires) qui sont chiffrés ou compressés, tapez :

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

Pour rechercher des fichiers et des dossiers avec des attributs couramment utilisés, utilisez le paramètre **attributes** . Ou, le **répertoire** de paramètres, **file** , **Hidden** , **ReadOnly** et **System** .

Le paramètre **attributes** prend en charge les propriétés suivantes :

- **Archive**
- **Compressed**
- **Appareil**
- **Directory**
- **Chiffré**
- **Hidden**
- **IntegrityStream**
- **Normal**
- **NoScrubData**
- **NotContentIndexed**
- **Hors connexion**
- **Lecture seule**
- **ReparsePoint**
- **SparseFile**
- **Système**
- **Temporaire**

Pour obtenir une description de ces attributs, consultez l' [énumération FileAttributes](/dotnet/api/system.io.fileattributes).

Pour combiner des attributs, utilisez les opérateurs suivants :

- `!` PAS
- `+` LES
- `,` NI

N’utilisez pas d’espaces entre un opérateur et son attribut. Les espaces sont acceptés après les virgules.

Pour les attributs courants, utilisez les abréviations suivantes :

- `D` Directory
- `H` Masquer
- `R` (Lecture seule)
- `S` Requise

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Profondeur

Ce paramètre a été ajouté dans PowerShell 5,0 et vous permet de contrôler la profondeur de récurrence. Par défaut, `Get-ChildItem` affiche le contenu du répertoire parent. Le paramètre **Depth** détermine le nombre de niveaux de sous-répertoires qui sont inclus dans la récursivité et affiche le contenu.

Par exemple, `Depth 2` comprend le répertoire du paramètre **path** , le premier niveau de sous-répertoires et le second niveau de sous-répertoires. Par défaut, les noms de répertoires et les noms de fichiers sont inclus dans la sortie.

> [!NOTE]
> Sur un ordinateur Windows à partir de PowerShell ou **cmd.exe** , vous pouvez afficher une vue graphique d’une structure de répertoires à l’aide de la commande **Tree.com** .

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Répertoire

Pour obtenir la liste des répertoires, utilisez le paramètre **Directory** ou le paramètre **attributes** avec la propriété **Directory** . Vous pouvez utiliser le paramètre **recurse** avec le **répertoire** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

Spécifie, sous la forme d’un tableau de chaînes, une propriété ou une propriété que cette applet de commande exclut de l’opération.
La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` ou `A*` . Les caractères génériques sont acceptés.

Un astérisque ( `*` ) de fin dans le paramètre **path** est facultatif. Par exemple, `-Path C:\Test\Logs` ou `-Path C:\Test\Logs\*`. Si un astérisque () de fin `*` est inclus, la commande parcourt les sous-répertoires du paramètre **path** . Sans l’astérisque ( `*` ), le contenu du paramètre **path** est affiché. Plus de détails sont inclus dans l’exemple 5 et la section Remarques.

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

### -File

Pour obtenir la liste des fichiers, utilisez le paramètre **file** . Vous pouvez utiliser le paramètre **recurse** avec le **fichier** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Spécifie un filtre pour qualifier le paramètre **path** . Le fournisseur [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) est le seul fournisseur PowerShell installé qui prend en charge les filtres. Les filtres sont plus efficaces que les autres paramètres. Le fournisseur applique le filtre lorsque l’applet de commande obtient les objets au lieu d’avoir PowerShell de filtrer les objets une fois qu’ils sont récupérés. La chaîne de filtrage est transmise à l’API .NET pour énumérer les fichiers. L’API prend en charge uniquement les `*` `?` caractères génériques et.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -FollowSymlink

Par défaut, l' `Get-ChildItem` applet de commande affiche des liens symboliques vers les répertoires trouvés lors de la récursivité, mais ne les recurset pas. Utilisez le paramètre **FollowSymlink** pour rechercher dans les répertoires qui ciblent ces liens symboliques. **FollowSymlink** est un paramètre dynamique qui est pris en charge uniquement dans le fournisseur **FileSystem** .

Ce paramètre a été introduit dans PowerShell 6,0.

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

### -Force

Permet à l’applet de commande d’extraire des éléments qui ne sont pas accessibles par l’utilisateur, tels que des fichiers cachés ou système. Le paramètre **force** ne remplace pas les restrictions de sécurité. L’implémentation est différente d’un fournisseur à l’autre. Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

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

### -Hidden

Pour récupérer uniquement les éléments masqués, utilisez le paramètre **Hidden** ou le paramètre **attributes** avec la propriété **Hidden** . Par défaut, `Get-ChildItem` n’affiche pas les éléments masqués. Utilisez le paramètre **force** pour récupérer les éléments masqués.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
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

### -LiteralPath

Spécifie un chemin d’accès à un ou plusieurs emplacements. La valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell de ne pas interpréter les caractères comme des séquences d’échappement.

Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Obtient uniquement les noms des éléments de l’emplacement. La sortie est un objet String qui peut être envoyé vers d’autres commandes via le pipeline. Les caractères génériques sont autorisés.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

Spécifie un chemin d’accès à un ou plusieurs emplacements. Les caractères génériques sont acceptés. L’emplacement par défaut est le répertoire actif ( `.` ).

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -ReadOnly

Pour obtenir uniquement les éléments en lecture seule, utilisez le paramètre **ReadOnly** ou la propriété **ReadOnly** du paramètre **attributes** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Recurse

Obtient les éléments aux emplacements spécifiés, de même que dans tous les éléments enfants de ces emplacements.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -System

Obtient uniquement les fichiers et répertoires système. Pour récupérer uniquement les fichiers et dossiers système, utilisez la propriété **système** du paramètre **System** ou du paramètre **attributes** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

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

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Get-ChildItem` .

## SORTIES

### System.Object

Le type d’objet `Get-ChildItem` retourné est déterminé par les objets figurant dans le chemin d’accès du lecteur du fournisseur.

### System.String

Si vous utilisez le paramètre **Name** , `Get-ChildItem` retourne les noms d’objets sous forme de chaînes.

## REMARQUES

- `Get-ChildItem` peut être exécuté à l’aide de l’un des alias intégrés, `ls` , `dir` et `gci` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- `Get-ChildItem` n’obtient pas les éléments masqués par défaut. Pour obtenir des éléments cachés, utilisez le paramètre **Force** .
- L' `Get-ChildItem` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .
  Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-Alias](../Microsoft.PowerShell.Utility/Get-Alias.md)

[Get-Item](Get-Item.md)

[Get-Location](Get-Location.md)

[Get-Process](Get-Process.md)

[Get-PSProvider](Get-PSProvider.md)

[Split-Path](Split-Path.md)
