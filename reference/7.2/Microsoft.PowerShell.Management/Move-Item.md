---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: a47c017371fe5fe87618c11551cd1ecba76d5c60
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599010"
---
# Move-Item

## SYNOPSIS
Déplace un élément d'un emplacement à un autre.

## SYNTAXE

### Chemin d’accès (par défaut)

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Move-Item` applet de commande déplace un élément, y compris ses propriétés, son contenu et ses éléments enfants, d’un emplacement à un autre. Les emplacements doivent être pris en charge par le même fournisseur.
Par exemple, elle peut déplacer un fichier ou un sous-répertoire d'un répertoire à un autre ou une sous-clé de Registre d'une clé à une autre.
Lors du déplacement d'un élément, celui-ci est ajouté au nouvel emplacement et supprimé de l'emplacement d'origine.

## EXEMPLES

### Exemple 1 : déplacer un fichier vers un autre répertoire et le renommer

Cette commande déplace le `Test.txt` fichier du `C:` lecteur vers le `E:\Temp` répertoire et le renomme `test.txt` en `tst.txt` .

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### Exemple 2 : déplacer un répertoire et son contenu vers un autre répertoire

Cette commande déplace le `C:\Temp` répertoire et son contenu vers le `C:\Logs` répertoire.
Le répertoire « Temp », ainsi que tous ses sous-répertoires et fichiers, apparaissent dans le répertoire « logs ».

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### Exemple 3 : déplacer tous les fichiers d’une extension spécifiée du répertoire actif vers un autre répertoire

Cette commande déplace tous les fichiers texte ( `*.txt` ) dans le répertoire actif (représenté par un point ( `.` )) vers le `C:\Logs` répertoire.

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### Exemple 4 : déplacer de manière récursive tous les fichiers d’une extension spécifiée du répertoire actif vers un autre répertoire

Cette commande déplace tous les fichiers texte du répertoire actif et de tous ses sous-répertoires, de manière récursive, vers le répertoire « C:\Textfiles. ».

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

La commande utilise l' `Get-ChildItem` applet de commande pour obtenir tous les éléments enfants dans le répertoire actif (représenté par le \[ point \] ) et ses sous-répertoires qui ont une *extension de nom de fichier « . txt ». Elle utilise le paramètre **recurse** pour rendre la récupération récursive et le paramètre Include pour limiter la récupération aux fichiers «*. txt ».

L’opérateur de pipeline ( `|` ) envoie les résultats de cette commande à `Move-Item` , qui déplace les fichiers texte vers le répertoire « textfiles ».

Si les fichiers à déplacer vers « C:\Textfiles. » portent le même nom, `Move-Item` affiche une erreur et se poursuit, mais il déplace un seul fichier avec chaque nom à « c:\Textfiles. ».
Les autres fichiers restent dans les répertoires d'origine.

Si le répertoire « Textfiles » (ou tout autre élément du chemin d’accès de destination) n’existe pas, la commande échoue.
Le répertoire manquant n’est pas créé pour vous, même si vous utilisez le paramètre **force** .
`Move-Item` déplace le premier élément vers un fichier appelé « Textfiles », puis affiche une erreur expliquant que le fichier existe déjà.

De même, par défaut, `Get-ChildItem` ne déplace pas les fichiers masqués.
Pour déplacer des fichiers masqués, utilisez le paramètre **force** avec `Get-ChildItem` .

> [!NOTE]
> Dans Windows PowerShell 2,0, quand vous utilisez le paramètre **recurse** de l’applet de commande `Get-ChildItem` , la valeur du paramètre **path** doit être un conteneur.
> Utilisez le paramètre **Include** pour spécifier le filtre d'extension de nom de fichier .txt (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).

### Exemple 5 : déplacer des clés et des valeurs de Registre vers une autre clé

Cette commande déplace les clés et les valeurs de registre de la clé de Registre « MyCompany » dans `HKLM\Software` vers la clé « MyNewCompany ».
Le caractère générique ( `*` ) indique que le contenu de la clé « MyCompany » doit être déplacé, et non la clé elle-même.
Dans cette commande, les noms de paramètres facultatifs **path** et **destination** sont omis.

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### Exemple 6 : déplacer un répertoire et son contenu vers un sous-répertoire du répertoire spécifié

Cette commande déplace le répertoire « logs \[ septembre \` 06 \] » (et son contenu) dans le répertoire « logs \[ 2006 \] ».

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

Le paramètre **LiteralPath** est utilisé à la place de **path**, car le nom du répertoire d’origine comprend les parenthèses ouvrante et fermante (« \[ » et «» \] ).
Le chemin d’accès est également placé entre guillemets simples (' '), afin que le symbole de la contre-impulsion ( \` ) ne soit pas interprété à tort.

Le paramètre **destination** ne requiert pas de chemin d’accès littéral, car la variable de destination doit également être placée entre guillemets simples, car elle comprend des crochets qui peuvent être mal interprétés.

## PARAMETERS

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

Spécifie le chemin d'accès à l'emplacement vers lequel les éléments sont déplacés.
L'emplacement par défaut est le répertoire actif.
Les caractères génériques sont autorisés, mais le résultat doit spécifier un seul emplacement.

Pour renommer l’élément déplacé, spécifiez un nouveau nom dans la valeur du paramètre **destination** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.
L'implémentation est différente d'un fournisseur à l'autre.
Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

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

### -PassThru

Retourne un objet représentant l’élément que vous utilisez.
Par défaut, cette applet de commande ne génère aucun résultat.

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

Spécifie le chemin d'accès à l'emplacement actuel des éléments.
L'emplacement par défaut est le répertoire actif.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
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

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.

## SORTIES

### Aucun ou un objet représentant l’élément déplacé

Quand vous utilisez le paramètre *PassThru* , cette applet de commande génère un objet représentant l’élément déplacé.
Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

- Cette applet de commande déplace les fichiers entre les lecteurs pris en charge par le même fournisseur, mais elle déplace les répertoires uniquement dans le même lecteur.
- Étant donné qu’une `Move-Item` commande déplace les propriétés, le contenu et les éléments enfants d’un élément, tous les déplacements sont récursifs par défaut.
- Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.
  Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .
  Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

