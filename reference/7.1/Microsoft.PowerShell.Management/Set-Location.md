---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: 0c511ea30d55c1e6949f687c81d1edef809546fc
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "93206073"
---
# Set-Location

## SYNOPSIS
Définit l'emplacement de travail actif sur un emplacement spécifié.

## SYNTAX

### Chemin d’accès (par défaut)

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### LiteralPath

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### Pile

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## Description

L' `Set-Location` applet de commande définit l’emplacement de travail à un emplacement spécifié. Cet emplacement peut être un répertoire, un sous-répertoire, un emplacement du registre ou n’importe quel chemin d’accès du fournisseur.

PowerShell 6,2 a ajouté la prise en charge de `-` et `+` en tant que valeurs pour le paramètre **path** . PowerShell conserve un historique des 20 derniers emplacements accessibles avec `-` et `+` . Cette liste est indépendante de la pile d’emplacements accessible à l’aide du paramètre **StackName** .

## EXEMPLES

### Exemple 1 : définir l’emplacement actuel

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

Cette commande définit l’emplacement actuel à la racine du `HKLM:` lecteur.

### Exemple 2 : définir l’emplacement actuel et afficher cet emplacement

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

Cette commande définit l’emplacement actuel à la racine du `Env:` lecteur. Elle utilise le paramètre **PassThru** pour indiquer à PowerShell de retourner un objet **PathInfo** qui représente l' `Env:\` emplacement.

### Exemple 3 : définir l’emplacement actuel sur le lecteur C :

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

La première commande définit l’emplacement à la racine du `HKLM:` lecteur dans le fournisseur de registre.
La deuxième commande définit l’emplacement à l’emplacement actuel du `C:` lecteur dans le fournisseur FileSystem.
Lorsque le nom du lecteur est spécifié sous la forme `<DriveName>:` (sans barre oblique inverse), l’applet de commande définit l’emplacement à l’emplacement actuel dans le PSDrive.
Pour accéder à l’emplacement actuel dans la commande PSDrive use `Get-Location -PSDrive <DriveName>` .

### Exemple 4 : définir l’emplacement actuel sur une pile nommée

```
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

La première commande ajoute l’emplacement actuel à la pile de chemins d’accès.
La deuxième commande permet à l’emplacement des chemins d’accès de la pile d’emplacements active.
La troisième commande affiche les emplacements dans la pile d’emplacements active.

Les `*-Location` applets de commande utilisent la pile d’emplacements active, sauf si une pile d’emplacements différente est spécifiée dans la commande. Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).

### Exemple 5 : naviguer dans l’historique des emplacements à l’aide `+` de ou `-`

```
PS C:\> Set-Location -Path $env:SystemRoot
PS C:\Windows> Set-Location -Path Cert:\
PS Cert:\> Set-Location -Path HKLM:\
PS HKLM:\>

# Navigate back through the history using "-"
PS HKLM:\> Set-Location -Path -
PS Cert:\> Set-Location -Path -
PS C:\Windows>

# Navigate using the Set-Location alias "cd" and the implicit positional Path parameter
PS C:\Windows> cd -
PS C:\> cd +
PS C:\Windows> cd +
PS Cert:\>
```

À l’aide de l’alias, `cd -` ou `cd +` est un moyen simple de naviguer dans votre historique d’emplacement dans votre terminal. Pour plus d’informations sur la navigation dans `-` / `+` , consultez le paramètre **path** .

## PARAMETERS

### -LiteralPath

Spécifie le chemin d’accès de l’emplacement. La valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n'est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourne un objet **PathInfo** qui représente l’emplacement. Par défaut, cette applet de commande ne génère aucun résultat.

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

Spécifiez le chemin d’accès d’un nouvel emplacement de travail. Si aucun chemin d’accès n’est fourni, `Set-Location` le répertoire de démarrage de l’utilisateur actuel est utilisé par défaut. Lorsque des caractères génériques sont utilisés, l’applet de commande choisit le premier chemin d’accès qui correspond au modèle de caractère générique.

PowerShell conserve un historique des 20 derniers emplacements que vous avez définis. Si la valeur du paramètre **path** est le `-` caractère, le nouvel emplacement de travail sera l’emplacement de travail précédent dans l’historique (s’il existe). De même, si la valeur est le `+` caractère, le nouvel emplacement de travail sera l’emplacement de travail suivant dans l’historique (s’il existe). Cette approche est similaire à l’utilisation de et, à `Pop-Location` `Push-Location` la différence près que l’historique est une liste, et non une pile, et qu’elle est suivie implicitement, et non pas manuellement. Actuellement, il n’existe aucun moyen d’afficher la liste de l’historique.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StackName

Spécifie le nom existant de la pile d’emplacements que cette applet de commande établit avec la pile d’emplacements active. Entrez un nom de pile d'emplacements. Pour indiquer la pile d’emplacements par défaut sans nom, tapez `$null` ou une chaîne vide ( `""` ).

Les `*-Location` applets de commande agissent sur la pile active, sauf si vous utilisez le paramètre **StackName** pour spécifier une autre pile. Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).

```yaml
Type: System.String
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès, mais pas un chemin d’accès littéral, vers cette applet de commande.

## SORTIES

### Aucun, System. Management. Automation. PathInfo, System. Management. Automation. PathInfoStack

Cette applet de commande ne génère pas de sortie, sauf si vous spécifiez le paramètre **PassThru** . L’utilisation de **PassThru** avec **path** ou **LiteralPath** génère un objet **PathInfo** qui représente le nouvel emplacement. L’utilisation de **PassThru** avec **StackName** génère un objet **PathInfoStack** qui représente le nouveau contexte de pile.

## REMARQUES

PowerShell prend en charge plusieurs instances d’exécution par processus. Chaque instance d’exécution a son propre _répertoire actif_ .
Ce n’est pas le même que `[System.Environment]::CurrentDirectory` . Ce comportement peut être un problème lors de l’appel d’API .NET ou de l’exécution d’applications natives sans fournir de chemins d’accès explicites au répertoire.

Même si les applets de commande location ont défini le répertoire actif à l’ensemble du processus, vous ne pouvez pas en dépendre, car une autre instance d’exécution peut la modifier à tout moment. Vous devez utiliser les applets de commande location pour effectuer des opérations basées sur le chemin d’accès à l’aide du répertoire de travail actuel spécifique à l’instance d’exécution actuelle.

L' `Set-Location` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).

Une pile est une liste de dernier et premier sorti dans laquelle seul l’élément le plus récemment ajouté est accessible. Vous ajoutez des éléments à une pile dans l'ordre dans lequel vous les utilisez, puis les récupérez pour une utilisation dans l'ordre inverse. PowerShell vous permet de stocker les emplacements des fournisseurs dans des piles d’emplacements. PowerShell crée une pile d’emplacements par défaut sans nom. Vous pouvez créer plusieurs piles d’emplacements nommées. Si vous ne spécifiez pas de nom de pile, PowerShell utilise la pile d’emplacements active. Par défaut, l’emplacement par défaut sans nom est la pile d’emplacements active, mais vous pouvez utiliser l' `Set-Location` applet de commande pour modifier la pile d’emplacements active.

Pour gérer les piles d’emplacements, utilisez les `*-Location` applets de commande suivantes :

- Pour ajouter un emplacement à une pile d’emplacements, utilisez l’applet de commande `Push-Location` .

- Pour obtenir un emplacement à partir d’une pile d’emplacements, utilisez l’applet de commande `Pop-Location` .

- Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** de l’applet de commande `Get-Location` . Pour afficher les emplacements dans une pile d’emplacements nommée, utilisez le paramètre **StackName** de `Get-Location` .

- Pour créer une nouvelle pile d’emplacements, utilisez le paramètre **StackName** de `Push-Location` . Si vous spécifiez une pile qui n’existe pas, `Push-Location` crée la pile.

- Pour faire d’une pile d’emplacements la pile d’emplacements active, utilisez le paramètre **StackName** de `Set-Location` .

La pile d'emplacements par défaut sans nom n'est entièrement accessible que s'il s'agit de la pile d'emplacements active.
Si vous définissez une pile d’emplacements nommée sur la pile d’emplacements active, vous ne pouvez plus utiliser les `Push-Location` applets de commande ou `Pop-Location` pour ajouter ou obtenir des éléments à partir de la pile par défaut ou utiliser l' `Get-Location` applet de commande pour afficher les emplacements dans la pile sans nom. Pour que la pile sans nom soit la pile active, utilisez le paramètre **StackName** de l' `Set-Location` applet de commande avec une valeur `$null` ou une chaîne vide ( `""` ).

## LIENS CONNEXES

[Get-Location](Get-Location.md)

[Pop-Location](Pop-Location.md)

[Push-Location](Push-Location.md)

