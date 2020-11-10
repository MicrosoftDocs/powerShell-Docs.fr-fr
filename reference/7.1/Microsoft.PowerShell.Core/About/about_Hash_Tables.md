---
description: Décrit comment créer, utiliser et trier des tables de hachage dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: 26d5aad01833bc564ad65f2dcd141c7f57042431
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391389"
---
# <a name="about-hash-tables"></a>À propos des tables de hachage

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit comment créer, utiliser et trier des tables de hachage dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Une table de hachage, également appelée un dictionnaire ou un tableau associatif, est une structure de données compacte qui stocke une ou plusieurs paires clé/valeur. Par exemple, une table de hachage peut contenir une série d’adresses IP et de noms d’ordinateurs, où les adresses IP sont les clés et les noms d’ordinateur sont les valeurs, ou vice versa.

Dans PowerShell, chaque table de hachage est un objet Hashtable (System. Collections. Hashtable). Vous pouvez utiliser les propriétés et les méthodes des objets Hashtable dans PowerShell.

À compter de PowerShell 3,0, vous pouvez utiliser l’attribut [Ordered] pour créer un dictionnaire ordonné (System. Collections. Specialized. OrderedDictionary) dans PowerShell.

Les dictionnaires ordonnés diffèrent des tables de hachage dans le sens où les clés apparaissent toujours dans l’ordre dans lequel vous les répertoriez. L’ordre des clés dans une table de hachage n’est pas déterminé.

Les clés et la valeur des tables de hachage sont également des objets .NET. Ils sont le plus souvent des chaînes ou des entiers, mais ils peuvent avoir n’importe quel type d’objet. Vous pouvez également créer des tables de hachage imbriquées, dans lesquelles la valeur d’une clé est une autre table de hachage.

Les tables de hachage sont fréquemment utilisées, car elles sont très efficaces pour rechercher et récupérer des données. Vous pouvez utiliser des tables de hachage pour stocker des listes et créer des propriétés calculées dans PowerShell. Et PowerShell a une applet de commande, ConvertFrom-StringData, qui convertit les chaînes en une table de hachage.

### <a name="syntax"></a>Syntaxe

La syntaxe d’une table de hachage est la suivante :

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

La syntaxe d’un dictionnaire ordonné est la suivante :

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

L’attribut [Ordered] a été introduit dans PowerShell 3,0.

### <a name="creating-hash-tables"></a>Création de tables de hachage

Pour créer une table de hachage, suivez les instructions ci-dessous :

- Commencez la table de hachage par un arobase (@).
- Placez la table de hachage entre accolades ( {} ).
- Entrez une ou plusieurs paires clé/valeur pour le contenu de la table de hachage.
- Utilisez un signe égal (=) pour séparer chaque clé de sa valeur.
- Utilisez un point-virgule (;) ou un saut de ligne pour séparer les paires clé/valeur.
- La clé qui contient des espaces doit être placée entre guillemets. Les valeurs doivent être des expressions PowerShell valides. Les chaînes doivent apparaître entre guillemets, même si elles n’incluent pas d’espaces.
- Pour gérer la table de hachage, enregistrez-la dans une variable.
- Lorsque vous assignez une table de hachage triée à une variable, placez l’attribut [Ordered] avant le symbole « @ ». Si vous le placez avant le nom de la variable, la commande échoue.

Pour créer une table de hachage vide dans la valeur de $hash, tapez :

```powershell
$hash = @{}
```

Vous pouvez également ajouter des clés et des valeurs à une table de hachage quand vous la créez. Par exemple, l’instruction suivante crée une table de hachage avec trois clés.

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a>Création de dictionnaires ordonnés

Vous pouvez créer un dictionnaire ordonné en ajoutant un objet de type OrderedDictionary, mais le moyen le plus simple de créer un dictionnaire ordonné est d’utiliser l’attribut [Ordered].

L’attribut [Ordered] est introduit dans PowerShell 3,0.

Placez l’attribut juste avant le symbole « @ ».

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

Vous pouvez utiliser des dictionnaires ordonnés de la même façon que vous utilisez des tables de hachage.
L’un ou l’autre type peut être utilisé comme valeur des paramètres qui acceptent une table de hachage ou un dictionnaire (iDictionary).

Vous ne pouvez pas utiliser l’attribut [Ordered] pour convertir ou caster une table de hachage. Si vous placez l’attribut ordered avant le nom de la variable, la commande échoue avec le message d’erreur suivant.

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

Pour corriger l’expression, déplacez l’attribut [Ordered].

```powershell
PS C:\> $hash = [ordered]@{}
```

Vous pouvez convertir un dictionnaire ordonné en table de hachage, mais vous ne pouvez pas récupérer l’attribut ordonné, même si vous effacez la variable et entrez de nouvelles valeurs. Pour rétablir la commande, vous devez supprimer et recréer la variable.

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a>Affichage des tables de hachage

Pour afficher une table de hachage qui est enregistrée dans une variable, tapez le nom de la variable.
Par défaut, les tables de hachage sont affichées sous la forme d’une table avec une colonne pour les clés et une pour les valeurs.

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

Les tables de hachage ont des propriétés Keys et values. Utilisez la notation par points pour afficher toutes les clés ou toutes les valeurs.

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

Chaque nom de clé est également une propriété de la table de hachage, et sa valeur est la valeur de la propriété Key-Name. Utilisez le format suivant pour afficher les valeurs de propriété.

```powershell
$hashtable.<key>
<value>
```

Par exemple :

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

Si le nom de la clé est en conflit avec l’un des noms de propriété du type HashTable, vous pouvez utiliser `PSBase` pour accéder à ces propriétés. Par exemple, si le nom de clé est `keys` et que vous souhaitez retourner la collection de clés, utilisez la syntaxe suivante :

```powershell
$hashtable.PSBase.Keys
```

Les tables de hachage ont une propriété Count qui indique le nombre de paires clé-valeur dans la table de hachage.

```powershell
C:\PS> $hash.count
3
```

Les tables de table de hachage ne sont pas des tableaux. vous ne pouvez donc pas utiliser un entier comme index dans la table de hachage, mais vous pouvez utiliser un nom de clé pour indexer la table de hachage.
Si la clé est une valeur de chaîne, mettez le nom de la clé entre guillemets.

Par exemple :

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a>Ajout et suppression de clés et de valeurs

Pour ajouter des clés et des valeurs à une table de hachage, utilisez le format de commande suivant.

```powershell
$hash["<key>"] = "<value>"
```

Par exemple, pour ajouter une clé « Time » avec la valeur « Now » à la table de hachage, utilisez le format d’instruction suivant.

```powershell
$hash["Time"] = "Now"
```

Vous pouvez également ajouter des clés et des valeurs à une table de hachage à l’aide de la méthode Add de l’objet System. Collections. Hashtable. La méthode Add a la syntaxe suivante :

```powershell
Add(Key, Value)
```

Par exemple, pour ajouter une clé « Time » avec la valeur « Now » à la table de hachage, utilisez le format d’instruction suivant.

```powershell
$hash.Add("Time", "Now")
```

En outre, vous pouvez ajouter des clés et des valeurs à une table de hachage en utilisant l’opérateur d’addition (+) pour ajouter une table de hachage à une table de hachage existante. Par exemple, l’instruction suivante ajoute une clé « Time » avec la valeur « Now » à la table de hachage dans la variable $hash.

```powershell
$hash = $hash + @{Time="Now"}
```

Vous pouvez également ajouter des valeurs stockées dans des variables.

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

Vous ne pouvez pas utiliser un opérateur de soustraction pour supprimer une paire clé/valeur d’une table de hachage, mais vous pouvez utiliser la méthode Remove de l’objet Hashtable. La méthode Remove prend la clé comme valeur.

La méthode Remove a la syntaxe suivante :

```
Remove(Key)
```

Par exemple, pour supprimer la paire clé/valeur de date/heure de la table de hachage dans la valeur de la variable $hash, tapez :

```powershell
$hash.Remove("Time")
```

Vous pouvez utiliser toutes les propriétés et méthodes des objets Hashtable dans PowerShell, y compris Contains, Clear, clone et CopyTo. Pour plus d’informations sur les objets Hashtable, consultez [System. Collections. Hashtable](/dotnet/api/system.collections.hashtable).

### <a name="object-types-in-hashtables"></a>Types d’objets dans les tables de hachage

Les clés et les valeurs d’une table de hachage peuvent avoir n’importe quel type d’objet .NET, et une seule table de hachage peut avoir des clés et des valeurs de plusieurs types.

L’instruction suivante crée une table de hachage de chaînes de nom de processus et traite les valeurs d’objet et les enregistre dans la `$p` variable.

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

Vous pouvez afficher la table de hachage dans `$p` et utiliser les propriétés Key-Name pour afficher les valeurs.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

Les clés d’une table de hachage peuvent également être de n’importe quel type .NET. L’instruction suivante ajoute une paire clé/valeur à la table de hachage dans la `$p` variable. La clé est un objet de service qui représente le service WinRM et la valeur est l’état actuel du service.

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

Vous pouvez afficher la nouvelle paire clé/valeur et y accéder à l’aide des mêmes méthodes que celles que vous utilisez pour d’autres paires dans la table de hachage.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

Les clés et les valeurs d’une table de hachage peuvent également être des objets Hashtable. L’instruction suivante ajoute une paire clé/valeur à la table de hachage dans la `$p` variable dans laquelle la clé est une chaîne, Hash2, et la valeur est une table de hachage avec trois paires clé/valeur.

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

Vous pouvez afficher les nouvelles valeurs et y accéder à l’aide des mêmes méthodes.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a>Tri des clés et des valeurs

Les éléments d’une table de hachage ne sont pas triés intrinsèquement. Les paires clé/valeur peuvent apparaître dans un ordre différent chaque fois que vous les affichez.

Bien que vous ne puissiez pas trier une table de hachage, vous pouvez utiliser la méthode GetEnumerator des tables de hachage pour énumérer les clés et les valeurs, puis utiliser l’applet de commande Sort-Object pour trier les valeurs énumérées à afficher.

Par exemple, les commandes suivantes énumèrent les clés et les valeurs de la table de hachage dans la `$p` variable, puis trient les clés par ordre alphabétique.

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

La commande suivante utilise la même procédure pour trier les valeurs de hachage dans l’ordre décroissant.

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a>Création d’objets à partir de tables de hachage

À compter de PowerShell 3,0, vous pouvez créer un objet à partir d’une table de hachage de propriétés et de valeurs de propriété.

La syntaxe est la suivante :

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

Cette méthode fonctionne uniquement pour les classes qui ont un constructeur null, autrement dit, un constructeur qui n’a aucun paramètre. Les propriétés de l’objet doivent être publiques et définissables.

Pour plus d’informations, consultez [about_Object_Creation](about_Object_Creation.md).

### <a name="convertfrom-stringdata"></a>ConvertFrom-StringData

L' `ConvertFrom-StringData` applet de commande convertit une chaîne ou une chaîne ici de paires clé/valeur en une table de hachage. Vous pouvez utiliser l' `ConvertFrom-StringData` applet de commande en toute sécurité dans la section des données d’un script, et vous pouvez l’utiliser avec l' `Import-LocalizedData` applet de commande pour afficher les messages utilisateur dans la culture de l’interface utilisateur (IU) de l’utilisateur actuel.

Ici-les chaînes sont particulièrement utiles lorsque les valeurs de la table de hachage sont des guillemets. Pour plus d’informations sur les chaînes ici, consultez [about_Quoting_Rules](about_Quoting_Rules.md).

L’exemple suivant montre comment créer une chaîne « ici- » des messages utilisateur dans l’exemple précédent et comment utiliser `ConvertFrom-StringData` pour les convertir d’une chaîne en une table de hachage.

La commande suivante crée une chaîne ici-String des paires clé/valeur, puis l’enregistre dans la \$ variable chaîne.

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

Cette commande utilise l’applet de commande ConvertFrom-StringData pour convertir la chaîne here en une table de hachage.

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

Pour plus d’informations sur les chaînes ici, consultez [about_Quoting_Rules](about_Quoting_Rules.md).

## <a name="see-also"></a>VOIR AUSSI

[about_Arrays](about_Arrays.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[System.Collections.Hashtable](/dotnet/api/system.collections.hashtable)
