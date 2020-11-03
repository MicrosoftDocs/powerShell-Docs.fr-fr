---
description: Décrit comment définir et utiliser des jeux de paramètres dans les fonctions avancées.
title: about_Parameter_Sets
ms.date: 02/11/2020
ms.openlocfilehash: e6f7d006551bdeee11b68951f96f3fa2251e73e3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208274"
---
# <a name="about-parameter-sets"></a>À propos des jeux de paramètres

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit comment définir et utiliser des jeux de paramètres dans les fonctions avancées.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

PowerShell utilise des jeux de paramètres pour vous permettre d’écrire une fonction unique qui peut effectuer différentes actions pour différents scénarios. Les jeux de paramètres vous permettent d’exposer des paramètres différents à l’utilisateur. Et pour retourner des informations différentes en fonction des paramètres spécifiés par l’utilisateur.

## <a name="parameter-set-requirements"></a>Spécifications du jeu de paramètres

Les exigences suivantes s’appliquent à tous les jeux de paramètres.

- Chaque jeu de paramètres doit avoir au moins un paramètre unique. Si possible, définissez ce paramètre sur un paramètre obligatoire.

- Un jeu de paramètres qui contient plusieurs paramètres positionnels doit définir des positions uniques pour chaque paramètre. Deux paramètres positionnels ne peuvent pas spécifier la même position.

- Un seul paramètre d’un ensemble peut déclarer le `ValueFromPipeline` mot clé avec la valeur `true` . Plusieurs paramètres peuvent définir le `ValueFromPipelineByPropertyName` mot clé avec la valeur `true` .

- Si aucun jeu de paramètres n’est spécifié pour un paramètre, le paramètre appartient à tous les jeux de paramètres.

> [!NOTE]
> Il existe une limite de 32 jeux de paramètres.

## <a name="default-parameter-sets"></a>Jeux de paramètres par défaut

Lorsque plusieurs jeux de paramètres sont définis, le `DefaultParameterSetName` mot clé de l’attribut **CmdletBinding** spécifie le jeu de paramètres par défaut.
PowerShell utilise le jeu de paramètres par défaut lorsqu’il ne peut pas déterminer le jeu de paramètres à utiliser en fonction des informations fournies à la commande. Pour plus d’informations sur l’attribut **CmdletBinding** , consultez [about_Functions_CmdletBindingAttribute](about_functions_cmdletbindingattribute.md).

## <a name="declaring-parameter-sets"></a>Déclarer des jeux de paramètres

Pour créer un jeu de paramètres, vous devez spécifier le `ParameterSetName` mot clé de l’attribut de **paramètre** pour chaque paramètre dans le jeu de paramètres. Pour les paramètres appartenant à plusieurs jeux de paramètres, ajoutez un attribut de **paramètre** pour chaque jeu de paramètres.

L’attribut **Parameter** vous permet de définir le paramètre différemment pour chaque jeu de paramètres. Par exemple, vous pouvez définir un paramètre comme obligatoire dans un jeu et facultatif dans un autre. Toutefois, chaque jeu de paramètres doit contenir au moins un paramètre unique.

Les paramètres qui n’ont pas de nom de jeu de paramètres attribué appartiennent à tous les jeux de paramètres.

### <a name="example"></a>Exemple

L’exemple de fonction suivant compte le nombre de lignes, de caractères et de mots dans un fichier texte. À l’aide de paramètres, vous pouvez spécifier les valeurs à renvoyer et les fichiers que vous souhaitez mesurer. Quatre jeux de paramètres sont définis :

- Chemin d’accès
- PathAll
- LiteralPath
- LiteralPathAll

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

Chaque jeu de paramètres doit avoir un paramètre unique ou une combinaison unique de paramètres. Les `Path` `PathAll` jeux de paramètres et sont très similaires, mais le paramètre **All** est unique pour le `PathAll` jeu de paramètres. Il en va de même pour `LiteralPath` les `LiteralPathAll` jeux de paramètres et. Bien que les paramètres `PathAll` et `LiteralPathAll` soient définis tous les deux avec le paramètre **All** , les paramètres **path** et **LiteralPath** les différencient.

Utilisez `Get-Command -Syntax` affiche la syntaxe de chaque jeu de paramètres. Toutefois, il n’affiche pas le nom du jeu de paramètres. L’exemple suivant montre les paramètres qui peuvent être utilisés dans chaque jeu de paramètres.

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a>Jeux de paramètres en action

Dans cet exemple, nous utilisons le `PathAll` jeu de paramètres.

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```

