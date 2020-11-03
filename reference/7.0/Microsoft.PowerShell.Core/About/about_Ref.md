---
description: Décrit comment créer et utiliser une variable de type référence. Vous pouvez utiliser des variables de type référence pour permettre à une fonction de modifier la valeur d’une variable qui lui est transmise.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: b4848e80ae45a8c183f2747cbb678c59e36c7392
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207814"
---
# <a name="about-ref"></a>À propos de Ref

## <a name="short-description"></a>Description courte
Décrit comment créer et utiliser une variable de type référence. Vous pouvez utiliser des variables de type référence pour permettre à une fonction de modifier la valeur d’une variable qui lui est transmise.

## <a name="long-description"></a>Description longue

Vous pouvez passer des variables aux fonctions *par référence* ou *par valeur* .

Lorsque vous passez une variable *par valeur* , vous passez une copie des données.

Dans l’exemple suivant, la fonction modifie la valeur de la variable qui lui est transmise. Dans PowerShell, les entiers sont des types valeur afin qu’ils soient passés par valeur.
Par conséquent, la valeur de `$var` est inchangée en dehors de la portée de la fonction.

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

Dans l’exemple suivant, une variable contenant un `Hashtable` est passée à une fonction. `Hashtable` est un type d’objet, par défaut, il est passé à la fonction *par référence* .

Lors du passage d’une variable *par référence* , la fonction peut modifier les données et cette modification persiste après l’exécution de la fonction.

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

La fonction ajoute une nouvelle paire clé-valeur qui persiste en dehors de la portée de la fonction.

### <a name="writing-functions-to-accept-reference-parameters"></a>Écriture de fonctions pour accepter des paramètres de référence

Vous pouvez coder vos fonctions pour prendre un paramètre en tant que référence, quel que soit le type de données passé. Pour cela, vous devez spécifier le type de paramètres en tant que `System.Management.Automation.PSReference` , ou `[ref]` .

Lorsque vous utilisez des références, vous devez utiliser la `Value` propriété du `System.Management.Automation.PSReference` type pour accéder à vos données.

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

Pour passer une variable à un paramètre qui attend une référence, vous devez taper cast de la variable en tant que référence.

> [!NOTE]
> Les crochets et les parenthèses sont tous deux requis.

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a>Passage de références à des méthodes .NET

Certaines méthodes .NET peuvent vous obliger à passer une variable en tant que référence. Lorsque la définition de la méthode utilise les mots clés `in` , `out` ou `ref` sur un paramètre, elle attend une référence.

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

La `TryParse` méthode tente d’analyser une chaîne comme un entier. Si la méthode réussit, elle retourne `$true` et le résultat est stocké dans la variable que vous avez passée **par référence** .

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a>Références et étendues

Les références permettent de modifier la valeur d’une variable dans l’étendue parente dans une étendue enfant.

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

Seule la variable du type de référence a été modifiée.

## <a name="see-also"></a>Voir aussi

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Scopes](about_scopes.md)
