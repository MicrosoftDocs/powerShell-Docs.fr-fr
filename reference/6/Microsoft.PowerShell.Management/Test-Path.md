---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: d61168634745505c4ae172aafabf45f6f7a46c5e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202386"
---
# Test-Path

## SYNOPSIS
Détermine si tous les éléments d'un chemin d'accès existent.

## SYNTAX

### Chemin d’accès (par défaut)

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### LiteralPath

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## Description

L' `Test-Path` applet de commande détermine si tous les éléments du chemin d’accès existent. Elle retourne `$True` si tous les éléments existent et `$False` si des éléments sont manquants. Il peut également indiquer si la syntaxe du chemin d’accès est valide et si le chemin d’accès est un conteneur ou un élément terminal ou feuille. Si le `Path` est un espace blanc d’une chaîne vide, `$False` est retourné. Si `Path` est `$null` , tableau `$null` ou tableau vide, une erreur sans fin d’achèvement est retournée.

## EXEMPLES

### Exemple 1 : tester un chemin d’accès

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

Cette commande vérifie si tous les éléments du chemin d’accès existent, autrement dit, le répertoire C :, le répertoire documents and Settings et le répertoire DavidC S’il en manque, l’applet de commande retourne `$False` .
Sinon, il retourne `$True`.

### Exemple 2 : tester le chemin d’accès d’un profil

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

Ces commandes testent le chemin d’accès du profil PowerShell.

La première commande détermine si tous les éléments du chemin d'accès existent. La deuxième commande détermine si la syntaxe du chemin d'accès est correcte. Dans ce cas, le chemin d’accès est `$False` , mais la syntaxe est correcte `$True` . Ces commandes utilisent `$profile` , la variable automatique qui pointe vers l’emplacement du profil, même si le profil n’existe pas.

Pour plus d'informations sur les variables automatiques, consultez about_Automatic_Variables.

### Exemple 3 : vérifier si des fichiers sont en dehors d’un type spécifié

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

Cette commande vérifie si des fichiers se trouvent dans le répertoire des bâtiments commerciaux, à l’exception des fichiers. dwg.

La commande utilise le paramètre **path** pour spécifier le chemin d’accès. Étant donné que le chemin d’accès comprend un espace, le chemin d’accès est placé entre guillemets. L'astérisque situé à la fin du chemin d'accès indique le contenu du répertoire Commercial Building. Avec des chemins d’accès longs, tels que celui-ci, tapez les premières lettres du chemin d’accès, puis utilisez la touche TAB pour compléter le chemin d’accès.

La commande spécifie le paramètre **Exclude** pour spécifier les fichiers qui seront omis de l’évaluation.

Dans ce cas, étant donné que le répertoire contient uniquement des fichiers. dwg, le résultat est `$False` .

### Exemple 4 : Rechercher un fichier

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

Cette commande vérifie si le chemin d’accès stocké dans la `$profile` variable ouvre un fichier. Dans ce cas, étant donné que le profil PowerShell est un `.ps1` fichier, l’applet de commande retourne `$True` .

### Exemple 5 : vérifier les chemins d’accès dans le registre

Ces commandes utilisent `Test-Path` avec le fournisseur de Registre PowerShell.

La première commande teste si le chemin d’accès du registre de la clé de Registre **Microsoft. PowerShell** est correct sur le système. Si PowerShell est installé correctement, l’applet de commande retourne `$True` .

> [!IMPORTANT]
> `Test-Path` ne fonctionne pas correctement avec tous les fournisseurs PowerShell. Par exemple, vous pouvez utiliser `Test-Path` pour tester le chemin d’accès à une clé de Registre, mais si vous l’utilisez pour tester le chemin d’accès d’une entrée de Registre, elle retourne toujours `$False` , même si l’entrée de Registre est présente.

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### Exemple 6 : tester si un fichier est plus récent qu’une date spécifiée

Cette commande utilise le paramètre dynamique **NewerThan** pour déterminer si le fichier « PowerShell.exe » sur l’ordinateur est plus récent que « le 13 juillet 2009 ».

Le paramètre NewerThan fonctionne uniquement dans les lecteurs de système de fichiers.

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### Exemple 7 : tester un chemin d’accès avec NULL comme valeur

L’erreur retournée pour `null` , tableau de `null` ou tableau vide est une erreur sans fin d’achèvement. Il peut être supprimé à l’aide de `-ErrorAction SilentlyContinue` . L’exemple suivant montre tous les cas qui retournent l' `NullPathNotPermitted` erreur.

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### Exemple 8 : test d’un chemin d’accès avec un espace blanc en tant que valeur

Lorsqu’un espace blanc ou une chaîne vide est fourni pour le `-Path` paramètre, la **valeur false** est retournée.
L’exemple suivant montre un espace blanc et une chaîne vide.

```powershell
Test-Path ' '
Test-Path ''
```

```Output
False
False
```

## PARAMETERS

### -Credential

> [!NOTE]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell. Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

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

### -Exclude

Spécifie les éléments que cette applet de commande omet. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d'accès, tel que « *.txt ». Les caractères génériques sont autorisés.

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

Spécifie un filtre dans le format ou la langue du fournisseur. La valeur de ce paramètre qualifie le paramètre **Path** . La syntaxe du filtre, notamment l’utilisation de caractères génériques, dépend du fournisseur. Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsqu’il récupère les objets au lieu d’avoir le filtre PowerShell pour les objets après leur récupération.

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

Spécifie les chemins que cette applet de commande teste. La valeur de ce paramètre qualifie le paramètre **Path** . Entrez un élément ou un modèle de chemin d'accès, tel que « *.txt ». Les caractères génériques sont autorisés.

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

### -IsValid

Indique que cette applet de commande teste la syntaxe du chemin d’accès, que les éléments du chemin d’accès existent ou non. Cette applet de commande retourne `$True` si la syntaxe du chemin d’accès est valide et si ce n' `$False` est pas le cas.

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

Spécifie un chemin d’accès à vérifier. Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n'est interprété en tant que caractère générique. Si le chemin d’accès comprend des caractères qui peuvent être interprétés par PowerShell comme des séquences d’échappement, vous devez placer le chemin d’accès entre guillemets simples afin qu’ils ne soient pas interprétés.

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

### -NewerThan

Spécifiez une heure sous la forme d’un objet **DateTime** .

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OlderThan 

Spécifiez une heure sous la forme d’un objet **DateTime** .

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie un chemin d’accès à vérifier.
Les caractères génériques sont autorisés.
Si le chemin d’accès inclut des espaces, mettez-le entre guillemets.

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

### -PathType

Spécifie le type de l’élément final dans le chemin d’accès. Cette applet de commande retourne `$True` si l’élément est du type spécifié et `$False` si ce n’est pas le cas. Les valeurs valides pour ce paramètre sont :

- Conteneur.
  élément qui contient d'autres éléments (répertoire ou clé de Registre, par exemple).
- Inférieurs.
  élément qui ne contient pas d'autres éléments (fichier, par exemple).
- Aux.
  conteneur ou nœud terminal.

Indique si le dernier élément figurant dans le chemin d’accès est d’un type particulier.

> [!CAUTION]
>
> Jusqu’à PowerShell version 6.1.2, lorsque les commutateurs **IsValid** et **PathType** sont spécifiés ensemble, l’applet de commande `Test-Path` ignore le commutateur **PathType** et valide uniquement le chemin syntaxique sans valider le type de chemin d’accès.
>
> En fonction du [problème #8607](https://github.com/PowerShell/PowerShell/issues/8607), la résolution de ce problème peut être une modification avec rupture dans une future version, où les commutateurs **IsValid** et **PathType** appartiennent à des jeux de paramètres distincts et, par conséquent, ne peuvent pas être utilisés ensemble pour éviter cette confusion.

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.

## SORTIES

### System.Boolean

L’applet de commande retourne une valeur **booléenne** .

## REMARQUES

Les applets de commande qui contiennent le nom de **chemin** d’accès (les applets de commande **path** ) fonctionnent avec des noms de chemins d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter. Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier.
Utilisez-les comme vous le feriez avec **dirname** , **Normpath** , **realpath** , **join** ou d’autres manipulateurs de chemin.

Le `Test-Path` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.
Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .
Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)
