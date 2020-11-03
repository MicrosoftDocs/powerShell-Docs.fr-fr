---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: 6ddcada506e5bc1ed70615ce32b1481b7d4e9d8b
ms.sourcegitcommit: 33ac34789e86ffb4e7e69453ae38fc0bd24933dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "93206166"
---
# Copy-Item

## SYNOPSIS
Copie un élément d’un emplacement vers un autre.

## SYNTAX

### Chemin d’accès (par défaut)

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### LiteralPath

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## Description

L' `Copy-Item` applet de commande copie un élément d’un emplacement vers un autre dans le même espace de noms.
Par exemple, il peut copier un fichier dans un dossier, mais il ne peut pas copier un fichier vers un lecteur de certificat.

Cette applet de commande ne coupe pas ou ne supprime pas les éléments copiés. Les éléments spécifiques que l’applet de commande peut copier dépendent du fournisseur PowerShell qui expose l’élément. Par exemple, il peut copier des fichiers et des répertoires dans un lecteur du système de fichiers et des clés de Registre et des entrées dans le lecteur du Registre.

Cette applet de commande peut copier et renommer des éléments dans la même commande. Pour renommer un élément, entrez le nouveau nom dans la valeur du paramètre **destination** . Pour renommer un élément sans le copier, utilisez l’applet de commande `Rename-Item` .

## EXEMPLES

### Exemple 1 : copier un fichier dans le répertoire spécifié

Cet exemple copie le `mar1604.log.txt` fichier dans le `C:\Presentation` répertoire. Le fichier d’origine n’est pas supprimé.

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### Exemple 2 : copier le contenu d’un répertoire dans un répertoire existant

Cet exemple copie le contenu du `C:\Logfiles` répertoire dans le répertoire existant `C:\Drawings` . Le `Logfiles` répertoire n’est pas copié.

Si le `Logfiles` répertoire contient des fichiers dans des sous-répertoires, ces derniers sont copiés avec leurs arborescences de fichiers intactes. Par défaut, le paramètre **Container** a la valeur **true** , ce qui permet de conserver la structure de répertoires.

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> Si vous devez inclure le `Logfiles` répertoire dans la copie, supprimez du `\*` chemin d' **accès** .
> Par exemple :
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### Exemple 3 : copier le répertoire et le contenu dans un nouveau répertoire

Cet exemple copie le contenu du `C:\Logfiles` répertoire source et crée un répertoire de destination. Le nouveau répertoire de destination, `\Logs` est créé dans `C:\Drawings` .

Pour inclure le nom du répertoire source, copiez-le dans un répertoire de destination existant, comme indiqué dans l' **exemple 2** . Ou, nommez le nouveau répertoire de destination avec le même nom que le répertoire source.

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> Si le **chemin d’accès** inclut `\*` , tous les contenus du fichier du répertoire, y compris les arborescences de sous-répertoires, sont copiés dans le nouveau répertoire de destination. Par exemple :
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### Exemple 4 : copier un fichier dans le répertoire spécifié et renommer le fichier

Cet exemple utilise l' `Copy-Item` applet de commande pour copier le `Get-Widget.ps1` script du `\\Server01\Share` répertoire vers `\\Server12\ScriptArchive` le répertoire. Dans le cadre de l’opération de copie, la commande remplace le nom d’élément par `Get-Widget.ps1` `Get-Widget.ps1.txt` , afin qu’il puisse être joint à des messages électroniques.

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### Exemple 5 : copier un fichier sur un ordinateur distant

Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .

L' `Copy-Item` applet de `test.log` commande copie le `D:\Folder001` dossier dans le `C:\Folder001_Copy` dossier sur l’ordinateur distant à l’aide des informations de session stockées dans la `$Session` variable. Le fichier d’origine n’est pas supprimé.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### Exemple 6 : copier un dossier sur un ordinateur distant

Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .

L' `Copy-Item` applet de commande copie le `D:\Folder002` dossier dans le `C:\Folder002_Copy` répertoire sur l’ordinateur distant à l’aide des informations de session stockées dans la `$Session` variable. Tous les sous-dossiers ou fichiers ne sont pas copiés sans utiliser le commutateur **recurse** .
L’opération crée le `Folder002_Copy` dossier s’il n’existe pas déjà.

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### Exemple 7 : copier de manière récursive la totalité du contenu d’un dossier sur un ordinateur distant

Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .

L' `Copy-Item` applet de commande copie l’intégralité du contenu du `D:\Folder003` dossier dans le `C:\Folder003_Copy` Répertoire de l’ordinateur distant à l’aide des informations de session stockées dans la `$Session` variable. Les sous-dossiers sont copiés avec leurs arborescences de fichiers intactes. L’opération crée le `Folder003_Copy` dossier s’il n’existe pas déjà.

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### Exemple 8 : copier un fichier sur un ordinateur distant, puis renommer le fichier

Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .

L' `Copy-Item` applet de `scriptingexample.ps1` commande copie le `D:\Folder004` dossier dans le `C:\Folder004_Copy` dossier sur l’ordinateur distant à l’aide des informations de session stockées dans la `$Session` variable. Dans le cadre de l’opération de copie, la commande remplace le nom d’élément par `scriptingexample.ps1` `scriptingexample_copy.ps1` , afin qu’il puisse être joint à des messages électroniques. Le fichier d’origine n’est pas supprimé.

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### Exemple 9 : copier un fichier distant sur l’ordinateur local

Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .

L' `Copy-Item` applet de `test.log` commande copie à partir du `C:\MyRemoteData\` dossier distant vers le `D:\MyLocalData` dossier local à l’aide des informations de session stockées dans la `$Session` variable. Le fichier d’origine n’est pas supprimé.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### Exemple 10 : copier l’intégralité du contenu d’un dossier distant sur l’ordinateur local

Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .

L' `Copy-Item` applet de commande copie l’intégralité du contenu du dossier distant dans `C:\MyRemoteData\scripts` le dossier local à `D:\MyLocalData` l’aide des informations de session stockées dans la `$Session` variable. Si le dossier scripts contient des fichiers dans des sous-dossiers, ceux-ci sont copiés avec leurs arborescences de fichiers intactes.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### Exemple 11 : copier de manière récursive la totalité du contenu d’un dossier distant sur l’ordinateur local

Une session est créée sur l’ordinateur distant nommé **SERVEUR01** avec les informations d’identification de `Contoso\User01` et stocke les résultats dans la variable nommée `$Session` .

L' `Copy-Item` applet de commande copie l’intégralité du contenu du dossier distant dans `C:\MyRemoteData\scripts` le dossier local à `D:\MyLocalData\scripts` l’aide des informations de session stockées dans la `$Session` variable. Étant donné que le paramètre **recurse** est utilisé, l’opération crée le dossier scripts s’il n’existe pas déjà. Si le dossier scripts contient des fichiers dans des sous-dossiers, ceux-ci sont copiés avec leurs arborescences de fichiers intactes.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### Exemple 12 : copier de manière récursive les fichiers d’une arborescence de dossiers dans le dossier actif

Cet exemple montre comment copier des fichiers à partir d’une structure de dossiers à plusieurs niveaux dans un dossier plat unique.
Les trois premières commandes affichent la structure de dossiers existante et le contenu de deux fichiers, les deux noms `file3.txt` .

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

Le `Copy-Item` paramètre **Container** de l’applet de commande est défini sur `$false` . Cela entraîne la copie du contenu du dossier source, mais ne conserve pas la structure de dossiers. Notez que les fichiers portant le même nom sont remplacés dans le dossier de destination.

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

### -Container

Indique que cette applet de commande conserve les objets conteneur pendant l’opération de copie. Par défaut, le paramètre **Container** a la valeur **true** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
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

### -Destination

Spécifie le chemin d'accès au nouvel emplacement. L'emplacement par défaut est le répertoire actif.

Pour renommer l’élément en cours de copie, spécifiez un nouveau nom dans la valeur du paramètre **destination** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut dans l’opération. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés. Le paramètre **Exclude** est effectif uniquement lorsque la commande inclut le contenu d’un élément, tel que `C:\Windows\*` , où le caractère générique spécifie le contenu du `C:\Windows` répertoire.

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
Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils sont récupérés.

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

Indique que cette applet de commande copie des éléments qui ne peuvent pas être modifiés autrement, tels que la copie sur un fichier ou un alias en lecture seule.

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

### -Tosession

Spécifie l’objet **PSSession** à partir duquel un fichier distant est copié. Lorsque vous utilisez ce paramètre, les paramètres **path** et **LiteralPath** font référence au chemin d’accès local sur l’ordinateur distant.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

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

### -PassThru

Retourne un objet qui représente l’élément avec lequel vous travaillez. Par défaut, cette applet de commande ne génère pas de sortie.

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

### -Path

Spécifie, sous forme de tableau de chaînes, le chemin d’accès aux éléments à copier. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Recurse

Indique que cette applet de commande effectue une copie récursive.

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

### -ToSession

Spécifie l’objet **PSSession** dans lequel un fichier distant est copié. Lorsque vous utilisez ce paramètre, le paramètre de **destination** fait référence au chemin d’accès local sur l’ordinateur distant.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
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

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.

## SORTIES

### Aucun ou un objet représentant l’élément copié

Quand vous utilisez le paramètre **PassThru** , cette applet de commande retourne un objet qui représente l’élément copié. Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Clear-Item](Clear-Item.md)

[Get-Item](Get-Item.md)

[Get-PSProvider](Get-PSProvider.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)
