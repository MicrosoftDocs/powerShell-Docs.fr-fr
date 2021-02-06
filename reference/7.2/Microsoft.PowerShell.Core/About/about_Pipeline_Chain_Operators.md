---
description: Décrit le chaînage des pipelines avec `&&` les `||` opérateurs et dans PowerShell.
Locale: en-US
ms.date: 09/30/2019
schema: 2.0.0
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: ece84ec061126401e53bf58112cd79a07a816e8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598803"
---
# <a name="about-pipeline-chain-operators"></a>À propos des opérateurs de chaîne de pipeline

## <a name="short-description"></a>Description courte

Décrit le chaînage des pipelines avec `&&` les `||` opérateurs et dans PowerShell.

## <a name="long-description"></a>Description longue

À compter de PowerShell 7, PowerShell implémente `&&` les `||` opérateurs et pour chaîner de manière conditionnelle des pipelines. Ces opérateurs sont connus dans PowerShell en tant qu' *opérateurs de chaîne de pipeline* et sont similaires à des [listes et ou](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) dans des interpréteurs de commandes POSIX tels que bash, zsh et SH, ainsi qu’à des [symboles de traitement conditionnel](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) dans l’interface de commande Windows (cmd.exe).

L’opérateur `&&` exécute le pipeline droit si l’exécution du pipeline gauche a réussi. Inversement, l’opérateur `||` exécute le pipeline droit si l’exécution du pipeline gauche a échoué.

Ces opérateurs utilisent les variables `$?` et `$LASTEXITCODE` pour déterminer si un pipeline a échoué. Cela vous permet de les utiliser avec des commandes natives, et pas seulement avec des cmdlet ou des fonctions. Par exemple :

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a>Exemples

#### <a name="two-successful-commands"></a>Deux commandes réussies

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a>La première commande échoue, provoquant la non-exécution de la seconde

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a>La première commande réussit, donc la deuxième commande n’est pas exécutée

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a>La première commande échoue, donc la deuxième commande est exécutée

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

La réussite du pipeline est définie par la valeur de la `$?` variable, que PowerShell définit automatiquement après l’exécution d’un pipeline en fonction de son état d’exécution.
Cela signifie que les opérateurs de chaîne de pipeline ont l’équivalence suivante :

```powershell
Test-Command '1' && Test-Command '2'
```

fonctionne de la même façon que

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

and

```powershell
Test-Command '1' || Test-Command '2'
```

fonctionne de la même façon que

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a>Assignation à partir de chaînes de pipeline

L’affectation d’une variable à partir d’une chaîne de pipeline prend la concaténation de tous les pipelines de la chaîne :

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

Si une erreur de fin de script se produit pendant l’assignation à partir d’une chaîne de pipeline, l’affectation échoue :

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a>Syntaxe et priorité des opérateurs

Contrairement à d’autres opérateurs, `&&` et `||` fonctionnent sur des pipelines, plutôt que sur des expressions telles que `+` ou `-and` , par exemple.

`&&` et `||` ont une priorité plus faible que le canalisation ( `|` ) ou la redirection ( `>` ), mais une priorité plus élevée que les opérateurs de travail ( `&` ), l’assignation ( `=` ) ou les points-virgules ( `;` ). Cela signifie que les pipelines d’une chaîne de pipeline peuvent être redirigés individuellement, et que toutes les chaînes de pipeline peuvent être en arrière-plan, affectées à des variables ou être séparées en tant qu’instructions.

Pour utiliser une syntaxe de précédence inférieure dans une chaîne de pipeline, envisagez l’utilisation de parenthèses `(...)` .
De même, pour incorporer une instruction dans une chaîne de pipeline, une sous-expression `$(...)` peut être utilisée.
Cela peut être utile pour combiner des commandes natives avec un workflow de contrôle :

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

Depuis PowerShell 7, le comportement de ces syntaxes a été modifié afin de `$?` définir comme prévu quand une commande réussit ou échoue entre parenthèses ou sous-expression.

Comme la plupart des autres opérateurs dans PowerShell, `&&` et `||` sont également *associatifs à gauche*, ce qui signifie qu’ils sont regroupés à partir de la gauche. Par exemple :

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

regroupera en tant que :

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

équivalent à :

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a>Interaction d’erreur

Les opérateurs de chaîne de pipeline n’absorbent pas les erreurs. Lorsqu’une instruction dans une chaîne de pipeline lève une erreur de fin de script, la chaîne de pipeline est arrêtée.

Par exemple :

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

Même lorsque l’erreur est interceptée, la chaîne de pipeline est toujours terminée :

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

Si une erreur ne se termine pas ou ne termine qu’un pipeline, la chaîne de pipeline continue, en respectant la valeur de `$?` :

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a>Chaînage des pipelines plutôt que des commandes

Les opérateurs de chaîne de pipeline, par leur nom, peuvent être utilisés pour chaîner des pipelines, plutôt que simplement des commandes. Cela correspond au comportement d’autres shells, mais peut rendre la *réussite* plus difficile à déterminer :

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

Notez que n' `Write-Output 'All done!'` est pas exécuté, car `Test-NotTwo` est considéré comme ayant échoué après la génération de l’erreur sans fin d’exécution.

## <a name="see-also"></a>Voir aussi

- [about_Operators](about_Operators.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_pipelines](about_pipelines.md)

