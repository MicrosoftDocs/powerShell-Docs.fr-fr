---
description: Décrit comment utiliser la projection pour passer des paramètres à des commandes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: a64cbbe5edd40bf4fc7f9b7347421988d225e666
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207278"
---
# <a name="about-splatting"></a>À propos de la projection

## <a name="short-description"></a>Description courte

Décrit comment utiliser la projection pour passer des paramètres à des commandes dans PowerShell.

## <a name="long-description"></a>Description longue

La projection est une méthode de transmission d’une collection de valeurs de paramètre à une commande en tant qu’unité. PowerShell associe chaque valeur de la collection à un paramètre de commande. Les valeurs de paramètres réintégrés sont stockées dans des variables de projection nommées, qui ressemblent à des variables standard, mais commencent par un symbole arobase ( `@` ) au lieu d’un signe dollar ( `$` ). Le symbole at indique à PowerShell que vous passez une collection de valeurs, au lieu d’une seule valeur.

La projection rend vos commandes plus courtes et plus faciles à lire. Vous pouvez réutiliser les valeurs de réorganisation dans des appels de commande différents et utiliser la projection pour passer des valeurs de paramètre de la `$PSBoundParameters` variable automatique à d’autres scripts et fonctions.

À compter de Windows PowerShell 3,0, vous pouvez également utiliser la projection pour représenter tous les paramètres d’une commande.

## <a name="syntax"></a>Syntaxe

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

Pour fournir des valeurs de paramètre pour les paramètres positionnels, dans lesquelles les noms de paramètres ne sont pas requis, utilisez la syntaxe de tableau. Pour fournir des paires nom de paramètre/valeur, utilisez la syntaxe de table de hachage. La valeur de la projection peut apparaître n’importe où dans la liste de paramètres.

Lors de la projection, vous n’avez pas besoin d’utiliser une table de hachage ou un tableau pour passer tous les paramètres. Vous pouvez passer certains paramètres en utilisant la projection et en passer d’autres par position ou par nom de paramètre. En outre, vous pouvez se terminant par plusieurs objets dans une même commande afin de ne pas transmettre plus d’une valeur pour chaque paramètre.

À partir de PowerShell 7,1, vous pouvez substituer un paramètre de la manière explicite en définissant explicitement un paramètre dans une commande.

## <a name="splatting-with-hash-tables"></a>Projection avec des tables de hachage

Utilisez une table de hachage pour se terminant par les paires nom de paramètre/valeur. Vous pouvez utiliser ce format pour tous les types de paramètres, y compris les paramètres positionnels et de commutateur.
Les paramètres positionnels doivent être attribués par nom.

Les exemples suivants comparent deux `Copy-Item` commandes qui copient le fichier Test.txt dans le fichier Test2.txt dans le même répertoire.

Le premier exemple utilise le format traditionnel dans lequel les noms de paramètres sont inclus.

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

Le deuxième exemple utilise la projection de table de hachage. La première commande crée une table de hachage de paires paramètre-nom et paramètre-valeur et la stocke dans la `$HashArguments` variable. La deuxième commande utilise la `$HashArguments` variable dans une commande avec projection. Le symbole arobase ( `@HashArguments` ) remplace le signe dollar ( `$HashArguments` ) dans la commande.

Pour fournir une valeur pour le paramètre de commutateur **WhatIf** , utilisez `$True` ou `$False` .

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> Dans la première commande, le symbole arobase ( `@` ) indique une table de hachage, et non une valeur à la fois. La syntaxe des tables de hachage dans PowerShell est la suivante : `@{<name>=<value>; <name>=<value>; ...}`

## <a name="splatting-with-arrays"></a>Projection avec des tableaux

Utilisez un tableau pour se terminant par des valeurs pour les paramètres positionnels, qui ne nécessitent pas de noms de paramètres. Les valeurs doivent être dans l’ordre de numéro de position dans le tableau.

Les exemples suivants comparent deux `Copy-Item` commandes qui copient le fichier Test.txt dans le fichier Test2.txt dans le même répertoire.

Le premier exemple utilise le format traditionnel dans lequel les noms de paramètres sont omis. Les valeurs des paramètres apparaissent dans l’ordre de position dans la commande.

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

Le deuxième exemple utilise la projection de tableau. La première commande crée un tableau des valeurs de paramètre et les stocke dans la `$ArrayArguments` variable. Les valeurs sont dans l’ordre de position dans le tableau. La deuxième commande utilise la `$ArrayArguments` variable dans une commande en cours de projection. Le symbole arobase ( `@ArrayArguments` ) remplace le signe dollar ( `$ArrayArguments` ) dans la commande.

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a>Utilisation du paramètre ArgumentList

Plusieurs applets de commande ont un paramètre **argumentlist** qui est utilisé pour passer des valeurs de paramètre à un bloc de script qui est exécuté par l’applet de commande. Le paramètre **argumentlist** prend un tableau de valeurs qui est passé au bloc de script. PowerShell utilise en fait la projection de tableau pour lier les valeurs aux paramètres du bloc de script. Lorsque vous utilisez **argumentlist** , si vous devez passer un tableau en tant qu’objet unique lié à un seul paramètre, vous devez encapsuler le tableau comme seul élément d’un autre tableau.

L’exemple suivant a un bloc de script qui accepte un paramètre unique qui est un tableau de chaînes.

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```
<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
Dans cet exemple, seul le premier élément de `$array` est passé au bloc de script.

```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
} -ArgumentList (,$array)
```

Dans cet exemple, `$array` est encapsulé dans un tableau afin que le tableau entier soit passé au bloc de script sous la forme d’un objet unique.

```Output
Hello World!
```

## <a name="examples"></a>Exemples

### <a name="example-1-reuse-splatted-parameters-in-different-commands"></a>Exemple 1 : réutiliser des paramètres réintégrés dans des commandes différentes

Cet exemple montre comment réutiliser des valeurs réintégrées dans des commandes différentes. Dans cet exemple, les commandes utilisent l' `Write-Host` applet de commande pour écrire des messages dans la console du programme hôte. Elle utilise la projection pour spécifier les couleurs de premier plan et d’arrière-plan.

Pour modifier les couleurs de toutes les commandes, il vous suffit de modifier la valeur de la `$Colors` variable.

La première commande crée une table de hachage de noms et de valeurs de paramètres et stocke la table de hachage dans la `$Colors` variable.

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

Les deuxième et troisième commandes utilisent la `$Colors` variable pour la projection dans une `Write-Host` commande. Pour utiliser le `$Colors variable` , remplacez le signe dollar ( `$Colors` ) par un symbole arobase ( `@Colors` ).

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

### <a name="example-2-forward-parameters-using-psboundparameters"></a>Exemple 2 : transférer des paramètres à l’aide de $PSBoundParameters

Cet exemple montre comment transférer leurs paramètres à d’autres commandes à l’aide de la variable de projection et de la `$PSBoundParameters` variable automatique.

La `$PSBoundParameters` variable automatique est un objet dictionnaire (System. Collections. Generic. Dictionary) qui contient tous les noms et valeurs de paramètres utilisés lors de l’exécution d’un script ou d’une fonction.

Dans l’exemple suivant, nous utilisons la `$PSBoundParameters` variable pour transférer les valeurs de paramètres passées à un script ou à une fonction de `Test2` la fonction à la `Test1` fonction. Les deux appels à la `Test1` fonction à partir de `Test2` utilisent la projection.

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

### <a name="example-3-override-splatted-parameters-with-explicitly-defined-parameters"></a>Exemple 3 : remplacement de paramètres à l’aide de paramètres définis de manière explicite

Cet exemple montre comment substituer un paramètre de projection à l’aide de paramètres définis de manière explicite. Cela est utile lorsque vous ne souhaitez pas créer de nouvelle Hashtable ou modifier une valeur dans la Hashtable que vous utilisez pour se terminant par.

La `$commonParams` variable stocke les paramètres pour créer des ordinateurs virtuels à l' `East US` emplacement. La `$allVms` variable est une liste de machines virtuelles à créer. Nous parcourons la liste et utilisons `$commonParams` pour se terminant par les paramètres afin de créer chaque machine virtuelle. Toutefois, nous voulons `myVM2` créer dans une région différente de celle des autres machines virtuelles. Au lieu d’ajuster la `$commonParams` Hashtable, vous pouvez définir explicitement le paramètre **location** dans `New-AzVm` pour remplacer la valeur de la `Location` clé dans `$commonParams` .

```powershell
$commonParams = @{
    ResourceGroupName = "myResourceGroup"
    Location = "East US"
    VirtualNetworkName = "myVnet"
    SubnetName = "mySubnet"
    SecurityGroupName = "myNetworkSecurityGroup"
    PublicIpAddressName = "myPublicIpAddress"
}

$allVms = @('myVM1','myVM2','myVM3',)

foreach ($vm in $allVms)
{
    if ($vm -eq 'myVM2')
    {
        New-AzVm @commonParams -Name $vm -Location "West US"
    }
    else
    {
        New-AzVm @commonParams -Name $vm
    }
}
```

## <a name="splatting-command-parameters"></a>Paramètres de commande de projection

Vous pouvez utiliser la projection pour représenter les paramètres d’une commande. Cette technique est utile lorsque vous créez une fonction proxy, c’est-à-dire une fonction qui appelle une autre commande. Cette fonctionnalité est introduite dans Windows PowerShell 3,0.

Pour se terminant par les paramètres d’une commande, utilisez `@Args` pour représenter les paramètres de commande. Cette technique est plus facile que l’énumération des paramètres de commande et elle fonctionne sans révision même si les paramètres de la commande appelée changent.

La fonctionnalité utilise la `$Args` variable automatique, qui contient toutes les valeurs de paramètre non assignées.

Par exemple, la fonction suivante appelle l' `Get-Process` applet de commande. Dans cette fonction, `@Args` représente tous les paramètres de l' `Get-Process` applet de commande.

```powershell
function Get-MyProcess { Get-Process @Args }
```

Lorsque vous utilisez la `Get-MyProcess` fonction, tous les paramètres et valeurs de paramètre non assignés sont passés à `@Args` , comme indiqué dans les commandes suivantes.

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

Vous pouvez utiliser `@Args` dans une fonction qui a des paramètres déclarés explicitement. Vous pouvez l’utiliser plusieurs fois dans une fonction, mais tous les paramètres que vous entrez sont passés à toutes les instances de `@Args` , comme illustré dans l’exemple suivant.

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a>Notes

Si vous faites une fonction dans une fonction avancée à l’aide des attributs **CmdletBinding** ou **Parameter** , la `$args` variable automatique n’est plus disponible dans la fonction. Les fonctions avancées nécessitent une définition de paramètre explicite.

La configuration d’état souhaité (DSC) PowerShell n’a pas été conçue pour utiliser la projection.
Vous ne pouvez pas utiliser la projection pour passer des valeurs dans une ressource DSC. Pour plus d’informations, consultez l’article intitulé « [Pseudo-relatting DSC](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)» de gael Colas.

## <a name="see-also"></a>Voir aussi

[about_Arrays](about_Arrays.md)

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Parameters](about_Parameters.md)
