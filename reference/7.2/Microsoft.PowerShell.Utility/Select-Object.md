---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 80882d27c9c8fa2d7f9e1c8ca00a02cf73ae94e6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596099"
---
# Select-Object

## SYNOPSIS
Sélectionne des objets ou des propriétés d'objet.

## SYNTAXE

### DefaultParameter (par défaut)

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### SkipLastParameter

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### IndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### SkipIndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## Description

L' `Select-Object` applet de commande sélectionne les propriétés spécifiées d’un objet ou d’un ensemble d’objets. Elle peut également sélectionner des objets uniques, un nombre spécifié d'objets ou des objets à une position spécifiée dans un tableau.

Pour sélectionner des objets dans une collection, utilisez les paramètres **First**, **Last**, **Unique**, **Skip** et **Index**. Pour sélectionner des propriétés d'objet, utilisez le paramètre **Property**. Lorsque vous sélectionnez Propriétés, `Select-Object` retourne de nouveaux objets qui ont uniquement les propriétés spécifiées.

À compter de Windows PowerShell 3,0, `Select-Object` comprend une fonctionnalité d’optimisation qui empêche les commandes de créer et de traiter des objets qui ne sont pas utilisés.

Quand vous incluez une `Select-Object` commande avec le **premier** paramètre ou les paramètres d' **index** dans un pipeline de commande, PowerShell arrête la commande qui génère les objets dès que le nombre d’objets sélectionné est généré, même lorsque la commande qui génère les objets apparaît avant la `Select-Object` commande dans le pipeline. Pour désactiver ce comportement d'optimisation, utilisez le paramètre **Wait**.

## EXEMPLES

### Exemple 1 : sélectionner des objets par propriété

Cet exemple crée des objets qui ont les propriétés **Name**, **ID** et Working Set (**WS**) des objets Process.

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### Exemple 2 : sélectionner des objets par propriété et mettre en forme les résultats

Cet exemple obtient des informations sur les modules utilisés par les processus sur l’ordinateur. Elle utilise l' `Get-Process` applet de commande pour récupérer le processus sur l’ordinateur.

Elle utilise l' `Select-Object` applet de commande pour générer un tableau d' `[System.Diagnostics.ProcessModule]` instances, tel qu’il est contenu dans la propriété **modules** de chaque instance de `System.Diagnostics.Process` sortie de `Get-Process` .

Le paramètre **Property** de l' `Select-Object` applet de commande sélectionne les noms des processus. Cela ajoute un `ProcessName` **NoteProperty** à chaque `[System.Diagnostics.ProcessModule]` instance et le remplit avec la valeur de la propriété **ProcessName** du processus actuel.

Enfin, `Format-List` l’applet de commande est utilisée pour afficher le nom et les modules de chaque processus dans une liste.

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### Exemple 3 : sélectionner les processus utilisant le plus de mémoire

Cet exemple obtient les cinq processus qui utilisent le plus de mémoire. L' `Get-Process` applet de commande obtient les processus sur l’ordinateur. L' `Sort-Object` applet de commande trie les processus en fonction de l’utilisation de la mémoire (plage de travail), et l’applet de commande `Select-Object` sélectionne uniquement les cinq derniers membres du tableau d’objets résultant.

Le paramètre **Wait** n’est pas requis dans les commandes qui incluent l’applet de commande `Sort-Object` , car `Sort-Object` traite tous les objets, puis retourne une collection. L' `Select-Object` optimisation est disponible uniquement pour les commandes qui retournent des objets individuellement au fur et à mesure de leur traitement.

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### Exemple 4 : sélectionner des caractères uniques d’un tableau

Cet exemple utilise le paramètre **unique** de `Select-Object` pour récupérer des caractères uniques à partir d’un tableau de caractères.

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### Exemple 5 : sélectionner les événements les plus récents et les plus anciens dans le journal des événements

Cet exemple obtient le premier (dernier) et le dernier événement (le plus ancien) dans le journal des événements Windows PowerShell.

`Get-EventLog` Obtient tous les événements dans le journal Windows PowerShell et les enregistre dans la `$a` variable.
Ensuite, `$a` est dirigé vers l' `Select-Object` applet de commande. La `Select-Object` commande utilise le paramètre **index** pour sélectionner des événements dans le tableau d’événements de la `$a` variable. L'index du premier événement est 0. L’index du dernier événement est le nombre d’éléments dans `$a` moins 1.

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### Exemple 6 : sélectionner tout, sauf le premier objet

Cet exemple crée une session PSSession sur chacun des ordinateurs figurant dans les fichiers de Servers.txt, à l’exception du premier.

`Select-Object` sélectionne tous les ordinateurs sauf le premier dans une liste de noms d’ordinateurs. La liste des ordinateurs qui en résulte est définie en tant que valeur du paramètre **ComputerName** de l’applet de commande `New-PSSession` .

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### Exemple 7 : renommer des fichiers et en sélectionner plusieurs à examiner

Cet exemple ajoute un suffixe « -RO » aux noms de base des fichiers texte qui ont l’attribut de lecture seule, puis affiche les cinq premiers fichiers pour que l’utilisateur puisse voir un exemple de l’effet.

`Get-ChildItem` utilise le paramètre dynamique **ReadOnly** pour obtenir les fichiers en lecture seule. Les fichiers résultants sont dirigés vers l’applet de commande `Rename-Item` , qui renomme le fichier. Elle utilise le paramètre **PassThru** de `Rename-Item` pour envoyer les fichiers renommés à l' `Select-Object` applet de commande, qui sélectionne les 5 premiers à afficher.

Le paramètre **Wait** de `Select-Object` empêche PowerShell d’arrêter l' `Get-ChildItem` applet de commande après avoir extrait les cinq premiers fichiers texte en lecture seule. Sans ce paramètre, seuls les cinq premiers fichiers en lecture seule seraient renommés.

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### Exemple 8 : illustrer les subtilités du paramètre-ExpandProperty

Cet exemple illustre les subtilités du paramètre **ExpandProperty** .

Notez que la sortie générée était un tableau d' `[System.Int32]` instances. Les instances sont conformes aux règles de mise en forme standard de la **vue sortie**. Cela est vrai pour toutes les propriétés *développées* . Si les objets en sortie ont un format standard spécifique, la propriété développée peut ne pas être visible.

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### Exemple 9 : créer des propriétés personnalisées sur des objets

L’exemple suivant illustre l’utilisation `Select-Object` de pour ajouter une propriété personnalisée à n’importe quel objet.
Lorsque vous spécifiez un nom de propriété qui n’existe pas, `Select-Object` crée cette propriété en tant que **NoteProperty** sur chaque objet passé.

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### Exemple 10 : créer des propriétés calculées pour chaque InputObject

Cet exemple montre comment utiliser `Select-Object` pour ajouter des propriétés calculées à votre entrée. Le passage d’un **scriptblock** au paramètre **Property** entraîne l' `Select-Object` évaluation de l’expression sur chaque objet passé et l’ajout des résultats à la sortie. Dans le **scriptblock**, vous pouvez utiliser la `$_` variable pour référencer l’objet actuel dans le pipeline.

Par défaut, `Select-Object` utilise la chaîne **scriptblock** comme nom de la propriété. À l’aide d’une **Hashtable**, vous pouvez étiqueter la sortie de votre **scriptblock** en tant que propriété personnalisée ajoutée à chaque objet. Vous pouvez ajouter plusieurs propriétés calculées à chaque objet passé à `Select-Object` .

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## PARAMETERS

### -ExcludeProperty

Spécifie les propriétés que cette applet de commande exclut de l’opération. Les caractères génériques sont autorisés.

À compter de PowerShell 6, il n’est plus nécessaire d’inclure le paramètre **Property** pour que **ExcludeProperty** fonctionne.

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ExpandProperty

Spécifie une propriété à sélectionner et indique qu'une tentative doit être effectuée pour développer cette propriété.

- Si la propriété spécifiée est un tableau, chaque valeur du tableau est incluse dans la sortie.
- Si la propriété spécifiée est un objet, les propriétés des objets sont développées pour chaque **InputObject**

Dans les deux cas, le **type** de sortie d’objets correspondra au **type** de la propriété développée.

Si le paramètre **Property** est spécifié, `Select-Object` tente d’ajouter chaque propriété sélectionnée en tant que **NoteProperty** à chaque objet sorti.

> [!WARNING]
> Si vous recevez l’erreur : la propriété Select : ne peut pas être traitée, car la propriété `<PropertyName>` existe déjà, prenez en compte les éléments suivants.
> Notez que, lors de l’utilisation `-ExpandProperty` de, `Select-Object` ne peut pas remplacer une propriété existante.
> Cela signifie que :
>
> - Si l’objet développé a une propriété du même nom, une erreur se produit.
> - Si l’objet *sélectionné* a une propriété du même nom qu’une propriété d’objets *développés* , une erreur se produit.

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -First

Spécifie le nombre d'objets à sélectionner à partir du début d'un tableau d'objets d'entrée.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Index

Sélectionne des objets dans un tableau en fonction de leurs valeurs d'index. Entrez les index dans une liste séparée par des virgules. Les index d'un tableau commencent à 0, où 0 représente la première valeur et (n-1) représente la dernière valeur.

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie des objets à envoyer à l'applet de commande via le pipeline. Ce paramètre vous permet de diriger des objets vers `Select-Object` .

Lorsque vous transmettez des objets au paramètre **InputObject** , au lieu d’utiliser le pipeline, `Select-Object` traite l' **InputObject** comme un objet unique, même si la valeur est une collection. Il est recommandé d’utiliser le pipeline lors du passage de collections à `Select-Object` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Dernier

Spécifie le nombre d'objets à sélectionner à partir de la fin d'un tableau d'objets d'entrée.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Propriété

Spécifie les propriétés à sélectionner. Ces propriétés sont ajoutées en tant que membres **NoteProperty** aux objets de sortie. Les caractères génériques sont autorisés.

La valeur du paramètre **Property** peut être une nouvelle propriété calculée. Pour créer une propriété calculée, utilisez une table de hachage.

Les clés valides sont les suivantes :

- Nom (ou étiquette)- `<string>`
- Expression `<string>` ou `<script block>`

Pour plus d’informations, consultez [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Ignorer

Ignore (ne sélectionne pas) le nombre spécifié d'éléments. Par défaut, le paramètre **Skip** est compté à partir du début du tableau ou de la liste d’objets, mais si la commande utilise le **dernier** paramètre, elle est comptabilisée à partir de la fin de la liste ou du tableau.

Contrairement au paramètre **Index**, qui commence le comptage à 0, le paramètre **Skip** commence à 1.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipLast

Ignore (ne sélectionne pas) le nombre spécifié d’éléments à partir de la fin de la liste ou du tableau. Fonctionne de la même façon que l’utilisation de **Skip** avec le **dernier** paramètre.

Contrairement au paramètre **index** , qui commence à compter à 0, le paramètre **SkipLast** commence à 1.

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Unique

Spécifie que si un sous-ensemble des objets d'entrée a des propriétés et des valeurs identiques, un seul membre du sous-ensemble est sélectionné.

Ce paramètre respecte la casse. Par conséquent, les chaînes qui diffèrent uniquement par la casse sont considérées comme uniques.

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

### -Wait

Indique que l’applet de commande désactive l’optimisation. PowerShell exécute les commandes dans l’ordre dans lequel elles apparaissent dans le pipeline de commande et leur permet de générer tous les objets. Par défaut, si vous incluez une `Select-Object` commande avec les paramètres **First** ou **index** dans un pipeline de commande, PowerShell arrête la commande qui génère les objets dès que le nombre d’objets sélectionné est généré.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipIndex

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger n’importe quel objet vers `Select-Object` .

## SORTIES

### System. Management. Automation. PSObject

## REMARQUES

- Vous pouvez également faire référence à l’applet de commande `Select-Object` par son alias intégré, `select` . Pour plus d’informations, consultez [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

- La fonctionnalité d’optimisation de `Select-Object` est disponible uniquement pour les commandes qui écrivent des objets dans le pipeline au fur et à mesure de leur traitement. Elle n'a pas d'effet sur les commandes qui placent les objets traités dans une mémoire tampon et les écrivent sous forme de collection. Écrire immédiatement les objets est une pratique recommandée dans la conception des applets de commande. Pour plus d’informations, consultez _écrire des enregistrements uniques dans le pipeline_ dans [conseils de développement fortement encouragés](/powershell/scripting/developer/windows-powershell).

## LIENS CONNEXES

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Group-Object](Group-Object.md)

[Sort-Object](Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
