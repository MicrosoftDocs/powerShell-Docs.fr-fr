---
description: Décrit une commande de langage que vous pouvez utiliser pour parcourir tous les éléments d’une collection d’éléments.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach
ms.openlocfilehash: f1f00df8b0f07dd945994860897584d883ef2ce4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207670"
---
# <a name="about-foreach"></a>À propos de ForEach

## <a name="short-description"></a>Description courte
Décrit une commande de langage que vous pouvez utiliser pour parcourir tous les éléments d’une collection d’éléments.

## <a name="long-description"></a>Description longue

L' `Foreach` instruction (également appelée `Foreach` boucle) est une construction de langage permettant d’effectuer un pas à pas (itération) d’une série de valeurs dans une collection d’éléments.

Le type de collection le plus simple et le plus courant à parcourir est un tableau.
Dans une `Foreach` boucle, il est courant d’exécuter une ou plusieurs commandes sur chaque élément d’un tableau.

## <a name="syntax"></a>Syntaxe

L’exemple suivant illustre la `ForEach` syntaxe :

```
foreach ($<item> in $<collection>){<statement list>}
```

La partie de l' `ForEach` instruction entre parenthèses représente une variable et une collection à itérer. PowerShell crée automatiquement la variable `$<item>` lors de l’exécution de la `Foreach` boucle. Avant chaque itération de la boucle, la variable est définie sur une valeur dans la collection.
Le bloc suivant une `Foreach` instruction `{<statement list>}` contient un ensemble de commandes à exécuter sur chaque élément d’une collection.

### <a name="examples"></a>Exemples

Par exemple, la `Foreach` boucle de l’exemple suivant affiche les valeurs dans le `$letterArray` tableau.

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

Dans cet exemple, le `$letterArray` tableau est créé et initialisé avec les valeurs de chaîne `"a"` , `"b"` , `"c"` et `"d"` . La première fois que l' `Foreach` instruction est exécutée, elle définit la `$letter` variable comme étant égale au premier élément de `$letterArray` ( `"a"` ). Elle utilise ensuite l' `Write-Host` applet de commande pour afficher la lettre a. La prochaine fois que la boucle `$letter` est définie, a la valeur `"b"` , et ainsi de suite. Une fois que la `Foreach` boucle affiche la lettre d, PowerShell quitte la boucle.

La totalité de l' `Foreach` instruction doit apparaître sur une seule ligne pour pouvoir être exécutée en tant que commande à partir de l’invite de commandes PowerShell. Il `Foreach` n’est pas nécessaire que l’instruction entière apparaisse sur une seule ligne si vous placez la commande dans un fichier de script. ps1 à la place.

`Foreach` les instructions peuvent également être utilisées avec les applets de commande qui retournent une collection d’éléments. Dans l’exemple suivant, l’instruction foreach effectue un pas à pas dans la liste des éléments retournés par l’applet de commande `Get-ChildItem` .

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

Vous pouvez affiner l’exemple en utilisant une `If` instruction pour limiter les résultats retournés. Dans l’exemple suivant, l' `Foreach` instruction exécute la même opération de boucle que l’exemple précédent, mais elle ajoute une `If` instruction pour limiter les résultats aux fichiers dont la taille est supérieure à 100 kilo-octets (Ko) :

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

Dans cet exemple, la `Foreach` boucle utilise une propriété de la `$file` variable pour effectuer une opération de comparaison ( `$file.length -gt 100KB` ). La `$file` variable contient toutes les propriétés de l’objet qui est retourné par l' `Get-ChildItem` applet de commande. Par conséquent, vous pouvez retourner plus qu’un simple nom de fichier.
Dans l’exemple suivant, PowerShell retourne la longueur et le dernier temps d’accès à l’intérieur de la liste d’instructions :

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
    Write-Host $file.length
    Write-Host $file.lastaccesstime
  }
}
```

Dans cet exemple, vous n’êtes pas limité à l’exécution d’une seule commande dans une liste d’instructions.

Vous pouvez également utiliser une variable en dehors d’une `Foreach` boucle et incrémenter la variable à l’intérieur de la boucle. L’exemple suivant compte les fichiers dont la taille est supérieure à 100 Ko :

```powershell
$i = 0
foreach ($file in Get-ChildItem) {
  if ($file.length -gt 100KB) {
    Write-Host $file "file size:" ($file.length / 1024).ToString("F0") KB
    $i = $i + 1
  }
}

if ($i -ne 0) {
  Write-Host
  Write-Host $i " file(s) over 100 KB in the current directory."
}
else {
  Write-Host "No files greater than 100 KB in the current directory."
}
```

Dans l’exemple précédent, la `$i` variable est définie à l' `0` extérieur de la boucle, et la variable est incrémentée à l’intérieur de la boucle pour chaque fichier dont la taille est supérieure à 100 Ko. Lorsque la boucle se termine, une `If` instruction évalue la valeur de `$i` pour afficher le nombre de tous les fichiers de plus de 100 Ko. Ou bien, il affiche un message indiquant qu’aucun fichier de plus de 100 Ko n’a été trouvé.

L’exemple précédent montre également comment mettre en forme les résultats de la longueur de fichier :

```powershell
($file.length / 1024).ToString("F0")
```

La valeur est divisée par 1 024 pour afficher les résultats en kilo-octets plutôt qu’en octets, et la valeur résultante est ensuite mise en forme à l’aide du spécificateur de format à virgule fixe pour supprimer toutes les valeurs décimales du résultat. La valeur 0 fait que le spécificateur de format n’affiche pas de décimale.

Dans l’exemple suivant, la fonction définie analyse les scripts PowerShell et les modules de script et retourne l’emplacement des fonctions contenues dans. L’exemple montre comment utiliser la `MoveNext` méthode (qui fonctionne de la même façon que `skip X` sur une `For` boucle) et la `Current` propriété de la `$foreach` variable à l’intérieur d’un bloc de script ForEach. L’exemple de fonction peut rechercher des fonctions dans un script, même s’il existe des définitions de fonctions qui sont espacées de façon inhabituelle ou incohérente qui s’étendent sur plusieurs lignes.

Pour plus d’informations, consultez [utilisation d’énumérateurs](about_Automatic_Variables.md#using-enumerators).

```powershell
function Get-FunctionPosition {
  [CmdletBinding()]
  [OutputType('FunctionPosition')]
  param(
    [Parameter(Position = 0, Mandatory,
      ValueFromPipeline, ValueFromPipelineByPropertyName)]
    [ValidateNotNullOrEmpty()]
    [Alias('PSPath')]
    [System.String[]]
    $Path
  )

  process {
    try {
      $filesToProcess = if ($_ -is [System.IO.FileSystemInfo]) {
        Write-Verbose "From pipeline"
        $_
      } else {
        Write-Verbose "From parameter, $Path"
        Get-Item -Path $Path
      }
      $parser = [System.Management.Automation.Language.Parser]
      Write-Verbose "lets start the foreach loop on `$filesToProcess with $($filesToProcess.count) as count"
      foreach ($item in $filesToProcess) {
        Write-Verbose "$item"
        if ($item.PSIsContainer -or
            $item.Extension -notin @('.ps1', '.psm1')) {
          continue
        }
        $tokens = $errors = $null
        $parser::ParseFile($item.FullName, ([REF]$tokens),
          ([REF]$errors)) | Out-Null
        if ($errors) {
          $msg = "File '{0}' has {1} parser errors." -f $item.FullName,
            $errors.Count
          Write-Warning $msg
        }
        :tokenLoop foreach ($token in $tokens) {
          if ($token.Kind -ne 'Function') {
            continue
          }
          $position = $token.Extent.StartLineNumber
          do {
            if (-not $foreach.MoveNext()) {
              break tokenLoop
            }
            $token = $foreach.Current
          } until ($token.Kind -in @('Generic', 'Identifier'))
          $functionPosition = [pscustomobject]@{
            Name       = $token.Text
            LineNumber = $position
            Path       = $item.FullName
          }
          Add-Member -InputObject $functionPosition `
            -TypeName FunctionPosition -PassThru
        }
      }
    }
    catch {
      throw
    }
  }
}
```

## <a name="see-also"></a>VOIR AUSSI

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_If](about_If.md)

[ForEach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)
