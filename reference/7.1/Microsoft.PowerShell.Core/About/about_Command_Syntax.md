---
description: Décrit les diagrammes de syntaxe utilisés dans PowerShell.
Locale: en-US
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: 60bd9e8f29680d20be803c615f2e93572b4da12f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195358"
---
# <a name="about-command-syntax"></a>À propos de la syntaxe de commande

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit les diagrammes de syntaxe utilisés dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les applets de commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) et [obtenir-Command](xref:Microsoft.PowerShell.Core.Get-Command) affichent des diagrammes de syntaxe pour vous aider à construire correctement des commandes. Cette rubrique explique comment interpréter les diagrammes de syntaxe.

## <a name="syntax-diagrams"></a>DIAGRAMMES DE SYNTAXE

Chaque paragraphe dans un diagramme de syntaxe de commande représente un formulaire valide de la commande.

Pour construire une commande, suivez le diagramme de la syntaxe de gauche à droite. Sélectionnez parmi les paramètres facultatifs et fournissez des valeurs pour les espaces réservés.

PowerShell utilise la notation suivante pour les diagrammes de syntaxe.

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

Voici la syntaxe de l’applet de commande [New-alias](xref:Microsoft.PowerShell.Utility.New-Alias) .

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

La syntaxe est capitalisée pour des raisons de lisibilité, mais PowerShell ne respecte pas la casse.

Le diagramme de syntaxe contient les éléments suivants.

## <a name="command-name"></a>Nom de commande

Les commandes commencent toujours par un nom de commande, par exemple `New-Alias` . Tapez le nom de la commande ou son alias, par exemple « GCM » pour `Get-Command` .

## <a name="parameters"></a>Paramètres

Les paramètres d’une commande sont des options qui déterminent ce que fait la commande.
Certains paramètres acceptent une « valeur » qui est l’entrée utilisateur de la commande.

Par exemple, la `Get-Help` commande a un paramètre **Name** qui vous permet de spécifier le nom de la rubrique pour laquelle l’aide est affichée. Le nom de la rubrique est la valeur du paramètre **Name** .

Dans une commande PowerShell, les noms de paramètres commencent toujours par un trait d’Union.
Le trait d’Union indique à PowerShell que l’élément dans la commande est un nom de paramètre.

Par exemple, pour utiliser le paramètre Name de `New-Alias` , vous tapez ce qui suit :

```powershell
-Name
```

Les paramètres peuvent être obligatoires ou facultatifs. Dans un diagramme de syntaxe, les éléments facultatifs sont placés entre crochets `[ ]` .

Pour plus d’informations sur les paramètres, consultez [about_Parameters](about_Parameters.md).

## <a name="parameter-values"></a>Valeurs des paramètres

Une valeur de paramètre est l’entrée que le paramètre prend. Étant donné que Windows PowerShell est basé sur le Framework Microsoft .NET, les valeurs des paramètres sont représentées dans le diagramme de syntaxe par leur type .NET.

Par exemple, le paramètre Name de `Get-Help` prend une valeur « String », qui est une chaîne de texte, telle qu’un mot unique ou plusieurs mots placés entre guillemets.

```powershell
[-Name] <string>
```

Le type .NET d’une valeur de paramètre est placé entre crochets pointus `< >` pour indiquer qu’il s’agit d’un espace réservé pour une valeur et non d’un littéral que vous tapez dans une commande.

Pour utiliser le paramètre, remplacez l’espace réservé de type .NET par un objet qui a le type .NET spécifié.

Par exemple, pour utiliser le paramètre **Name** , tapez « -Name » suivi d’une chaîne, telle que la suivante :

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a>Paramètres sans valeurs

Certains paramètres n’acceptent pas d’entrée, donc ils n’ont pas de valeur de paramètre.
Les paramètres sans valeurs sont appelés « paramètres de commutateur », car ils fonctionnent comme des commutateurs activés/désactivés. Vous les incluez (sur) ou vous les omettez (OFF) à partir d’une commande.

Pour utiliser un paramètre de commutateur, tapez simplement le nom du paramètre, précédé d’un trait d’Union.

Par exemple, pour utiliser le paramètre **WhatIf** de l' `New-Alias` applet de commande, tapez ce qui suit :

```powershell
-WhatIf
```

## <a name="parameter-sets"></a>Jeux de paramètres

Les paramètres d’une commande sont répertoriés dans Jeux de paramètres. Les jeux de paramètres ressemblent aux paragraphes d’un diagramme de syntaxe.

L' `New-Alias` applet de commande a un jeu de paramètres, mais de nombreuses cmdlets ont plusieurs jeux de paramètres. Certains paramètres d’applet de commande sont uniques à un jeu de paramètres, tandis que d’autres apparaissent dans plusieurs jeux de paramètres. Chaque jeu de paramètres représente le format d’une commande valide. Un jeu de paramètres comprend uniquement des paramètres qui peuvent être utilisés ensemble dans une commande. Si les paramètres ne peuvent pas être utilisés dans la même commande, ils apparaissent dans des jeux de paramètres distincts.

Par exemple, l’applet de commande [obtenir-Random](xref:Microsoft.PowerShell.Utility.Get-Random) possède les jeux de paramètres suivants :

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

Le premier jeu de paramètres, qui retourne un nombre aléatoire, possède les paramètres **minimum** et **maximum** . Le deuxième jeu de paramètres, qui retourne un objet sélectionné de manière aléatoire à partir d’un ensemble d’objets, comprend les paramètres **InputObject** et **Count** . Les deux jeux de paramètres ont le paramètre **setseed** et les paramètres communs.

Ces jeux de paramètres indiquent que vous pouvez utiliser les paramètres **InputObject** et **Count** dans la même commande, mais vous ne pouvez pas utiliser les paramètres **maximum** et **Count** dans la même commande.

Vous indiquez le jeu de paramètres que vous souhaitez utiliser à l’aide des paramètres de ce jeu de paramètres.

Toutefois, chaque applet de commande possède également un jeu de paramètres par défaut. Le jeu de paramètres par défaut est utilisé lorsque vous ne spécifiez pas de paramètres propres à un jeu de paramètres. Par exemple, si vous utilisez `Get-Random` sans paramètres, Windows PowerShell part du principe que vous utilisez le jeu de paramètres **Number** et qu’il retourne un nombre aléatoire.

Dans chaque jeu de paramètres, les paramètres apparaissent dans l’ordre de position. L’ordre des paramètres dans une commande est important uniquement lorsque vous omettez les noms de paramètres facultatifs. Lorsque les noms de paramètres sont omis, PowerShell assigne des valeurs aux paramètres par position et type. Pour plus d’informations sur la position des paramètres, consultez `about_Parameters` .

## <a name="symbols-in-syntax-diagrams"></a>Symboles dans les diagrammes de syntaxe

Le diagramme de syntaxe répertorie le nom de la commande, les paramètres de commande et les valeurs de paramètre. Il utilise également des symboles pour montrer comment construire une commande valide.

Les diagrammes de syntaxe utilisent les symboles suivants :

- Un trait d’Union `-` indique un nom de paramètre. Dans une commande, tapez le trait d’Union juste avant le nom du paramètre sans espaces intermédiaires, comme indiqué dans le diagramme de syntaxe.

  Par exemple, pour utiliser le paramètre **Name** de `New-Alias` , tapez :

  ```powershell
  -Name
  ```

- Les chevrons indiquent le texte de l' `<>` espace réservé. Vous ne tapez pas les crochets pointus ni le texte de l’espace réservé dans une commande. Au lieu de cela, remplacez-le par l’élément qu’il décrit.

  Les chevrons sont utilisés pour identifier le type .NET de la valeur prise par un paramètre. Par exemple, pour utiliser le paramètre **Name** de l' `New-Alias` applet de commande, remplacez `<string>` par une chaîne, qui est un mot unique ou un groupe de mots entre guillemets.

- Les crochets `[ ]` indiquent des éléments facultatifs. Un paramètre et sa valeur peuvent être facultatifs, ou le nom d’un paramètre requis peut être facultatif.

  Par exemple, le paramètre **Description** de `New-Alias` et sa valeur sont placés entre crochets, car ils sont tous deux facultatifs.

  ```powershell
  [-Description <string>]
  ```

  Les crochets indiquent également que la valeur du paramètre name `<string>` est obligatoire, mais le nom du paramètre, « Name », est facultatif.

  ```powershell
  [-Name] <string>
  ```

- Un crochet droit et un crochet gauche `[]` ajoutés à un type .net indiquent que le paramètre peut accepter une ou plusieurs valeurs de ce type. Entrez les valeurs dans une liste séparée par des virgules.

  Par exemple, le paramètre **Name** de l' `New-Alias` applet de commande ne prend qu’une seule chaîne, mais le paramètre **Name** de l’applet de commande [obtient-process](xref:Microsoft.PowerShell.Management.Get-Process) peut prendre une ou plusieurs chaînes.

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- Les accolades `{}` indiquent une « énumération », qui est un ensemble de valeurs valides pour un paramètre.

  Les valeurs entre les accolades sont séparées par des barres verticales `|` . Ces barres indiquent un choix « exclusif ou », ce qui signifie que vous ne pouvez choisir qu’une seule valeur de l’ensemble de valeurs qui sont répertoriées à l’intérieur des accolades.

  Par exemple, la syntaxe de l' `New-Alias` applet de **commande** comprend l’énumération value suivante pour le paramètre option :

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  Les accolades et les barres verticales indiquent que vous pouvez choisir l’une des valeurs listées pour le paramètre **option** , par exemple « ReadOnly » ou « options AllScope ».

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a>Éléments facultatifs

Les crochets `[]` entourent les éléments facultatifs. Par exemple, dans la description de la syntaxe de l’applet de commande `New-Alias` , le paramètre **scope** est facultatif. Cela est indiqué dans la syntaxe par des crochets autour du nom et du type de paramètre :

```powershell
[-Scope <string>]
```

Les deux exemples suivants sont des utilisations correctes de l’applet de commande `New-Alias` :

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

Un nom de paramètre peut être facultatif même si la valeur de ce paramètre est requise. Cela est indiqué dans la syntaxe par des crochets autour du nom du paramètre, mais pas du type de paramètre, comme dans cet exemple de l’applet de commande `New-Alias` :

```powershell
[-Name] <string> [-Value] <string>
```

Les commandes suivantes utilisent correctement l' `New-Alias` applet de commande. Les commandes produisent le même résultat.

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

Si le nom du paramètre n’est pas inclus dans l’instruction comme étant typé, Windows PowerShell essaie d’utiliser la position des arguments pour assigner les valeurs aux paramètres.

L’exemple suivant n’est pas complet :

```powershell
New-Alias utd
```

Cette applet de commande requiert des valeurs pour les paramètres **Name** et **value** .

Dans les exemples de syntaxe, les crochets sont également utilisés pour nommer et effectuer un cast en types .NET Framework. Dans ce contexte, les crochets n’indiquent pas qu’un élément est facultatif.

## <a name="see-also"></a>VOIR AUSSI

- [about_Parameters](about_Parameters.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

