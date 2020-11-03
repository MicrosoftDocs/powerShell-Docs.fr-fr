---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 42a5c9c75c11a40b5bb842d86894688a354bed15
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "93205877"
---
# Pop-Location

## SYNOPSIS
Définit l'emplacement actuel sur le dernier emplacement placé sur la pile.

## SYNTAX

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## Description

L' `Pop-Location` applet de commande modifie l’emplacement actuel à l’emplacement le plus récemment déplacé vers la pile à l’aide de l’applet de commande `Push-Location` . Vous pouvez extraire un emplacement à partir de la pile par défaut ou d’une pile que vous créez à l’aide d’une `Push-Location` commande.

## EXEMPLES

### Exemple 1 : passer à l’emplacement le plus récent

```
PS C:\> Pop-Location
```

Cette commande définit l'emplacement sur le dernier emplacement ajouté à la pile active.

### Exemple 2 : passer à l’emplacement le plus récent dans une pile nommée

```
PS C:\> Pop-Location -StackName "Stack2"
```

Cette commande définit l'emplacement sur le dernier emplacement ajouté à la pile d'emplacements Stack2.

Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).

### Exemple 3 : passer d’un emplacement à un autre pour différents fournisseurs

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

Ces commandes utilisent les `Push-Location` applets de commande et `Pop-Location` pour se déplacer entre les emplacements pris en charge par les différents fournisseurs PowerShell. Les commandes utilisent l' `pushd` alias pour `Push-Location` et l' `popd` alias de `Pop-Location` .

La première commande transmet l’emplacement du système de fichiers actuel sur la pile et se déplace vers le lecteur HKLM pris en charge par le fournisseur de Registre PowerShell.

La deuxième commande transmet l’emplacement du Registre à la pile et se déplace vers un emplacement pris en charge par le fournisseur de certificats PowerShell.

Les deux dernières commandes extraient ces emplacements de la pile. La première `popd` commande retourne au lecteur du Registre, et la deuxième commande retourne au lecteur du système de fichiers.

## PARAMETERS

### -PassThru

Passe un objet qui représente l’emplacement au pipeline. Par défaut, cette applet de commande ne génère aucun résultat.

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

### -StackName

Spécifie la pile d'emplacements à partir de laquelle l'emplacement est extrait. Entrez un nom de pile d'emplacements.

Sans ce paramètre, exécute `Pop-Location` un pop sur un emplacement de la pile d’emplacements active. Par défaut, la pile d’emplacements active est la pile d’emplacements par défaut sans nom que PowerShell crée. Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre **StackName** de l’applet de commande `Set-Location` . Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).

`Pop-Location` Impossible de dépiler un emplacement à partir de la pile par défaut sans nom, sauf s’il s’agit de la pile d’emplacements active.

```yaml
Type: System.String
Parameter Sets: (All)
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

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun, System. Management. Automation. PathInfo

Cette applet de commande génère un objet **System. Management. Automation. PathInfo** qui représente l’emplacement, si vous spécifiez le paramètre **PassThru** . Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

PowerShell prend en charge plusieurs instances d’exécution par processus. Chaque instance d’exécution a son propre _répertoire actif_ .
Ce n’est pas le même que `[System.Environment]::CurrentDirectory` . Ce comportement peut être un problème lors de l’appel d’API .NET ou de l’exécution d’applications natives sans fournir de chemins d’accès explicites au répertoire.

Même si les applets de commande location ont défini le répertoire actif à l’ensemble du processus, vous ne pouvez pas en dépendre, car une autre instance d’exécution peut la modifier à tout moment. Vous devez utiliser les applets de commande location pour effectuer des opérations basées sur le chemin d’accès à l’aide du répertoire de travail actuel spécifique à l’instance d’exécution actuelle.

Une pile est une liste de dernier et premier sorti dans laquelle seul l’élément le plus récemment ajouté est accessible. Vous ajoutez des éléments à une pile dans l'ordre dans lequel vous les utilisez, puis les récupérez pour une utilisation dans l'ordre inverse. PowerShell vous permet de stocker les emplacements des fournisseurs dans des piles d’emplacements.

PowerShell crée une pile d’emplacements par défaut sans nom et vous pouvez créer plusieurs piles d’emplacements nommées. Si vous ne spécifiez pas de nom de pile, PowerShell utilise la pile d’emplacements active. Par défaut, l’emplacement par défaut sans nom est la pile d’emplacements active, mais vous pouvez utiliser l' `Set-Location` applet de commande pour modifier la pile d’emplacements active.

Pour gérer les piles d’emplacements, utilisez les `*-Location` applets de commande PowerShell comme suit :

- Pour ajouter un emplacement à une pile d’emplacements, utilisez l’applet de commande `Push-Location` .

- Pour obtenir un emplacement à partir d’une pile d’emplacements, utilisez l’applet de commande `Pop-Location` .

- Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** de l’applet de commande `Get-Location` .

- Pour afficher les emplacements dans une pile d’emplacements nommée, utilisez le paramètre **StackName** de l’applet de commande `Get-Location` .

- Pour créer une nouvelle pile d’emplacements, utilisez le paramètre **StackName** de l’applet de commande `Push-Location` . Si vous spécifiez une pile qui n’existe pas, `Push-Location` crée la pile.

- Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre **StackName** de l’applet de commande `Set-Location` .

La pile d'emplacements par défaut sans nom n'est entièrement accessible que s'il s'agit de la pile d'emplacements active.
Si vous définissez une pile d’emplacements nommée sur la pile d’emplacements active, vous ne pouvez plus utiliser les `Push-Location` applets de commande ou `Pop-Location` pour ajouter ou obtenir des éléments à partir de la pile par défaut ou utiliser l' `Get-Location` applet de commande pour afficher les emplacements dans la pile sans nom. Pour que la pile sans nom soit la pile active, utilisez le paramètre **StackName** de l' `Set-Location` applet de commande avec une valeur `$Null` ou une chaîne vide ( `""` ).

Vous pouvez également faire référence à `Pop-Location` par son alias intégré, `popd` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

`Pop-Location` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## LIENS CONNEXES

[Get-Location](Get-Location.md)

[Push-Location](Push-Location.md)

[Set-Location](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
