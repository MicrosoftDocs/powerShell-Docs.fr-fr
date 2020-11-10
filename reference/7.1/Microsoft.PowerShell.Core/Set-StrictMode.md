---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: 8773c69d638a1d04dc946cf448a44799341e663b
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390590"
---
# Set-StrictMode

## SYNOPSIS
Établit et applique des règles de codage dans les expressions, les scripts et les blocs de script.

## SYNTAXE

### Version (par défaut)

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### Désactivé

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## DESCRIPTION

L' `Set-StrictMode` applet de commande configure le mode strict pour l’étendue actuelle et toutes les étendues enfants, puis l’active et la désactive. Lorsque le mode strict est activé, PowerShell génère une erreur de fin lorsque le contenu d’une expression, d’un script ou d’un bloc de script enfreint les règles de codage de base recommandées.

Utilisez le paramètre **version** pour déterminer les règles de codage appliquées.

`Set-PSDebug -Strict` active le mode strict pour l’étendue globale. `Set-StrictMode` affecte uniquement l’étendue actuelle et ses portées enfants. Par conséquent, vous pouvez l’utiliser dans un script ou une fonction pour remplacer le paramètre hérité de la portée globale.

Lorsque `Set-StrictMode` est désactivé, PowerShell présente les comportements suivants :

- Les variables non initialisées sont supposées avoir la valeur 0 (zéro) ou `$Null` , selon le type
- Les références aux propriétés inexistantes retournent `$Null`
- Les résultats d’une syntaxe de fonction incorrecte varient selon les conditions d’erreur
- La tentative de récupération d’une valeur à l’aide d’un index non valide dans un tableau retourne `$Null`

## EXEMPLES

### Exemple 1 : activer le mode strict en tant que version 1,0

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
InvalidOperation: The variable '$a' cannot be retrieved because it has not been set.
```

Si le mode strict est défini sur la version 1,0, les tentatives de référencement des variables qui ne sont pas initialisées échouent.

### Exemple 2 : activer le mode strict en tant que version 2,0

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
InvalidOperation: The function or command was called as if it were a method. Parameters should be separated by spaces. For information about parameters, see the about_Parameters Help topic.
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$null -eq $string.Month
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$null -eq $string.Month
```

```Output
PropertyNotFoundException: The property 'Month' cannot be found on this object. Verify that the property exists.
```

Cette commande active le mode strict sur et lui affecte la version 2,0. Par conséquent, PowerShell retourne une erreur si vous utilisez la syntaxe de méthode, qui utilise des parenthèses et des virgules pour un appel de fonction ou référence des variables non initialisées ou des propriétés inexistantes.

L’exemple de sortie montre l’effet de la version 2,0 du mode strict.

Sans le mode strict version 2.0, la valeur « (3,4) » est interprétée comme un objet tableau unique auquel rien n'est ajouté. En utilisant le mode strict version 2,0, il est correctement interprété comme une syntaxe défectueuse pour l’envoi de deux valeurs.

Sans la version 2,0, la référence à la propriété **Month** inexistante d’une chaîne retourne uniquement `$Null` . En utilisant la version 2,0, elle est interprétée correctement comme une erreur de référence.

### Exemple 3 : activer le mode strict en tant que version 3,0

Si le mode strict est défini sur **off** , les index non valides ou hors limites renvoient des valeurs NULL.

```powershell
# Strict mode is off by default.
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
OperationStopped: Index was outside the bounds of the array.

InvalidArgument: Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
```

Si le mode strict est défini sur la version 3 ou une version ultérieure, les index non valides ou hors limites génèrent des erreurs.

## PARAMÈTRES

### -Désactivé

Indique que cette applet de commande désactive le mode strict pour l’étendue actuelle et toutes les étendues enfants.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version

Spécifie les conditions qui provoquent une erreur en mode strict. Ce paramètre accepte tout numéro de version PowerShell valide. Toute valeur supérieure à 3 est traitée comme la **dernière version**.

Les valeurs effectives pour ce paramètre sont les suivantes :

- 1.0
  - Interdit les références à des variables non initialisées, à l’exception des variables non initialisées dans les chaînes.
- 2.0
  - Interdit les références à des variables non initialisées. Cela comprend les variables non initialisées dans les chaînes.
  - Interdit les références aux propriétés inexistantes d’un objet.
  - Interdit les appels de fonction qui utilisent la syntaxe pour appeler des méthodes.
- 3.0
  - Interdit les références à des variables non initialisées. Cela comprend les variables non initialisées dans les chaînes.
  - Interdit les références aux propriétés inexistantes d’un objet.
  - Interdit les appels de fonction qui utilisent la syntaxe pour appeler des méthodes.
  - Interdit les index hors limites ou les index de tableau insolubles.
- Latest
  - Sélectionne la dernière version disponible. La dernière version est la plus stricte. Utilisez cette valeur pour vous assurer que les scripts utilisent la version disponible la plus stricte, même quand de nouvelles versions sont ajoutées à PowerShell.

> [!CAUTION]
> Utilisation d’une **version** des **derniers** scripts dans les scripts. La signification du **dernier** peut changer dans les nouvelles versions de PowerShell. Par conséquent, un script écrit pour une version antérieure de PowerShell qui utilise `Set-StrictMode -Version Latest` est soumis à des règles plus restrictives lorsqu’il est exécuté dans une version plus récente de PowerShell.

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

`Set-StrictMode` est effectif uniquement dans l’étendue dans laquelle il est défini et dans ses étendues enfants. Pour plus d’informations sur les étendues dans PowerShell, consultez [about_Scopes](about/about_Scopes.md).

## LIENS CONNEXES

[Set-PSDebug](Set-PSDebug.md)
