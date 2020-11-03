---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convert-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-String
ms.openlocfilehash: 29ec9e21277bae02ab94ce5e862787c86a87b439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203361"
---
# Convert-String

## SYNOPSIS
Met en forme une chaîne pour qu’elle corresponde à des exemples.

## SYNTAX

```
Convert-String [-Example <System.Collections.Generic.List`1[System.Management.Automation.PSObject]>]
 -InputObject <String> [<CommonParameters>]
```

## Description

L’applet de commande **Convert-String** met en forme une chaîne pour qu’elle corresponde au format des exemples.

## EXEMPLES

### Exemple 1 : convertir le format d’une chaîne

```powershell
"Mu Han", "Jim Hance", "David Ahs", "Kim Akers" | Convert-String -Example "Ed Wilson=Wilson, E."
```

```output
Han, M.
Hance, J.
Ahs, D.
Akers, K.
```

La première commande crée un tableau qui contient le prénom et le nom.

La deuxième commande met en forme les noms en fonction de l’exemple.
Il place le nom en premier dans la sortie, suivi d’un initial.

### Exemple 2 : simplifier le format d’une chaîne

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=last, first"
```

```output
Bach, Johann
Mozart, Wolfgang
Chopin, Frederic
Brahms, Johannes
```

La première commande crée un tableau qui contient les noms First, Middle et Last.
Notez que la dernière entrée n’a pas de deuxième prénom.

La deuxième commande met en forme les noms en fonction de l’exemple.
Il place le nom de famille en premier dans la sortie, suivi du prénom.
Tous les noms de milieu supprimés ; l’entrée sans le deuxième nom est gérée correctement.

### Exemple 3 : gestion de la sortie quand les chaînes ne correspondent pas à l’exemple

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=middle, first"
```

```output
Sebastian, Johann
Amadeus, Wolfgang
Francois, Frederic
```

La première commande crée un tableau qui contient les noms First, Middle et Last.
Notez que la dernière entrée n’a pas de deuxième prénom.

La deuxième commande met en forme les noms en fonction de l’exemple.
Il place le **deuxième** prénom dans la sortie, suivi du prénom.
La dernière entrée dans **$Composers** est ignorée, car elle ne correspond pas à l’exemple de modèle : elle n’a pas de deuxième prénom.

### Exemple 4 : prudence avec les espaces de beauté

```powershell
$composers = @("Antonio Vivaldi", "Richard Wagner ", "Franz Schubert", "Johannes Brahms ")
$composers | Convert-String -Example "Patti Fuller = Fuller, P."
```

```output
 Wagner, R.
 Brahms, J.
```

La première commande crée un tableau de nom et prénom.
Notez que les deuxième et quatrième éléments comportent un espace de fin supplémentaire, après le nom de famille.

La deuxième commande convertit toutes les chaînes qui correspondent à l’exemple de modèle : _mot, espace, mot et espace de fin final_ , tout ce qui précède le signe égal.
Notez également l’espace de début dans la sortie.

### Exemple 5 : mettre en forme les informations de processus avec plusieurs modèles

```powershell
$ExamplePatterns = @(
    @{before='"Hello","World"'; after='World: Hello'},
    @{before='"Hello","1"'; after='1: Hello'},
    @{before='"Hello-World","22"'; after='22: Hello-World'},
    @{before='"hello world","333"'; after='333: hello world'}
)
$Processes = Get-Process   | Select-Object -Property ProcessName, Id | ConvertTo-Csv -NoTypeInformation
$Processes | Convert-String -Example $ExamplePatterns
```

```output
Id: ProcessName
4368: AGSService
8896: Amazon Music Helper
4420: AppleMobileDeviceService
...
11140: git-bash
0: Idle
...
56: Secure System
...
13028: WmiPrvSE
2724: WUDFHost
2980: WUDFHost
3348: WUDFHost
```

**$ExamplePatterns** définit différents modèles attendus dans les données, par le biais d’exemples.

Le premier modèle, `@{before='"Hello","World"'; after='World: Hello'}` , lit comme suit : _attend des chaînes où un mot est placé entre guillemets doubles, puis une virgule,_ puis 
 _le deuxième et le dernier mot entre guillemets._ 
 _sans espace dans la chaîne. Sur la sortie : Placez le deuxième mot en premier,_ 
 _sans guillemets, puis un espace, puis le premier mot, sans guillemets._

Le deuxième modèle, `@{before='"Hello","1"'; after='1: Hello'}` , lit comme suit : _attend des chaînes où un mot est placé entre guillemets doubles, puis une virgule_ 
 _et un nombre entre guillemets._ 
 _sans espace dans la chaîne. Sur la sortie : Placez le nombre en premier,_ 
 _sans guillemets, puis un espace, puis le mot, sans guillemets._

Le troisième modèle, `@{before='"Hello-World","22"'; after='22: Hello-World'}` , lit comme suit : _attend des chaînes où deux mots avec un trait d’Union entre parenthèses sont placés_ entre guillemets 
 _doubles, puis une virgule et un nombre entre guillemets._ 
 sans _espace entre la virgule et le troisième guillemet double._ 
 _Sur la sortie : Placez le nombre en premier, sans guillemets, puis un espace,_ 
 puis _les mots avec trait d’Union, sans guillemets._

Le quatrième et dernier modèle, `@{before='"hello world","333"'; after='333: hello world'}` , lit comme suit : attend des _chaînes où deux mots avec un espace entre parenthèses sont placés entre_ guillemets 
 _doubles, puis une virgule et un nombre entre guillemets._ 
 sans _espace entre la virgule et le troisième guillemet double._ 
 _Sur la sortie : Placez le nombre en premier, sans guillemets, puis un espace,_ 
 puis _les mots avec l’espace entre, sans guillemets._

La première commande récupère tous les processus à l’aide de l’applet de commande Get-Process.
La commande les transmet à l’applet de commande Select-Object, qui sélectionne le nom de processus et l’ID de processus. À la fin du pipeline, la commande convertit la sortie en valeurs séparées par des virgules, sans informations de type, à l’aide de l’applet de commande ConvertTo-Csv.
La commande stocke les résultats dans la variable **$Processes** .
**$Processes** contient maintenant des noms de processus et un PID.

La deuxième commande spécifie un exemple de variable qui modifie l’ordre des éléments d’entrée.
La commande covertit chaque chaîne dans **$Processes** .

>**Remarque** Le quatrième modèle dit implicitement que deux mots ou plus séparés par des espaces sont mis en correspondance.
>
>Sans le quatrième modèle, seul le premier mot de la chaîne placée entre guillemets doubles est mis en correspondance.

## PARAMETERS

### -Exemple

Spécifie une liste d’exemples du format cible.
Spécifiez des paires séparées par le signe égal (=), avec le modèle source sur la gauche et le modèle cible à droite, comme dans les exemples suivants :

* `-Example "Hello World=World, Hello"`
* `-Example "Hello World=World: Hello",'"Hello","1"=1: Hello'`

>**Remarque** Le deuxième exemple utilise une liste de modèles

Vous pouvez également spécifier une liste de tables de hachage qui contiennent les propriétés **Before** et **after** .

* `-Example @{before='"Hello","World"'; after='World: Hello'}, @{before='"Hello","1"'; after='1: Hello'}`

>**Attention** Évitez d’utiliser des espaces autour du signe égal, car ils sont traités comme faisant partie du modèle.

```yaml
Type: System.Collections.Generic.List`1[System.Management.Automation.PSObject]
Parameter Sets: (All)
Aliases: E

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie une chaîne à mettre en forme.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### String

Vous pouvez diriger les chaînes vers cette applet de commande.

## SORTIES

### String

Cette applet de commande retourne une chaîne.

## REMARQUES

## LIENS CONNEXES

[ConvertFrom-String](ConvertFrom-String.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)

[Out-String](Out-String.md)

[Select-Object](Select-Object.md)
