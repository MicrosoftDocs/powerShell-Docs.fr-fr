---
description: Décrit une commande de langage que vous pouvez utiliser pour parcourir tous les éléments d’une collection d’éléments.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach
ms.openlocfilehash: 42cea9f61330e16adcad0ad543acca21e35d5ca8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208197"
---
# <a name="about-foreach"></a><span data-ttu-id="95ef9-104">À propos de ForEach</span><span class="sxs-lookup"><span data-stu-id="95ef9-104">About ForEach</span></span>

## <a name="short-description"></a><span data-ttu-id="95ef9-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="95ef9-105">Short description</span></span>
<span data-ttu-id="95ef9-106">Décrit une commande de langage que vous pouvez utiliser pour parcourir tous les éléments d’une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="95ef9-106">Describes a language command you can use to traverse all the items in a collection of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="95ef9-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="95ef9-107">Long description</span></span>

<span data-ttu-id="95ef9-108">L' `Foreach` instruction (également appelée `Foreach` boucle) est une construction de langage permettant d’effectuer un pas à pas (itération) d’une série de valeurs dans une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="95ef9-108">The `Foreach` statement (also known as a `Foreach` loop) is a language construct for stepping through (iterating) a series of values in a collection of items.</span></span>

<span data-ttu-id="95ef9-109">Le type de collection le plus simple et le plus courant à parcourir est un tableau.</span><span class="sxs-lookup"><span data-stu-id="95ef9-109">The simplest and most typical type of collection to traverse is an array.</span></span>
<span data-ttu-id="95ef9-110">Dans une `Foreach` boucle, il est courant d’exécuter une ou plusieurs commandes sur chaque élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="95ef9-110">Within a `Foreach` loop, it is common to run one or more commands against each item in an array.</span></span>

## <a name="syntax"></a><span data-ttu-id="95ef9-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95ef9-111">Syntax</span></span>

<span data-ttu-id="95ef9-112">L’exemple suivant illustre la `ForEach` syntaxe :</span><span class="sxs-lookup"><span data-stu-id="95ef9-112">The following shows the `ForEach` syntax:</span></span>

```
foreach ($<item> in $<collection>){<statement list>}
```

<span data-ttu-id="95ef9-113">La partie de l' `ForEach` instruction entre parenthèses représente une variable et une collection à itérer.</span><span class="sxs-lookup"><span data-stu-id="95ef9-113">The part of the `ForEach` statement enclosed in parenthesis represents a variable and a collection to iterate.</span></span> <span data-ttu-id="95ef9-114">PowerShell crée automatiquement la variable `$<item>` lors de l’exécution de la `Foreach` boucle.</span><span class="sxs-lookup"><span data-stu-id="95ef9-114">PowerShell creates the variable `$<item>` automatically when the `Foreach` loop runs.</span></span> <span data-ttu-id="95ef9-115">Avant chaque itération de la boucle, la variable est définie sur une valeur dans la collection.</span><span class="sxs-lookup"><span data-stu-id="95ef9-115">Prior to each iteration through the loop, the variable is set to a value in the collection.</span></span>
<span data-ttu-id="95ef9-116">Le bloc suivant une `Foreach` instruction `{<statement list>}` contient un ensemble de commandes à exécuter sur chaque élément d’une collection.</span><span class="sxs-lookup"><span data-stu-id="95ef9-116">The block following a `Foreach` statement `{<statement list>}` contains a set of commands to execute against each item in a collection.</span></span>

### <a name="examples"></a><span data-ttu-id="95ef9-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="95ef9-117">Examples</span></span>

<span data-ttu-id="95ef9-118">Par exemple, la `Foreach` boucle de l’exemple suivant affiche les valeurs dans le `$letterArray` tableau.</span><span class="sxs-lookup"><span data-stu-id="95ef9-118">For example, the `Foreach` loop in the following example displays the values in the `$letterArray` array.</span></span>

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

<span data-ttu-id="95ef9-119">Dans cet exemple, le `$letterArray` tableau est créé et initialisé avec les valeurs de chaîne `"a"` , `"b"` , `"c"` et `"d"` .</span><span class="sxs-lookup"><span data-stu-id="95ef9-119">In this example, the `$letterArray` array is created and initialized with the string values `"a"`, `"b"`, `"c"`, and `"d"`.</span></span> <span data-ttu-id="95ef9-120">La première fois que l' `Foreach` instruction est exécutée, elle définit la `$letter` variable comme étant égale au premier élément de `$letterArray` ( `"a"` ).</span><span class="sxs-lookup"><span data-stu-id="95ef9-120">The first time the `Foreach` statement runs, it sets the `$letter` variable equal to the first item in `$letterArray` (`"a"`).</span></span> <span data-ttu-id="95ef9-121">Elle utilise ensuite l' `Write-Host` applet de commande pour afficher la lettre a.</span><span class="sxs-lookup"><span data-stu-id="95ef9-121">Then, it uses the `Write-Host` cmdlet to display the letter a.</span></span> <span data-ttu-id="95ef9-122">La prochaine fois que la boucle `$letter` est définie, a la valeur `"b"` , et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="95ef9-122">The next time through the loop, `$letter` is set to `"b"`, and so on.</span></span> <span data-ttu-id="95ef9-123">Une fois que la `Foreach` boucle affiche la lettre d, PowerShell quitte la boucle.</span><span class="sxs-lookup"><span data-stu-id="95ef9-123">After the `Foreach` loop displays the letter d, PowerShell exits the loop.</span></span>

<span data-ttu-id="95ef9-124">La totalité de l' `Foreach` instruction doit apparaître sur une seule ligne pour pouvoir être exécutée en tant que commande à partir de l’invite de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95ef9-124">The entire `Foreach` statement must appear on a single line to run it as a command at the PowerShell command prompt.</span></span> <span data-ttu-id="95ef9-125">Il `Foreach` n’est pas nécessaire que l’instruction entière apparaisse sur une seule ligne si vous placez la commande dans un fichier de script. ps1 à la place.</span><span class="sxs-lookup"><span data-stu-id="95ef9-125">The entire `Foreach` statement does not have to appear on a single line if you place the command in a .ps1 script file instead.</span></span>

<span data-ttu-id="95ef9-126">`Foreach` les instructions peuvent également être utilisées avec les applets de commande qui retournent une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="95ef9-126">`Foreach` statements can also be used together with cmdlets that return a collection of items.</span></span> <span data-ttu-id="95ef9-127">Dans l’exemple suivant, l’instruction foreach effectue un pas à pas dans la liste des éléments retournés par l’applet de commande `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="95ef9-127">In the following example, the Foreach statement steps through the list of items that is returned by the `Get-ChildItem` cmdlet.</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

<span data-ttu-id="95ef9-128">Vous pouvez affiner l’exemple en utilisant une `If` instruction pour limiter les résultats retournés.</span><span class="sxs-lookup"><span data-stu-id="95ef9-128">You can refine the example by using an `If` statement to limit the results that are returned.</span></span> <span data-ttu-id="95ef9-129">Dans l’exemple suivant, l' `Foreach` instruction exécute la même opération de boucle que l’exemple précédent, mais elle ajoute une `If` instruction pour limiter les résultats aux fichiers dont la taille est supérieure à 100 kilo-octets (Ko) :</span><span class="sxs-lookup"><span data-stu-id="95ef9-129">In the following example, the `Foreach` statement performs the same looping operation as the previous example, but it adds an `If` statement to limit the results to files that are greater than 100 kilobytes (KB):</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

<span data-ttu-id="95ef9-130">Dans cet exemple, la `Foreach` boucle utilise une propriété de la `$file` variable pour effectuer une opération de comparaison ( `$file.length -gt 100KB` ).</span><span class="sxs-lookup"><span data-stu-id="95ef9-130">In this example, the `Foreach` loop uses a property of the `$file` variable to perform a comparison operation (`$file.length -gt 100KB`).</span></span> <span data-ttu-id="95ef9-131">La `$file` variable contient toutes les propriétés de l’objet qui est retourné par l' `Get-ChildItem` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="95ef9-131">The `$file` variable contains all the properties in the object that is returned by the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="95ef9-132">Par conséquent, vous pouvez retourner plus qu’un simple nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="95ef9-132">Therefore, you can return more than just a file name.</span></span>
<span data-ttu-id="95ef9-133">Dans l’exemple suivant, PowerShell retourne la longueur et le dernier temps d’accès à l’intérieur de la liste d’instructions :</span><span class="sxs-lookup"><span data-stu-id="95ef9-133">In the next example, PowerShell returns the length and the last access time inside the statement list:</span></span>

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

<span data-ttu-id="95ef9-134">Dans cet exemple, vous n’êtes pas limité à l’exécution d’une seule commande dans une liste d’instructions.</span><span class="sxs-lookup"><span data-stu-id="95ef9-134">In this example, you are not limited to running a single command in a statement list.</span></span>

<span data-ttu-id="95ef9-135">Vous pouvez également utiliser une variable en dehors d’une `Foreach` boucle et incrémenter la variable à l’intérieur de la boucle.</span><span class="sxs-lookup"><span data-stu-id="95ef9-135">You can also use a variable outside a `Foreach` loop and increment the variable inside the loop.</span></span> <span data-ttu-id="95ef9-136">L’exemple suivant compte les fichiers dont la taille est supérieure à 100 Ko :</span><span class="sxs-lookup"><span data-stu-id="95ef9-136">The following example counts files over 100 KB in size:</span></span>

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

<span data-ttu-id="95ef9-137">Dans l’exemple précédent, la `$i` variable est définie à l' `0` extérieur de la boucle, et la variable est incrémentée à l’intérieur de la boucle pour chaque fichier dont la taille est supérieure à 100 Ko.</span><span class="sxs-lookup"><span data-stu-id="95ef9-137">In the preceding example, the `$i` variable is set to `0` outside the loop, and the variable is incremented inside the loop for each file that is found that is larger than 100 KB.</span></span> <span data-ttu-id="95ef9-138">Lorsque la boucle se termine, une `If` instruction évalue la valeur de `$i` pour afficher le nombre de tous les fichiers de plus de 100 Ko.</span><span class="sxs-lookup"><span data-stu-id="95ef9-138">When the loop exits, an `If` statement evaluates the value of `$i` to display a count of all the files over 100 KB.</span></span> <span data-ttu-id="95ef9-139">Ou bien, il affiche un message indiquant qu’aucun fichier de plus de 100 Ko n’a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="95ef9-139">Or, it displays a message stating that no files over 100 KB were found.</span></span>

<span data-ttu-id="95ef9-140">L’exemple précédent montre également comment mettre en forme les résultats de la longueur de fichier :</span><span class="sxs-lookup"><span data-stu-id="95ef9-140">The previous example also demonstrates how to format the file length results:</span></span>

```powershell
($file.length / 1024).ToString("F0")
```

<span data-ttu-id="95ef9-141">La valeur est divisée par 1 024 pour afficher les résultats en kilo-octets plutôt qu’en octets, et la valeur résultante est ensuite mise en forme à l’aide du spécificateur de format à virgule fixe pour supprimer toutes les valeurs décimales du résultat.</span><span class="sxs-lookup"><span data-stu-id="95ef9-141">The value is divided by 1,024 to show the results in kilobytes rather than bytes, and the resulting value is then formatted using the fixed-point format specifier to remove any decimal values from the result.</span></span> <span data-ttu-id="95ef9-142">La valeur 0 fait que le spécificateur de format n’affiche pas de décimale.</span><span class="sxs-lookup"><span data-stu-id="95ef9-142">The 0 makes the format specifier show no decimal places.</span></span>

<span data-ttu-id="95ef9-143">Dans l’exemple suivant, la fonction définie analyse les scripts PowerShell et les modules de script et retourne l’emplacement des fonctions contenues dans.</span><span class="sxs-lookup"><span data-stu-id="95ef9-143">In the following example, the function defined parses PowerShell scripts and script modules and returns the location of functions contained within.</span></span> <span data-ttu-id="95ef9-144">L’exemple montre comment utiliser la `MoveNext` méthode (qui fonctionne de la même façon que `skip X` sur une `For` boucle) et la `Current` propriété de la `$foreach` variable à l’intérieur d’un bloc de script ForEach.</span><span class="sxs-lookup"><span data-stu-id="95ef9-144">The example demonstrates how to use the `MoveNext` method (which works similarly to `skip X` on a `For` loop) and the `Current` property of the `$foreach` variable inside of a foreach script block.</span></span> <span data-ttu-id="95ef9-145">L’exemple de fonction peut rechercher des fonctions dans un script, même s’il existe des définitions de fonctions qui sont espacées de façon inhabituelle ou incohérente qui s’étendent sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="95ef9-145">The example function can find functions in a script even if there are unusually- or inconsistently-spaced function definitions that span multiple lines.</span></span>

<span data-ttu-id="95ef9-146">Pour plus d’informations, consultez [utilisation d’énumérateurs](about_Automatic_Variables.md#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="95ef9-146">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators).</span></span>

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
        $_
      } else {
        $filesToProcess = Get-Item -Path $Path
      }
      $parser = [System.Management.Automation.Language.Parser]
      foreach ($item in $filesToProcess) {
        if ($item.PSIsContainer -or
            $item.Extension -notin @('.ps1', '.psm1')) {
          continue
        }
        $tokens = $errors = $null
        $ast = $parser::ParseFile($item.FullName, ([REF]$tokens),
          ([REF]$errors))
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

## <a name="see-also"></a><span data-ttu-id="95ef9-147">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="95ef9-147">SEE ALSO</span></span>

[<span data-ttu-id="95ef9-148">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="95ef9-148">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="95ef9-149">about_If</span><span class="sxs-lookup"><span data-stu-id="95ef9-149">about_If</span></span>](about_If.md)

[<span data-ttu-id="95ef9-150">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="95ef9-150">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
