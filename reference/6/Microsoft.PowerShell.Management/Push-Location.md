---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: 59199ee409749ed61d76f645a49890f43395885c
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "93205874"
---
# Push-Location

## SYNOPSIS
Ajoute l'emplacement actuel au sommet d'une liste d'emplacements.

## SYNTAX

### Chemin d’accès (par défaut)

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

### LiteralPath

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## Description

L' `Push-Location` applet de commande ajoute (« push ») l’emplacement actuel sur une pile d’emplacements. Si vous spécifiez un chemin d’accès, `Push-Location` exécute un push de l’emplacement actuel sur une pile d’emplacements, puis modifie l’emplacement actuel à l’emplacement spécifié par le chemin d’accès. Vous pouvez utiliser l' `Pop-Location` applet de commande pour récupérer les emplacements de la pile d’emplacements.

Par défaut, l' `Push-Location` applet de commande exécute un push de l’emplacement actuel dans la pile d’emplacements active, mais vous pouvez utiliser le paramètre **StackName** pour spécifier une autre pile d’emplacements. Si la pile n’existe pas, la `Push-Location` crée.

Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).

## EXEMPLES

### Exemple 1

Cet exemple exécute un push de l’emplacement actuel dans la pile d’emplacements par défaut, puis modifie l’emplacement en `C:\Windows` .

```
PS C:\> Push-Location C:\Windows
```

### Exemple 2

Cet exemple exécute un push de l’emplacement actuel dans la pile RegFunction, puis et modifie l’emplacement actuel à l' `HKLM:\Software\Policies` emplacement.

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

Vous pouvez utiliser les applets de commande location dans n’importe quel lecteur PowerShell (PSDrive).

### Exemple 3

Cette commande place l'emplacement actuel sur la pile par défaut. Elle ne modifie pas l'emplacement.

```
PS C:\> Push-Location
```

### Exemple 4 : créer et utiliser une pile nommée

Ces commandes indiquent comment créer et utiliser une pile d'emplacement nommée.

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

La première commande place l’emplacement actuel sur une nouvelle pile nommée Stack2, puis modifie l’emplacement actuel dans le répertoire de départ, représenté dans la commande par le symbole de tilde ( `~` ), qui, lorsqu’il est utilisé sur un lecteur de fournisseur FileSystem, est équivalent à `$HOME` et `$env:USERPROFILE` .

Si Stack2 n’existe pas encore dans la session, le `Push-Location` crée. La deuxième commande utilise l' `Pop-Location` applet de commande pour dépiler l’emplacement d’origine ( `C:\` ) à partir de la pile Stack2. Sans le paramètre **StackName** , `Pop-Location` dépilerait l’emplacement de la pile par défaut sans nom.

Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).

## PARAMETERS

### -LiteralPath

Spécifie le chemin d'accès au nouvel emplacement. Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Passe un objet représentant l'emplacement au pipeline. Par défaut, cette applet de commande ne génère aucun résultat.

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

Définit votre emplacement sur l'emplacement spécifié par ce chemin d'accès après avoir (ajouté) placé l'emplacement actuel au sommet de la pile. Entrez un chemin d'accès à n'importe quel emplacement dont le fournisseur prend en charge cette applet de commande. Les caractères génériques sont autorisés. Le nom de paramètre est facultatif.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StackName

Spécifie la pile d'emplacements à laquelle l'emplacement actuel est ajouté. Entrez un nom de pile d'emplacements.
Si la pile n’existe pas, la `Push-Location` crée.

Sans ce paramètre, `Push-Location` ajoute l’emplacement à la pile d’emplacements active. Par défaut, la pile d’emplacements active est la pile d’emplacements par défaut sans nom que PowerShell crée.
Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre **StackName** de l’applet de commande `Set-Location` . Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).

> [!NOTE]
> `Push-Location` Impossible d’ajouter un emplacement à la pile par défaut sans nom, sauf s’il s’agit de la pile d’emplacements active.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès (mais pas un chemin d’accès littéral) vers `Push-Location` .

## SORTIES

### None ou System. Management. Automation. PathInfo

Quand vous utilisez le paramètre **PassThru** , `Push-Location` génère un objet **System. Management. Automation. PathInfo** qui représente l’emplacement. Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

PowerShell prend en charge plusieurs instances d’exécution par processus. Chaque instance d’exécution a son propre _répertoire actif_ .
Ce n’est pas le même que `[System.Environment]::CurrentDirectory` . Ce comportement peut être un problème lors de l’appel d’API .NET ou de l’exécution d’applications natives sans fournir de chemins d’accès explicites au répertoire.

Même si les applets de commande location ont défini le répertoire actif à l’ensemble du processus, vous ne pouvez pas en dépendre, car une autre instance d’exécution peut la modifier à tout moment. Vous devez utiliser les applets de commande location pour effectuer des opérations basées sur le chemin d’accès à l’aide du répertoire de travail actuel spécifique à l’instance d’exécution actuelle.

Une pile est une liste de dernier sorti, premier sorti dans laquelle seul l’élément le plus récemment ajouté est accessible.
Vous ajoutez des éléments à une pile dans l'ordre dans lequel vous les utilisez, puis les récupérez pour une utilisation dans l'ordre inverse. PowerShell vous permet de stocker les emplacements des fournisseurs dans des piles d’emplacements.

PowerShell crée une pile d’emplacements par défaut sans nom et vous pouvez créer plusieurs piles d’emplacements nommées. Si vous ne spécifiez pas de nom de pile, PowerShell utilise la pile d’emplacements active. Par défaut, l’emplacement par défaut sans nom est la pile d’emplacements active, mais vous pouvez utiliser l' `Set-Location` applet de commande pour modifier la pile d’emplacements active.

Pour gérer les piles d’emplacements, utilisez les applets de commande PowerShell location, comme suit.

- Pour ajouter un emplacement à une pile d’emplacements, utilisez l’applet de commande `Push-Location` .

- Pour obtenir un emplacement à partir d’une pile d’emplacements, utilisez l’applet de commande `Pop-Location` .

- Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** de l’applet de commande `Get-Location` .

- Pour afficher les emplacements dans une pile d’emplacements nommée, utilisez le paramètre **StackName** de l’applet de commande `Get-Location` .

- Pour créer une nouvelle pile d’emplacements, utilisez le paramètre StackName de l’applet de commande `Push-Location` . Si vous spécifiez une pile qui n’existe pas, `Push-Location` crée la pile.

- Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre StackName de l’applet de commande `Set-Location` .

La pile d'emplacements par défaut sans nom n'est entièrement accessible que s'il s'agit de la pile d'emplacements active.
Si vous définissez une pile d’emplacements nommée sur la pile d’emplacements active, vous ne pouvez plus utiliser les `Push-Location` applets de commande ou `Pop-Location` pour ajouter ou obtenir des éléments à partir de la pile par défaut ou utiliser l' `Get-Location` applet de commande pour afficher les emplacements dans la pile sans nom. Pour que la pile sans nom soit la pile active, utilisez le paramètre **StackName** de l' `Set-Location` applet de commande avec une valeur `$null` ou une chaîne vide ( `""` ).

Vous pouvez également faire référence à `Push-Location` par son alias intégré, `pushd` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

L' `Push-Location` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Get-Location](Get-Location.md)

[Pop-Location](Pop-Location.md)

[Set-Location](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
