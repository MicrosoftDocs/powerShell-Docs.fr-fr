---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: 4c247513ab06f1bcba648a62969fb7d458e0d35d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598357"
---
# New-Item

## SYNOPSIS
Crée un élément.

## SYNTAXE

### pathSet (par défaut)

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### nameSet

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `New-Item` applet de commande crée un nouvel élément et définit sa valeur. Les types d’éléments qui peuvent être créés dépendent de l’emplacement de l’élément. Par exemple, dans le système de fichiers, `New-Item` crée des fichiers et des dossiers. Dans le registre, `New-Item` crée des clés et des entrées de registre.

`New-Item` peut également définir la valeur des éléments qu’elle crée. Par exemple, lorsqu’il crée un nouveau fichier, `New-Item` peut ajouter le contenu initial au fichier.

## EXEMPLES

### Exemple 1 : créer un fichier dans le répertoire actif

Cette commande crée un fichier texte nommé « testfile1.txt » dans le répertoire actif. Le point ('. ') dans la valeur du paramètre **path** indique le répertoire actif. Le texte entre guillemets qui suit le paramètre **value** est ajouté au fichier en tant que contenu.

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### Exemple 2 : créer un répertoire

Cette commande crée un répertoire nommé « LogFiles » dans le `C:` lecteur. Le paramètre **ItemType** spécifie que le nouvel élément est un répertoire, et non un fichier ou un autre objet de système de fichiers.

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### Exemple 3 : créer un profil

Cette commande crée un profil PowerShell dans le chemin d’accès spécifié par la `$profile` variable.

Vous pouvez utiliser des profils pour personnaliser PowerShell. `$profile` est une variable automatique (intégrée) qui stocke le chemin d’accès et le nom de fichier du profil « CurrentUser/CurrentHost ». Par défaut, le profil n’existe pas, même si PowerShell stocke un chemin d’accès et un nom de fichier pour celui-ci.

Dans cette commande, la `$profile` variable représente le chemin d’accès du fichier. Le paramètre **ItemType** spécifie que la commande crée un fichier. Le paramètre **force** vous permet de créer un fichier dans le chemin d’accès du profil, même si les répertoires du chemin d’accès n’existent pas.

Après avoir créé un profil, vous pouvez entrer des alias, des fonctions et des scripts dans le profil pour personnaliser votre shell.

Pour plus d’informations, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) et [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### Exemple 4 : créer un répertoire dans un autre répertoire

Cet exemple crée un répertoire scripts dans le répertoire « C:\PS-test. ».

Le nom du nouvel élément de répertoire, « scripts », est inclus dans la valeur du paramètre **path** , au lieu d’être spécifié dans la valeur de **Name**. Comme indiqué par la syntaxe, les deux formes de commande sont valides.

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### Exemple 5 : créer plusieurs fichiers

Cet exemple crée des fichiers dans deux répertoires différents. Étant donné que **path** accepte plusieurs chaînes, vous pouvez l’utiliser pour créer plusieurs éléments.

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### Exemple 6 : utilisation de caractères génériques pour créer des fichiers dans plusieurs répertoires

L' `New-Item` applet de commande prend en charge les caractères génériques dans le paramètre **path** . La commande suivante crée un `temp.txt` fichier dans tous les répertoires spécifiés par les caractères génériques dans le paramètre **path** .

```powershell
Get-ChildItem -Path C:\Temp\
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d-----        5/15/2019   6:45 AM        1   One
d-----        5/15/2019   6:45 AM        1   Two
d-----        5/15/2019   6:45 AM        1   Three
```

```powershell
New-Item -Path * -Name temp.txt -ItemType File | Select-Object FullName
```

```Output
FullName
--------
C:\Temp\One\temp.txt
C:\Temp\Three\temp.txt
C:\Temp\Two\temp.txt
```

L' `Get-ChildItem` applet de commande affiche trois répertoires sous le `C:\Temp` répertoire. À l’aide de caractères génériques, l’applet de commande `New-Item` crée un `temp.txt` fichier dans tous les répertoires sous le répertoire actif. L' `New-Item` applet de commande génère les éléments que vous avez créés, qui sont redirigés vers `Select-Object` pour vérifier les chemins des fichiers nouvellement créés.

### Exemple 7 : créer un lien symbolique vers un fichier ou un dossier

Cet exemple crée un lien symbolique vers le fichier Notice.txt dans le dossier actif.

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

Dans cet exemple, **target** est un alias pour le paramètre **value** . La cible du lien symbolique peut être un chemin d’accès relatif. Avant PowerShell v 6.2, la cible doit être un chemin d’accès complet.

À compter de PowerShell 7,1, vous pouvez désormais créer un **SymbolicLink** dans un dossier sur Windows à l’aide d’un chemin d’accès relatif.

### Exemple 8 : utiliser le paramètre-force pour tenter de recréer des dossiers

Cet exemple crée un dossier avec un fichier à l’intérieur de. Tente ensuite de créer le même dossier à l’aide de `-Force` . Il ne remplace pas le dossier, mais retourne simplement l’objet dossier existant avec le fichier créé intact.

```powershell
PS> New-Item -Path .\TestFolder -ItemType Directory
PS> New-Item -Path .\TestFolder\TestFile.txt -ItemType File

PS> New-Item -Path .\TestFolder -ItemType Directory -Force

    Directory: C:\
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/1/2020   8:03 AM                TestFolder

PS> Get-ChildItem .\TestFolder\

    Directory: C:\TestFolder
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:03 AM              0 TestFile.txt
```

### Exemple 9 : utiliser le paramètre-force pour remplacer les fichiers existants

Cet exemple crée un fichier avec une valeur, puis recrée le fichier à l’aide de `-Force` . Cela a pour fonction de remplacer le fichier existant et de perdre son contenu, comme vous pouvez le voir dans la propriété Length.

```powershell
PS> New-Item ./TestFile.txt -ItemType File -Value 'This is just a test file'

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM             24 TestFile.txt

New-Item ./TestFile.txt -ItemType File -Force

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM              0 TestFile.txt
```

> [!NOTE]
> Lors de l’utilisation `New-Item` de avec le `-Force` commutateur pour créer des clés de Registre, la commande se comporte de la même façon que lors du remplacement d’un fichier. Si la clé de Registre existe déjà, la clé et toutes les propriétés et valeurs sont remplacées par une clé de Registre vide.

## PARAMETERS

### -Credential

> [!NOTE]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell. Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez `Invoke-Command` .

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

### -Force

Force cette applet de commande à créer un élément qui écrit sur un élément en lecture seule existant. L'implémentation est différente d'un fournisseur à l'autre. Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.

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

### -ItemType

Spécifie le type indiqué par le fournisseur du nouvel élément. Les valeurs disponibles de ce paramètre dépendent du fournisseur actuel que vous utilisez.

Si votre emplacement se trouve dans un `FileSystem` lecteur, les valeurs suivantes sont autorisées :

- Fichier
- Répertoire
- SymbolicLink
- jonction
- HardLink

> [!NOTE]
> La création d’un `SymbolicLink` type sur Windows requiert une élévation en tant qu’administrateur. Toutefois, Windows 10 (version 14972 ou ultérieure) avec le mode développeur activé ne nécessite plus d’élévation pour créer des liens symboliques.

Dans un `Certificate` lecteur, les valeurs que vous pouvez spécifier sont les suivantes :

- Fournisseur Certificate
- Certificat
- Magasin
- StoreLocation

Pour plus d’informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie le nom du nouvel élément. Vous pouvez spécifier le nom du nouvel élément dans la valeur du paramètre **Name** ou **path** , et vous pouvez spécifier le chemin d’accès du nouvel élément dans le **nom** ou la valeur du **chemin d’accès** . Les noms d’éléments passés à l’aide du paramètre **Name** sont créés par rapport à la valeur du paramètre **path** .

```yaml
Type: System.String
Parameter Sets: nameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d’accès de l’emplacement du nouvel élément. La valeur par défaut est l’emplacement actuel lorsque le **chemin d’accès** est omis. Vous pouvez spécifier le nom du nouvel élément dans le **nom** ou l’inclure dans **path**. Les noms d’éléments passés à l’aide du paramètre **Name** sont créés par rapport à la valeur du paramètre **path** .

Pour cette applet de commande, le paramètre **path** fonctionne comme le paramètre **LiteralPath** d’autres applets de commande.
Les caractères génériques ne sont pas interprétés. Tous les caractères sont passés au fournisseur de l’emplacement. Le fournisseur ne prend peut-être pas en charge tous les caractères. Par exemple, vous ne pouvez pas créer un nom de fichier contenant un astérisque ( `*` ).

```yaml
Type: System.String[]
Parameter Sets: pathSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Value

Spécifie la valeur du nouvel élément. Vous pouvez également diriger une valeur vers `New-Item` .

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Target

Required: False
Position: Named
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

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.Object

Vous pouvez diriger une valeur pour le nouvel élément vers cette applet de commande.

## SORTIES

### System.Object

Cette applet de commande retourne l’élément qu’elle crée.

## REMARQUES

`New-Item` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PsProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

