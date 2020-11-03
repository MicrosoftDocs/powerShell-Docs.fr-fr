---
description: Décrit les opérateurs qui fonctionnent avec les types de Microsoft .NET.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 6b4b0f2eea28ddd5544174d01359491808e2e653
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208405"
---
# <a name="about-type-operators"></a>À propos des opérateurs de type

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit les opérateurs qui fonctionnent avec les types de Microsoft .NET.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les opérateurs de type booléen ( `-is` et `-isNot` ) indiquent si un objet est une instance d’un type .net spécifié. L' `-is` opérateur retourne la valeur **true** si le type correspond à et la valeur **false** dans le cas contraire. L' `-isNot` opérateur retourne la valeur **false** si le type correspond à et la valeur **true** dans le cas contraire.

L' `-as` opérateur tente de convertir l’objet d’entrée dans le type .net spécifié. Si elle réussit, elle retourne l’objet converti. En cas d’échec, elle retourne `$null` . Elle ne retourne pas d’erreur.

Le tableau suivant répertorie les opérateurs de type dans PowerShell.

|Opérateur|Description                |Exemple                          |
|--------|---------------------------|---------------------------------|
|`-is`   |Retourne la valeur TRUE lorsque l’entrée|`(get-date) -is [DateTime]`      |
|        |est une instance du      |`True`                           |
|        |type .NET spécifié.       |                                 |
|`-isNot`|Retourne la valeur TRUE lorsque l’entrée|`(get-date) -isNot [DateTime]`   |
|        |n’est pas une instance du     |`False`                          |
|        |type de specified.NET.        |                                 |
|`-as`   |Convertit l’entrée en  |`"5/7/07" -as [DateTime]`        |
|        |type .NET spécifié.       |`Monday, May 7, 2007 12:00:00 AM`|

La syntaxe des opérateurs de type est la suivante :

```powershell
<input> <operator> [.NET type]
```

Vous pouvez également utiliser la syntaxe suivante :

```powershell
<input> <operator> ".NET type"
```

Le type .NET peut être écrit sous la forme d’un nom de type entre crochets ou une chaîne, telle que `[DateTime]` ou `"DateTime"` pour **System. DateTime** . Si le type ne se trouve pas à la racine de l’espace de noms System, spécifiez le nom complet du type d’objet. Vous pouvez omettre « System. ». Par exemple, pour spécifier **System. Diagnostics. Process** , entrez `[System.Diagnostics.Process]` , `[Diagnostics.Process]` ou `"Diagnostics.Process"` .

Les opérateurs de type opèrent toujours sur l’objet d’entrée dans son ensemble. Autrement dit, si l’objet d’entrée est une collection, il s’agit du type de _collection_ qui est testé, et non des types des _éléments_ de la collection.

### <a name="-isisnot-operators"></a>-is/isNot, opérateurs

Les opérateurs de type **booléen** ( `-is` et `-isNot` ) retournent toujours une valeur **booléenne** , même si l’entrée est une collection d’objets.

Si `<input>` est un type qui est identique à ou qui est _dérivé_ du type .net, l' `-is` opérateur retourne `$True` .

Par exemple, le type **DirectoryInfo** est dérivé du type **FileSystemInfo** . Par conséquent, ces deux exemples renvoient la **valeur true** .

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

L' `-is` opérateur peut également faire correspondre des interfaces si `<input>` implémente l’interface dans la comparaison. Dans cet exemple, l’entrée est un tableau. Les tableaux implémentent l’interface **System. Collections. IList** .

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a>opérateur as

L' `-as` opérateur tente de convertir l’objet d’entrée dans le type .net spécifié. Si elle réussit, elle retourne l’objet converti. En cas d’échec, elle retourne `$null` . Elle ne retourne pas d’erreur.

Si le `<input>` est un type _dérivé_ du type .net, `-as` _passe par_ l’objet d’entrée retourné inchangé. Par exemple, le type **DirectoryInfo** est dérivé du type **FileSystemInfo** . Par conséquent, le type d’objet est inchangé dans l’exemple suivant :

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a>La conversion du type DateTime est dépendante de la culture

Contrairement au cast de type, `[DateTime]` la conversion en type à l’aide de l' `-as` opérateur fonctionne uniquement avec les chaînes mises en forme selon les règles de la culture actuelle.

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

Pour rechercher le type .NET d’un objet, utilisez l' `Get-Member` applet de commande. Ou bien, utilisez la méthode **GetType** de tous les objets avec la propriété **FullName** de cette méthode. Par exemple, l’instruction suivante obtient le type de la valeur de retour d’une `Get-Culture` commande :

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a>EXEMPLES

Les exemples suivants illustrent certaines utilisations des opérateurs de type :

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

L’exemple suivant montre que lorsque l’entrée est une collection d’objets, le type de correspondance est le type .NET de la collection, et non le type des objets individuels dans la collection.

Dans cet exemple, bien que les `Get-Culture` `Get-UICulture` applets de commande et retournent des objets **System. Globalization. CultureInfo** , une collection de ces objets est un tableau System. Object.

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

Les exemples suivants montrent comment utiliser l' `-as` opérateur.

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

L’exemple suivant montre que lorsque l' `-as` opérateur ne peut pas convertir l’objet d’entrée en type .net, il retourne `$null` .

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a>VOIR AUSSI

[about_Operators](about_Operators.md)
