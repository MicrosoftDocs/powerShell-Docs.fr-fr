---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: c72cde8e626993726ae1a52206c88e20c3a7c588
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "93208878"
---
# Compare-Object

## Synopsis
Compare deux ensembles d'objets.

## Syntaxe

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## Description

L' `Compare-Object` applet de commande compare deux ensembles d’objets. Un ensemble d’objets est la **référence** , et l’autre ensemble d’objets est la **différence**.

`Compare-Object` recherche les méthodes disponibles pour comparer un objet entier. S’il ne trouve pas de méthode appropriée, il appelle les méthodes **ToString ()** des objets d’entrée et compare les résultats de la chaîne. Vous pouvez fournir une ou plusieurs propriétés à utiliser pour la comparaison. Lorsque les propriétés sont fournies, l’applet de commande compare les valeurs de ces propriétés uniquement.

Le résultat de la comparaison indique si une valeur de propriété apparaît uniquement dans l’objet de **référence** ( `<=` ) ou uniquement dans l’objet de **différence** ( `=>` ). Si le paramètre **includeequal** est utilisé, ( `==` ) indique que la valeur se trouve dans les deux objets.

Si la **référence** ou les objets de **différence** sont null ( `$null` ), `Compare-Object` génère une erreur de fin.

Certains exemples utilisent la projection pour réduire la longueur de ligne des exemples de code. Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

## Exemples

### Exemple 1 : comparer le contenu de deux fichiers texte

Cet exemple compare le contenu de deux fichiers texte. L’exemple utilise les deux fichiers texte suivants, avec chaque valeur sur une ligne distincte.

- `Testfile1.txt` contient les valeurs : Dog, Squirrel et oiseau.
- `Testfile2.txt` contient les valeurs : Cat, oiseau et Racoon.

La sortie affiche uniquement les lignes qui sont différentes entre les fichiers. `Testfile1.txt` est l’objet de **référence** ( `<=` ) et `Testfile2.txt` est l’objet de **différence** ( `=>` ). Les lignes dont le contenu apparaît dans les deux fichiers ne sont pas affichées.

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### Exemple 2 : comparer chaque ligne de contenu et exclure les différences

Cet exemple utilise les paramètres **includeequal** et **ExcludeDifferent** pour comparer chaque ligne de contenu dans deux fichiers texte.

Étant donné que la commande utilise le paramètre **ExcludeDifferent** , la sortie contient uniquement les lignes contenues dans les deux fichiers, comme indiqué par **SideIndicator** ( `==` ).

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -IncludeEqual -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### Exemple 3 : afficher la différence lors de l’utilisation du paramètre PassThru

Normalement, `Compare-Object` retourne un type **PSCustomObject** avec les propriétés suivantes :

- **InputObject** qui est comparé
- Propriété **SideIndicator** indiquant l’objet d’entrée auquel la sortie appartient

Quand vous utilisez le paramètre **PassThru** , le **type** de l’objet n’est pas modifié, mais l’instance de l’objet retourné a un **NoteProperty** ajouté nommé **SideIndicator**. **SideIndicator** affiche l’objet d’entrée auquel la sortie appartient.

Les exemples suivants illustrent les différents types de sortie.

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

Lors de l’utilisation de **PassThru** , le type d’objet d’origine ( **System. Boolean** ) est retourné. Notez que la sortie affichée par le format par défaut pour les objets **System. Boolean** n’a pas affiché la propriété **SideIndicator** . Toutefois, l’objet **System. Boolean** retourné a le **NoteProperty** ajouté.

### Exemple 4-comparer deux objets simples à l’aide de propriétés

Dans cet exemple, nous comparons deux chaînes différentes qui ont la même longueur.

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### Exemple 5 : comparaison d’objets complexes à l’aide de propriétés

Cet exemple illustre le comportement de la comparaison d’objets complexes. Dans cet exemple, nous stockons deux objets de processus différents pour différentes instances de PowerShell. Les deux variables contiennent des objets de processus portant le même nom. Lorsque les objets sont comparés sans spécifier le paramètre **Property** , l’applet de commande considère que les objets sont égaux. Notez que la valeur de l' **InputObject** est identique à celle du résultat de la méthode **ToString ()** . Étant donné que la classe **System. Diagnostics. Process** n’a pas l’interface **IComparable** , l’applet de commande convertit les objets en chaînes, puis compare les résultats.

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

Lorsque vous spécifiez des propriétés à comparer, l’applet de commande affiche les différences.

### Exemple 6 : comparaison d’objets complexes qui implémentent IComparable

Si l’objet implémente **IComparable** , l’applet de commande recherche les façons de comparer les objets. Si les objets sont de types différents, l’objet de **différence** est converti en type de **ReferenceObject** , puis comparé.

Dans cet exemple, nous comparons une chaîne à un objet **TimeSpan** . Dans le premier cas, la chaîne est convertie en **intervalle** de temps, de sorte que les objets sont égaux.

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

Dans le deuxième cas, la valeur **TimeSpan** est convertie en une chaîne, de sorte que l’objet est différent.

## Paramètres

### -CaseSensitive

Indique que les comparaisons doivent respecter la casse.

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

### -Culture

Spécifie la culture à utiliser pour les comparaisons.

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

### -DifferenceObject

Spécifie les objets qui sont comparés aux objets de **référence** .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ExcludeDifferent

Indique que cette applet de commande affiche uniquement les caractéristiques des objets comparés qui sont égaux. Les différences entre les objets sont ignorées.

Utilisez **ExcludeDifferent** avec **includeequal** pour afficher uniquement les lignes qui correspondent entre les objets de **référence** et les objets de **différence** .

Si **ExcludeDifferent** est spécifié sans **includeequal** , il n’y a pas de sortie.

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

### -IncludeEqual

**Includeequal** affiche les correspondances entre les objets de **référence** et les objets de **différence** .

Par défaut, la sortie comprend également les différences entre les objets de **référence** et les objets de **différence** .

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

### -PassThru

Quand vous utilisez le paramètre **PassThru** , `Compare-Object` omet le wrapper **PSCustomObject** autour des objets comparés et retourne les objets différents, inchangés.

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

### -Propriété

Spécifie un tableau de propriétés des objets de **référence** et de **différence** à comparer.

La valeur du paramètre **Property** peut être une nouvelle propriété calculée. La propriété calculée peut être un bloc de script ou une table de hachage. Les paires clé-valeur valides sont :

- Expression `<string>` ou `<script block>`

Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceObject

Spécifie un tableau d’objets utilisés comme référence pour la comparaison.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SyncWindow

Spécifie le nombre d’objets adjacents `Compare-Object` inspectés lors de la recherche d’une correspondance dans une collection d’objets. `Compare-Object` examine les objets adjacents lorsqu’il ne trouve pas l’objet à la même position dans une collection. La valeur par défaut est, ce qui `[Int32]::MaxValue` signifie que `Compare-Object` examine la collection d’objets entière.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Entrées

### System. Management. Automation. PSObject

Vous pouvez envoyer un objet dans le pipeline au paramètre **differenceobject** .

## Sorties

### Aucun

Si l’objet de **référence** et l’objet de **différence** sont identiques, il n’y a pas de sortie, sauf si vous utilisez le paramètre **includeequal** .

### System. Management. Automation. PSCustomObject

Si les objets sont différents, `Compare-Object` encapsule les objets qui diffèrent dans un `PSCustomObject` wrapper avec une propriété **SideIndicator** pour référencer les différences.

Quand vous utilisez le paramètre **PassThru** , le **type** de l’objet n’est pas modifié, mais l’instance de l’objet retourné a un **NoteProperty** ajouté nommé **SideIndicator**. **SideIndicator** affiche l’objet d’entrée auquel la sortie appartient.

## Notes

Lors de l’utilisation du paramètre **PassThru** , la sortie affichée dans la console peut ne pas inclure la propriété **SideIndicator** . L’affichage de format par défaut de pour le type d’objet généré par `Compare-Object` n’inclut pas la propriété **SideIndicator** . Pour plus d’informations, consultez l' [exemple 3](#ex3) de cet article.

## Liens connexes

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)
