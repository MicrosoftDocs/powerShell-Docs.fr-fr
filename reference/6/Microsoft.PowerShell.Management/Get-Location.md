---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 2ed19d8def95d9c83ae950af263bae5110e3b2f1
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "93206065"
---
# Get-Location

## SYNOPSIS
Obtient des informations sur l'emplacement de travail actif ou une pile d'emplacements.

## SYNTAX

### Emplacement (par défaut)

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [<CommonParameters>]
```

### Pile

```
Get-Location [-Stack] [-StackName <String[]>] [<CommonParameters>]
```

## Description

L' `Get-Location` applet de commande obtient un objet qui représente le répertoire actif, similaire à la commande du répertoire de travail d’impression (PWD).

Quand vous passez d’un lecteur PowerShell à un autre, PowerShell conserve votre emplacement sur chaque lecteur. Vous pouvez utiliser cette applet de commande pour rechercher votre emplacement sur chaque lecteur.

Vous pouvez utiliser cette applet de commande pour obtenir le répertoire actif au moment de l’exécution et l’utiliser dans des fonctions et des scripts, par exemple dans une fonction qui affiche le répertoire actif dans l’invite PowerShell.

Vous pouvez également utiliser cette applet de commande pour afficher les emplacements dans une pile d’emplacements. Pour plus d’informations, consultez les remarques et les descriptions des paramètres **Stack** et **StackName** .

## EXEMPLES

### Exemple 1 : afficher l’emplacement actuel de votre lecteur

Cette commande affiche votre emplacement dans le lecteur PowerShell actuel.

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

Par exemple, si vous êtes dans le `Windows` répertoire du `C:` lecteur, le chemin d’accès à ce répertoire est affiché.

### Exemple 2 : afficher votre emplacement actuel pour des lecteurs différents

Cet exemple illustre l’utilisation de `Get-Location` pour afficher votre emplacement actuel dans différents lecteurs PowerShell. `Set-Location` est utilisé pour remplacer l’emplacement par plusieurs chemins différents sur différents PSDrives.

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### Exemple 3 : récupération d’emplacements à l’aide de piles

Cet exemple montre comment utiliser les paramètres **Stack** et **StackName** de `Get-Location` pour répertorier les emplacements dans la pile d’emplacements active et les autres piles d’emplacements.

L' `Push-Location` applet de commande est utilisée pour passer à trois emplacements différents. La troisième commande Push utilise un nom de pile différent. Le paramètre **Stack** de `Get-Location` affiche le contenu de la pile par défaut. Le paramètre **StackName** de `Get-Location` affiche le contenu de la pile nommée `Stack2` .

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### Exemple 4 : personnaliser l’invite de commandes PowerShell

Cet exemple montre comment personnaliser l’invite de commandes PowerShell.

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

La fonction qui définit l’invite comprend une `Get-Location` commande, qui est exécutée quand l’invite s’affiche dans la console.

Le format de l’invite PowerShell par défaut est défini par une fonction spéciale nommée `prompt` . Vous pouvez modifier l’invite dans votre console en créant une nouvelle fonction nommée `prompt` .

Pour afficher la fonction d’invite active, tapez la commande suivante : `Get-Content Function:\prompt`

## PARAMETERS

### -PSDrive

Obtient l’emplacement actuel dans le lecteur PowerShell spécifié.

Par exemple, si vous êtes dans le `Cert:` lecteur, vous pouvez utiliser ce paramètre pour rechercher votre emplacement actuel dans le `C:` lecteur.

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

Obtient l’emplacement actuel sur le lecteur pris en charge par le fournisseur PowerShell spécifié.
Si le fournisseur spécifié prend en charge plusieurs lecteurs, cette applet de commande retourne l’emplacement sur le lecteur le plus récemment utilisé.

Par exemple, si vous êtes dans le `C:` lecteur, vous pouvez utiliser ce paramètre pour rechercher votre emplacement actuel dans les lecteurs du fournisseur de **registre** PowerShell.

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Pile

Indique que cette applet de commande affiche les emplacements ajoutés à la pile d’emplacements active. Vous pouvez ajouter des emplacements à des piles à l’aide de l’applet de commande `Push-Location` .

Pour afficher les emplacements dans une autre pile d’emplacements, utilisez le paramètre **StackName** . Pour plus d’informations sur les piles d’emplacements, consultez les [Remarques](#notes).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StackName

Spécifie, sous la forme d’un tableau de chaînes, les piles d’emplacements nommées. Entrez un ou plusieurs noms de pile d'emplacements.

Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** . Pour faire d’une pile d’emplacements la pile d’emplacements active, utilisez l’applet de commande `Set-Location` .

Cette applet de commande ne peut pas afficher les emplacements dans la pile par défaut sans nom, sauf s’il s’agit de la pile active.

```yaml
Type: System.String[]
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

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System. Management. Automation. PathInfo ou System. Management. Automation. PathInfoStack

Si vous utilisez les paramètres **Stack** ou **StackName** , cette applet de commande retourne un objet **PathInfoStack** . Sinon, elle retourne un objet **PathInfo** .

## REMARQUES

PowerShell prend en charge plusieurs instances d’exécution par processus. Chaque instance d’exécution a son propre _répertoire actif_ .
Ce n’est pas le même que `[System.Environment]::CurrentDirectory` . Ce comportement peut être un problème lors de l’appel d’API .NET ou de l’exécution d’applications natives sans fournir de chemins d’accès explicites au répertoire.
L' `Get-Location` applet de commande retourne le répertoire actif de l’instance d’exécution PowerShell actuelle.

Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs dans votre session, tapez `Get-PSProvider` . Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

Les modes d’interaction entre les paramètres **PSProvider** , **PSDrive** , **Stack** et **StackName** dépendent du fournisseur. Certaines combinaisons provoquent des erreurs, par exemple la spécification d'un lecteur et d'un fournisseur qui n'expose pas ce lecteur. Si aucun paramètre n’est spécifié, cette applet de commande retourne l’objet **PathInfo** pour le fournisseur qui contient l’emplacement de travail actuel.

Une pile est une liste de dernier sorti, premier sorti dans laquelle seul l’élément le plus récemment ajouté est accessible. Vous ajoutez des éléments à une pile dans l'ordre dans lequel vous les utilisez, puis les récupérez pour une utilisation dans l'ordre inverse. PowerShell vous permet de stocker les emplacements des fournisseurs dans des piles d’emplacements. PowerShell crée une pile d’emplacements par défaut sans nom et vous pouvez créer plusieurs piles d’emplacements nommées. Si vous ne spécifiez pas de nom de pile, PowerShell utilise la pile d’emplacements active. Par défaut, l’emplacement par défaut sans nom est la pile d’emplacements active, mais vous pouvez utiliser l' `Set-Location` applet de commande pour modifier la pile d’emplacements active.

Pour gérer les piles d’emplacements, utilisez les `*-Location` applets de commande PowerShell comme suit.

- Pour ajouter un emplacement à une pile d’emplacements, utilisez l’applet de commande `Push-Location` .

- Pour obtenir un emplacement à partir d’une pile d’emplacements, utilisez l’applet de commande `Pop-Location` .

- Pour afficher les emplacements dans la pile d’emplacements active, utilisez le paramètre **Stack** de l’applet de commande `Get-Location` . Pour afficher les emplacements dans une pile d’emplacements nommée, utilisez le paramètre **StackName** de l’applet de commande `Get-Location` .

- Pour créer une nouvelle pile d’emplacements, utilisez le paramètre **StackName** de l’applet de commande `Push-Location` .
  Si vous spécifiez une pile qui n’existe pas, `Push-Location` crée la pile.

- Pour définir une pile d’emplacements en tant que pile d’emplacements active, utilisez le paramètre **StackName** de l’applet de commande `Set-Location` .

La pile d'emplacements par défaut sans nom n'est entièrement accessible que s'il s'agit de la pile d'emplacements active.
Si vous définissez une pile d’emplacements nommée sur la pile d’emplacements active, vous ne pouvez plus utiliser les `Push-Location` applets de commande ou `Pop-Location` pour ajouter ou obtenir des éléments à partir de la pile par défaut ou utiliser cette applet de commande pour afficher les emplacements dans la pile sans nom. Pour que la pile sans nom soit la pile active, utilisez le paramètre **StackName** de l' `Set-Location` applet de commande avec une valeur `$null` ou une chaîne vide ( `""` ).

## LIENS CONNEXES

[Pop-Location](Pop-Location.md)

[Push-Location](Push-Location.md)

[Set-Location](Set-Location.md)
