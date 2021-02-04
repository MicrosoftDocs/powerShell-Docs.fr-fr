---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: 963f99f69ff4406f94445841ad020555617dac42
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490862"
---
# Register-ArgumentCompleter

## SYNOPSIS

Inscrit un finaliseur d’argument personnalisé.

## SYNTAXE

### NativeSet

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### PowerShellSet

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## Description

L' `Register-ArgumentCompleter` applet de commande inscrit un finaliseur d’argument personnalisé. Un argument Complete vous permet de fournir une saisie semi-automatique par tabulation dynamique, au moment de l’exécution pour toute commande que vous spécifiez.

## EXEMPLES

### Exemple 1 : inscrire un finaliseur d’argument personnalisé

L’exemple suivant inscrit un argument Complete pour le paramètre **ID** de l’applet de commande `Set-TimeZone` .

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

La première commande crée un bloc de script qui prend les paramètres requis qui sont transmis quand l’utilisateur appuie sur la touche <kbd>Tab</kbd>. Pour plus d’informations, consultez la description du paramètre **scriptblock** .

Dans le bloc de script, les valeurs disponibles pour **ID** sont extraites à l’aide de l’applet de commande `Get-TimeZone` . La propriété **ID** de chaque fuseau horaire est dirigée vers l' `Where-Object` applet de commande. L' `Where-Object` applet de commande filtre tous les ID qui ne commencent pas par la valeur fournie par `$wordToComplete` , qui représente le texte que l’utilisateur a tapé avant d’appuyer sur la touche <kbd>Tab</kbd>. Les ID filtrés sont dirigés vers l’applet de commande `ForEach-Object` qui englobe chaque valeur entre guillemets, si la valeur contient des espaces.

La deuxième commande inscrit l’argument completer en passant le scriptblock, l’ID **ParameterName**  et le **CommandName** `Set-TimeZone` .

### Exemple 2 : ajouter des détails à vos valeurs de saisie semi-automatique par tabulation

L’exemple suivant remplace la saisie semi-automatique par tabulation pour le paramètre **Name** de l’applet de commande `Stop-Service` et retourne uniquement les services en cours d’exécution.

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

La première commande crée un bloc de script qui prend les paramètres requis qui sont transmis quand l’utilisateur appuie sur la touche <kbd>Tab</kbd>. Pour plus d’informations, consultez la description du paramètre **scriptblock** .

Dans le bloc de script, la première commande récupère tous les services en cours d’exécution à l’aide de l’applet de commande `Where-Object` . Les services sont dirigés vers l’applet de commande `ForEach-Object` . L' `ForEach-Object` applet de commande crée un nouvel [`[System.Management.Automation.CompletionResult]`](/dotnet/api/system.management.automation.completionresult) objet et le remplit avec les valeurs du service actuel (représenté par la variable de pipeline `$_` ).

L’objet **CompletionResult** vous permet de fournir des détails supplémentaires à chaque valeur retournée :

- **completionText** (String) : texte à utiliser comme résultat de la saisie semi-automatique. Il s’agit de la valeur envoyée à la commande.
- **listItemText** (String) : texte à afficher dans une liste, par exemple lorsque l’utilisateur appuie sur <kbd>CTRL</kbd> + <kbd>Space</kbd>. Cela est utilisé pour l’affichage uniquement et n’est pas passé à la commande quand elle est sélectionnée.
- **ResultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) : type de résultat de la saisie semi-automatique.
- **info-bulle** (String) : texte de l’info-bulle contenant les détails à afficher à propos de l’objet.
  Cela est visible lorsque l’utilisateur sélectionne un élément après avoir appuyé sur <kbd>CTRL</kbd> + <kbd>Space</kbd>.

La dernière commande montre que les services arrêtés peuvent toujours être passés manuellement à l' `Stop-Service` applet de commande. La saisie semi-automatique par tabulation est le seul aspect affecté.

### Exemple 3 : inscrire un finaliseur d’argument natif personnalisé

Vous pouvez utiliser le paramètre **Native** pour fournir la saisie semi-automatique par tabulation pour une commande native. L’exemple suivant ajoute la saisie semi-automatique par tabulation pour l' `dotnet` interface de ligne de commande (CLI).

> [!NOTE]
> La `dotnet complete` commande est disponible uniquement dans la version 2,0 et les versions ultérieures de l’interface CLI dotnet.

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

La première commande crée un bloc de script qui prend les paramètres requis qui sont transmis quand l’utilisateur appuie sur la touche <kbd>Tab</kbd>. Pour plus d’informations, consultez la description du paramètre **scriptblock** .

Dans le bloc de script, la `dotnet complete` commande est utilisée pour effectuer la saisie semi-automatique via la touche Tab.
Les résultats sont dirigés vers l’applet de commande `ForEach-Object` qui utilise la **nouvelle** méthode statique de la classe [System. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) pour créer un nouvel objet **CompletionResult** pour chaque valeur.

## PARAMETERS

### -CommandName

Spécifie le nom des commandes sous la forme d’un tableau.

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Natif

Indique que l’argument Complete est destiné à une commande Native où PowerShell ne peut pas terminer les noms de paramètres.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ParameterName

Spécifie le nom du paramètre dont l’argument est terminé. Le nom de paramètre spécifié ne peut pas être une valeur énumérée, telle que le paramètre **ForegroundColor** de l’applet de commande `Write-Host` .

Pour plus d’informations sur les enums, consultez [about_Enum](./About/about_Enum.md).

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

Spécifie les commandes à exécuter pour effectuer la saisie semi-automatique via la touche Tab. Le bloc de script que vous fournissez doit retourner les valeurs qui complètent l’entrée. Le bloc de script doit dérouler les valeurs à l’aide du pipeline ( `ForEach-Object` , `Where-Object` , etc.) ou d’une autre méthode appropriée. Le retour d’un tableau de valeurs amène PowerShell à traiter l’intégralité du tableau comme **une** valeur de saisie semi-automatique de tabulation.

Le bloc de script doit accepter les paramètres suivants dans l’ordre indiqué ci-dessous. Les noms des paramètres ne sont pas importants, car PowerShell passe les valeurs par position.

- `$commandName` (Position 0)-ce paramètre est défini sur le nom de la commande pour laquelle le bloc de script fournit la saisie semi-automatique par tabulation.
- `$parameterName` (Position 1)-ce paramètre est défini sur le paramètre dont la valeur nécessite la saisie semi-automatique par tabulation.
- `$wordToComplete` (Position 2)-ce paramètre est défini sur la valeur que l’utilisateur a fournie avant d’appuyer sur la touche <kbd>Tab</kbd>. Votre bloc de script doit utiliser cette valeur pour déterminer les valeurs de saisie semi-automatique de l’onglet.
- `$commandAst` (Position 3)-ce paramètre est défini sur l’arborescence de syntaxe abstraite (AST) pour la ligne d’entrée actuelle. Pour plus d’informations, consultez la [classe AST](/dotnet/api/system.management.automation.language.ast).
- `$fakeBoundParameters` (Position 4)-ce paramètre est défini sur une valeur Hashtable contenant le `$PSBoundParameters` pour l’applet de commande, avant que l’utilisateur ait appuyé sur la touche <kbd>Tab</kbd>. Pour plus d’informations, consultez [about_Automatic_Variables](./About/about_Automatic_Variables.md).

Lorsque vous spécifiez le paramètre **Native** , le bloc de script doit prendre les paramètres suivants dans l’ordre spécifié. Les noms des paramètres ne sont pas importants, car PowerShell passe les valeurs par position.

- `$wordToComplete` (Position 0)-ce paramètre est défini sur la valeur que l’utilisateur a fournie avant d’appuyer sur la touche <kbd>Tab</kbd>. Votre bloc de script doit utiliser cette valeur pour déterminer les valeurs de saisie semi-automatique de l’onglet.
- `$commandAst` (Position 1)-ce paramètre est défini sur l’arborescence de syntaxe abstraite (AST) pour la ligne d’entrée actuelle. Pour plus d’informations, consultez la [classe AST](/dotnet/api/system.management.automation.language.ast).
- `$cursorPosition` (Position 2)-ce paramètre est défini sur la position du curseur lorsque l’utilisateur a appuyé sur la touche <kbd>Tab</kbd>.

Vous pouvez également fournir un **ArgumentCompleter** en tant qu’attribut de paramètre. Pour plus d’informations, consultez [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](./About/about_CommonParameters.md).

## ENTRÉES

### Aucun

Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne retourne pas de sortie.

## REMARQUES

## LIENS CONNEXES
