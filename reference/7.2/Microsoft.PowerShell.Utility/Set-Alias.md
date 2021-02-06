---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: e9e80b4bf558dcf1e225868a1138979270ea304f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596917"
---
# Set-Alias

## SYNOPSIS
Crée ou modifie un alias pour une applet de commande ou une autre commande dans la session PowerShell active.

## SYNTAXE

### Valeur par défaut (par défaut)

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Set-Alias` applet de commande crée ou modifie un alias pour une applet de commande ou une commande, telle qu’une fonction, un script, un fichier ou un autre exécutable. Un alias est un autre nom qui fait référence à une applet de commande ou à une commande.
Par exemple, `sal` est l’alias de l' `Set-Alias` applet de commande. Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Une applet de commande peut avoir plusieurs alias, mais un alias ne peut être associé qu’à une seule applet de commande. Vous pouvez utiliser `Set-Alias` pour réassigner un alias existant à une autre applet de commande ou modifier les propriétés d’un alias, telles que la description.

Un alias créé ou modifié par `Set-Alias` n’est pas permanent et n’est disponible que pendant la session PowerShell active. Une fois la session PowerShell fermée, l’alias est supprimé.

## EXEMPLES

### Exemple 1 : créer un alias pour une applet de commande

Cette commande crée un alias pour une applet de commande dans la session PowerShell active.

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

L' `Set-Alias` applet de commande crée un alias dans la session PowerShell active. Le paramètre **Name** spécifie le nom de l’alias, `list` . Le paramètre **value** spécifie l’applet de commande exécutée par l’alias.

Pour exécuter l’alias, tapez `list` sur la ligne de commande PowerShell.

### Exemple 2 : réaffecter un alias existant à une autre applet de commande

Cette commande réaffecte un alias existant pour exécuter une applet de commande différente.

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

L' `Get-Alias` applet de commande utilise le paramètre **Name** pour afficher l' `list` alias. L' `list` alias est associé à l' `Get-ChildItem` applet de commande. Lorsque l' `list` alias est exécuté, les éléments du répertoire actif s’affichent.

L' `Set-Alias` applet de commande utilise le paramètre **Name** pour spécifier l' `list` alias. Le paramètre **value** associe l’alias à l’applet de commande `Get-Location` .

L' `Get-Alias` applet de commande utilise le paramètre **Name** pour afficher l' `list` alias. L' `list` alias est associé à l' `Get-Location` applet de commande. Lorsque l' `list` alias est exécuté, l’emplacement du répertoire actif est affiché.

### Exemple 3 : créer et modifier un alias en lecture seule

Cette commande crée un alias en lecture seule. L’option en lecture seule empêche toute modification involontaire d’un alias. Pour modifier ou supprimer un alias en lecture seule, utilisez le paramètre **force** .

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

L' `Set-Alias` applet de commande crée un alias dans la session PowerShell active. Le paramètre **Name** spécifie le nom de l’alias, `loc` . Le paramètre **value** spécifie l' `Get-Location` applet de commande exécutée par l’alias. Le paramètre **option** spécifie la valeur **ReadOnly** . Le paramètre **PassThru** représente l’objet alias et envoie l’objet dans le pipeline à l’applet de commande `Format-List` . `Format-List` utilise le paramètre **Property** avec un astérisque ( `*` ) pour que toutes les propriétés soient affichées. L’exemple de sortie montre une liste partielle de ces propriétés.

L' `loc` alias est modifié avec l’ajout de deux paramètres. **Description** ajoute du texte pour expliquer l’objectif de l’alias. Le paramètre **force** est nécessaire, car l' `loc` alias est en lecture seule. Si le paramètre **force** n’est pas utilisé, la modification échoue.

### Exemple 4 : créer un alias pour un fichier exécutable

Cet exemple crée un alias pour un fichier exécutable sur l’ordinateur local.

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

L' `Set-Alias` applet de commande crée un alias dans la session PowerShell active. Le paramètre **Name** spécifie le nom de l’alias, `np` . Le paramètre **value** spécifie le chemin d’accès et le nom de l’application **C:\Windows\notepad.exe**. L' `Get-Alias` applet de commande utilise le paramètre **Name** pour indiquer que l' `np` alias est associé à **notepad.exe**.

Pour exécuter l’alias, tapez `np` sur la ligne de commande PowerShell pour ouvrir **notepad.exe**.

### Exemple 5 : créer un alias pour une commande avec des paramètres

Cet exemple montre comment assigner un alias à une commande avec des paramètres.

Vous pouvez créer un alias pour une applet de commande, telle que `Set-Location` . Vous ne pouvez pas créer un alias pour une commande avec des paramètres et des valeurs, tels que `Set-Location -Path C:\Windows\System32` . Pour créer un alias pour une commande, créez une fonction qui inclut la commande, puis créez un alias pour la fonction. Pour plus d’informations, consultez [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

Une fonction nommée `CD32` est créée. La fonction utilise l' `Set-Location` applet de commande avec le paramètre **path** pour spécifier le répertoire, **C:\Windows\System32**.

L' `Set-Alias` applet de commande crée un alias pour la fonction dans la session PowerShell active. Le paramètre **Name** spécifie le nom de l’alias, `Go` . Le paramètre **value** spécifie le nom de la fonction, `CD32` .

Pour exécuter l’alias, tapez `Go` sur la ligne de commande PowerShell. La `CD32` fonction s’exécute et passe au répertoire **C:\Windows\System32**.

## PARAMETERS

### Description

Spécifie une description de l'alias. Vous pouvez entrer n'importe quelle chaîne. Si la description comprend des espaces, placez-la entre guillemets simples.

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

### -Force

Utilisez le paramètre **force** pour modifier ou supprimer un alias dont le paramètre **option** a la valeur **ReadOnly**.

Le paramètre **force** ne peut pas modifier ou supprimer un alias avec le paramètre **option** défini sur **constant**.

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

### -Name

Spécifie le nom d’un nouvel alias. Un nom d’alias peut contenir des caractères alphanumériques et des traits d’Union. Les noms d’alias ne peuvent pas être numériques, par exemple 123.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Option

Définit la valeur de la propriété **option** de l’alias. Les valeurs telles que **ReadOnly** et **constant** protègent un alias des modifications inattendues. Pour afficher la propriété **option** de tous les alias dans la session, tapez `Get-Alias | Format-Table -Property Name, Options -Autosize` .

Les valeurs acceptables pour ce paramètre sont les suivantes :

- **Options AllScope** L’alias est copié dans toutes les nouvelles étendues créées.
- **Constante** Ne peut pas être modifié ou supprimé.
- **Aucun** Ne définit aucune option et est la valeur par défaut.
- **Privé** L’alias est uniquement disponible dans l’étendue actuelle.
- **Lecture seule** Ne peut pas être modifié ou supprimé, sauf si le paramètre **force** est utilisé.
- **Unspecified**

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourne un objet qui représente l'alias. Utilisez une applet de commande format telle que `Format-List` pour afficher l’objet. Par défaut, `Set-Alias` ne génère pas de sortie.

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

### -Étendue

Spécifie l'étendue dans laquelle cet alias est valide. La valeur par défaut est **local**. Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

Les valeurs acceptables sont les suivantes :

- Global
- Local
- Blockchain privée
- Étendues numérotées
- Script

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

Spécifie le nom de l’applet de commande ou de la commande exécutée par l’alias. Le paramètre **value** est la propriété de **définition** de l’alias.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### None

`Set-Alias` n’accepte pas d’entrée du pipeline.

## SORTIES

### None ou System. Management. Automation. AliasInfo

Quand vous utilisez le paramètre **PassThru** , `Set-Alias` génère un objet **System. Management. Automation. AliasInfo** représentant l’alias. Dans le cas contraire, `Set-Alias` ne génère pas de sortie.

## REMARQUES

PowerShell comprend des alias intégrés qui sont disponibles dans chaque session PowerShell. L' `Get-Alias` applet de commande affiche les alias disponibles dans une session PowerShell.

Pour créer un alias, utilisez les applets de commande `Set-Alias` ou `New-Alias` . Dans PowerShell 6, pour supprimer un alias, utilisez l' `Remove-Alias` applet de commande. `Remove-Item` est accepté pour la compatibilité descendante comme pour les scripts créés avec des versions antérieures de PowerShell. Utilisez une commande telle que `Remove-Item -Path Alias:aliasname` .

Pour créer un alias qui est disponible dans chaque session PowerShell, ajoutez-le à votre profil PowerShell.
Pour plus d’informations, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

Un alias peut être enregistré et réutilisé dans une autre session PowerShell en procédant à une exportation et une importation. Pour enregistrer un alias dans un fichier, utilisez `Export-Alias` . Pour ajouter un alias enregistré à une nouvelle session PowerShell, utilisez `Import-Alias` .

## LIENS CONNEXES

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)

[about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Remove-Alias](Remove-Alias.md)

[Remove-Item](../Microsoft.PowerShell.Management/Remove-Item.md)

