---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: 575f696d74e6a7aa7cf864cbb559f15a25ac1a66
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203769"
---
# Invoke-Expression

## SYNOPSIS
Exécute des commandes ou des expressions sur l'ordinateur local.

## SYNTAX

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## Description

L' `Invoke-Expression` applet de commande évalue ou exécute une chaîne spécifiée en tant que commande et retourne les résultats de l’expression ou de la commande. Sans `Invoke-Expression` , une chaîne envoyée à la ligne de commande est retournée (en écho) inchangée.

Les expressions sont évaluées et exécutées dans l’étendue actuelle. Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

> [!CAUTION]
> Prenez des précautions raisonnables lors de l’utilisation `Invoke-Expression` de l’applet de commande dans les scripts. Lorsque vous utilisez `Invoke-Expression` pour exécuter une commande entrée par l’utilisateur, vérifiez que la commande peut être exécutée en toute sécurité avant de l’exécuter. En général, il est préférable de concevoir votre script avec des options d'entrée prédéfinies, plutôt que d'autoriser des entrées libres.

## EXEMPLES

### Exemple 1 : évaluer une expression

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

Cet exemple illustre l’utilisation de `Invoke-Expression` pour évaluer une expression. Sans `Invoke-Expression` , l’expression est imprimée, mais pas évaluée.

La première commande attribue une valeur `Get-Process` (une chaîne) à la `$Command` variable.

La deuxième commande illustre le résultat de l'entrée du nom de la variable sur la ligne de commande. PowerShell renvoie la chaîne.

La troisième commande utilise `Invoke-Expression` pour évaluer la chaîne.

### Exemple 2 : exécuter un script sur l’ordinateur local

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

Ces commandes utilisent `Invoke-Expression` pour exécuter un script, TestScript.ps1, sur l’ordinateur local. Les deux commandes sont équivalentes. La première utilise le paramètre **Command** pour spécifier la commande à exécuter.
La seconde utilise un opérateur de pipeline ( `|` ) pour envoyer la chaîne de commande à `Invoke-Expression` .

### Exemple 3 : exécuter une commande dans une variable

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

Cet exemple exécute une chaîne de commande enregistrée dans la `$Command` variable.

La chaîne de commande est placée entre guillemets simples, car elle comprend une variable, `$_` , qui représente l’objet actuel. S’il est placé entre guillemets doubles, la `$_` variable est remplacée par sa valeur avant d’être enregistrée dans la `$Command` variable.

### Exemple 4 : obtenir et exécuter un exemple d’aide sur une applet de commande

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

Cette commande récupère et exécute le premier exemple de la `Get-EventLog` rubrique d’aide de l’applet de commande.

Pour exécuter un exemple d’une autre applet de commande, remplacez la valeur de la `$Cmdlet_name` variable par le nom de l’applet de commande. Et, remplacez la `$Example_number` variable par l’exemple de numéro que vous souhaitez exécuter. La commande échoue si le numéro de l’exemple n’est pas valide.

## PARAMETERS

### -Command

Spécifie la commande ou l'expression à exécuter. Tapez la commande ou l'expression, ou entrez une variable qui contient la commande ou l'expression. Le paramètre **Command** est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System. String ou PSObject

Vous pouvez diriger un objet qui représente la commande vers `Invoke-Expression` .
Utilisez la `$Input` variable Automatic pour représenter les objets d’entrée de la commande.

## SORTIES

### PSObject

Retourne la sortie générée par la commande appelée (la valeur du paramètre de **commande** ).

## REMARQUES

Dans la plupart des cas, vous appelez des expressions à l’aide de l’opérateur d’appel de PowerShell et obtenez les mêmes résultats.
L’opérateur d’appel est une méthode plus sûre. Pour plus d’informations, consultez [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-).

## LIENS CONNEXES

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)
