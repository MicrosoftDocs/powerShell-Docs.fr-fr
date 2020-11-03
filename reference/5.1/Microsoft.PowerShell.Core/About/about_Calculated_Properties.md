---
description: PowerShell offre la possibilité d’ajouter dynamiquement de nouvelles propriétés et de modifier la mise en forme de la sortie des objets dans le pipeline.
Locale: en-US
ms.date: 10/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 4dd7912c7e1a976e20f92093a47355f3a3291093
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207789"
---
# <a name="about-calculated-properties"></a><span data-ttu-id="e7208-103">À propos des propriétés calculées</span><span class="sxs-lookup"><span data-stu-id="e7208-103">About calculated properties</span></span>

## <a name="short-description"></a><span data-ttu-id="e7208-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="e7208-104">Short Description</span></span>

<span data-ttu-id="e7208-105">PowerShell offre la possibilité d’ajouter dynamiquement de nouvelles propriétés et de modifier la mise en forme de la sortie des objets dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="e7208-105">PowerShell provides the ability to dynamically add new properties and alter the formatting of objects output to the pipeline.</span></span>

## <a name="long-description"></a><span data-ttu-id="e7208-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="e7208-106">Long Description</span></span>

<span data-ttu-id="e7208-107">Un certain nombre d’applets de commande PowerShell transforment, agrègent ou traitent des objets d’entrée en objets de sortie à l’aide de paramètres qui permettent d’ajouter de nouvelles propriétés à ces objets de sortie.</span><span class="sxs-lookup"><span data-stu-id="e7208-107">A number of PowerShell cmdlets transform, aggregate, or process input objects into output objects using parameters that allow the addition of new properties to those output objects.</span></span> <span data-ttu-id="e7208-108">Ces paramètres peuvent être utilisés pour générer de nouvelles propriétés calculées sur les objets de sortie en fonction des valeurs des objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e7208-108">These parameters can be used to generate new, calculated properties on output objects based on the values of input objects.</span></span>
<span data-ttu-id="e7208-109">La propriété calculée est définie par une [Hashtable](about_hash_tables.md) contenant des paires clé-valeur qui spécifient le nom de la nouvelle propriété, une expression pour calculer la valeur et des informations de mise en forme facultatives.</span><span class="sxs-lookup"><span data-stu-id="e7208-109">The calculated property is defined by a [hashtable](about_hash_tables.md) containing key-value pairs that specify the name of the new property, an expression to calculate the value, and optional formatting information.</span></span>

## <a name="supported-cmdlets"></a><span data-ttu-id="e7208-110">Applets de commande prises en charge</span><span class="sxs-lookup"><span data-stu-id="e7208-110">Supported cmdlets</span></span>

<span data-ttu-id="e7208-111">Les applets de commande suivantes prennent en charge les valeurs de propriété calculées pour le paramètre **Property** .</span><span class="sxs-lookup"><span data-stu-id="e7208-111">The following cmdlets support calculated property values for the **Property** parameter.</span></span> <span data-ttu-id="e7208-112">Les `Format-*` applets de commande prennent également en charge les valeurs calculées pour le paramètre **GroupBy** .</span><span class="sxs-lookup"><span data-stu-id="e7208-112">The `Format-*` cmdlets also support calculated values for the **GroupBy** parameter.</span></span>

<span data-ttu-id="e7208-113">La liste suivante détaille les applets de commande qui prennent en charge les propriétés calculées et les paires clé-valeur prises en charge par chaque applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e7208-113">The following list itemizes the cmdlets that support calculated properties and the key-value pairs that are supported by each cmdlet.</span></span>

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - <span data-ttu-id="e7208-114">`name`/`label` -facultatif (ajouté dans PowerShell 6. x)</span><span class="sxs-lookup"><span data-stu-id="e7208-114">`name`/`label` - optional (added in PowerShell 6.x)</span></span>
  - `expression`
  - <span data-ttu-id="e7208-115">`width` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-115">`width` - optional</span></span>
  - <span data-ttu-id="e7208-116">`alignment` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-116">`alignment` - optional</span></span>

- `Format-Custom`
  - `expression`
  - <span data-ttu-id="e7208-117">`depth` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-117">`depth` - optional</span></span>

- `Format-List`
  - <span data-ttu-id="e7208-118">`name`/`label` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-118">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="e7208-119">`formatstring` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-119">`formatstring` - optional</span></span>

  <span data-ttu-id="e7208-120">Ce même jeu de paires clé-valeur s’applique également aux valeurs de propriété calculées transmises au paramètre **GroupBy** pour toutes les `Format-*` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="e7208-120">This same set of key-value pairs also apply to calculated property values passed to the **GroupBy** parameter for all `Format-*` cmdlets.</span></span>

- `Format-Table`
  - <span data-ttu-id="e7208-121">`name`/`label` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-121">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="e7208-122">`formatstring` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-122">`formatstring` - optional</span></span>
  - <span data-ttu-id="e7208-123">`width` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-123">`width` - optional</span></span>
  - <span data-ttu-id="e7208-124">`alignment` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-124">`alignment` - optional</span></span>

- `Format-Wide`
  - `expression`
  - <span data-ttu-id="e7208-125">`formatstring` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-125">`formatstring` - optional</span></span>

- `Group-Object`
  - `expression`

- `Measure-Object`
  - <span data-ttu-id="e7208-126">Ne prend en charge qu’un bloc de script pour l’expression, et non une Hashtable.</span><span class="sxs-lookup"><span data-stu-id="e7208-126">Only supports a script block for the expression, not a hashtable.</span></span>
  - <span data-ttu-id="e7208-127">Non pris en charge dans PowerShell 5,1 et versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="e7208-127">Not supported in PowerShell 5.1 and older.</span></span>

- `Select-Object`
  - <span data-ttu-id="e7208-128">`name`/`label` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-128">`name`/`label` - optional</span></span>
  - `expression`

- `Sort-Object`
  - `expression`
  - <span data-ttu-id="e7208-129">`ascending`/`descending` -facultatif</span><span class="sxs-lookup"><span data-stu-id="e7208-129">`ascending`/`descending` - optional</span></span>

> [!NOTE]
> <span data-ttu-id="e7208-130">La valeur de `expression` peut être un bloc de script au lieu d’une Hashtable.</span><span class="sxs-lookup"><span data-stu-id="e7208-130">The value of the `expression` can be a script block instead of a hashtable.</span></span> <span data-ttu-id="e7208-131">Pour plus d’informations, consultez la section [Remarques](#notes) .</span><span class="sxs-lookup"><span data-stu-id="e7208-131">For more information, see the [Notes](#notes) section.</span></span>

## <a name="hashtable-key-definitions"></a><span data-ttu-id="e7208-132">Définitions de clé de la Hashtable</span><span class="sxs-lookup"><span data-stu-id="e7208-132">Hashtable key definitions</span></span>

- <span data-ttu-id="e7208-133">`name`/`label` -Spécifie le nom de la propriété en cours de création.</span><span class="sxs-lookup"><span data-stu-id="e7208-133">`name`/`label` - Specifies the name of the property being created.</span></span> <span data-ttu-id="e7208-134">Vous pouvez utiliser `name` ou son alias, `label` , interchangeable.</span><span class="sxs-lookup"><span data-stu-id="e7208-134">You can use `name` or its alias, `label`, interchangeably.</span></span>
- <span data-ttu-id="e7208-135">`expression` : Bloc de script utilisé pour calculer la valeur de la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="e7208-135">`expression` - A script block used to calculate the value of the new property.</span></span>
- <span data-ttu-id="e7208-136">`alignment` -Utilisé par les applets de commande qui produisent une sortie tabulaire pour définir la manière dont les valeurs sont affichées dans une colonne.</span><span class="sxs-lookup"><span data-stu-id="e7208-136">`alignment` - Used by cmdlets that produce tabular output to define how the values are displayed in a column.</span></span> <span data-ttu-id="e7208-137">La valeur doit être `'left'` , `'center'` ou `'right'` .</span><span class="sxs-lookup"><span data-stu-id="e7208-137">The value must be `'left'`, `'center'`, or `'right'`.</span></span>
- <span data-ttu-id="e7208-138">`formatstring` : Spécifie une chaîne de format qui définit la façon dont la valeur est mise en forme pour la sortie.</span><span class="sxs-lookup"><span data-stu-id="e7208-138">`formatstring` - Specifies a format string that defines how the value is formatted for output.</span></span> <span data-ttu-id="e7208-139">Pour plus d’informations sur les chaînes de format, consultez [types de format dans .net](/dotnet/standard/base-types/formatting-types).</span><span class="sxs-lookup"><span data-stu-id="e7208-139">For more information about format strings, see [Format types in .NET](/dotnet/standard/base-types/formatting-types).</span></span>
- <span data-ttu-id="e7208-140">`width` -Spécifie la largeur maximale d’une colonne dans une table lorsque la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="e7208-140">`width` - Specifies the maximum width column in a table when the value is displayed.</span></span> <span data-ttu-id="e7208-141">La valeur doit être supérieure à `0` .</span><span class="sxs-lookup"><span data-stu-id="e7208-141">The value must be greater than `0`.</span></span>
- <span data-ttu-id="e7208-142">`depth` -Le paramètre **Depth** de `Format-Custom` spécifie la profondeur d’expansion pour toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="e7208-142">`depth` - The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="e7208-143">La `depth` clé vous permet de spécifier la profondeur d’expansion par propriété.</span><span class="sxs-lookup"><span data-stu-id="e7208-143">The `depth` key allows you to specify the depth of expansion per property.</span></span>
- <span data-ttu-id="e7208-144">`ascending` / `descending` -Vous permet de spécifier l’ordre de tri pour une ou plusieurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="e7208-144">`ascending` / `descending` - Allows you to specify the order of sorting for one or more properties.</span></span> <span data-ttu-id="e7208-145">Il s’agit de valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="e7208-145">These are boolean values.</span></span>

<span data-ttu-id="e7208-146">Les clés Hashtable n’ont pas besoin d’être épelées tant que le préfixe de nom spécifié n’est pas ambigu.</span><span class="sxs-lookup"><span data-stu-id="e7208-146">The hashtable keys need not be spelled out as long as the specified name prefix is unambiguous.</span></span> <span data-ttu-id="e7208-147">Par exemple, `n` peut être utilisé à la place de `Name` et `e` peut être utilisé à la place de `Expression` .</span><span class="sxs-lookup"><span data-stu-id="e7208-147">For example, `n` can be used in lieu of `Name` and `e` can be used in lieu of `Expression`.</span></span>

## <a name="examples"></a><span data-ttu-id="e7208-148">Exemples</span><span class="sxs-lookup"><span data-stu-id="e7208-148">Examples</span></span>

### <a name="compare-object"></a><span data-ttu-id="e7208-149">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="e7208-149">Compare-Object</span></span>

<span data-ttu-id="e7208-150">Avec les propriétés calculées, vous pouvez contrôler la façon dont les propriétés des objets d’entrée sont comparées.</span><span class="sxs-lookup"><span data-stu-id="e7208-150">With calculated properties, you can control how the properties of the input objects are compared.</span></span> <span data-ttu-id="e7208-151">Dans cet exemple, au lieu de comparer directement les valeurs, les valeurs sont comparées au résultat de l’opération arithmétique (modulo de 2).</span><span class="sxs-lookup"><span data-stu-id="e7208-151">In this example, rather than comparing the values directly, the values are compared to the result of the arithmetic operation (modulus of 2).</span></span>

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a><span data-ttu-id="e7208-152">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="e7208-152">ConvertTo-Html</span></span>

<span data-ttu-id="e7208-153">`ConvertTo-Html` peut convertir une collection d’objets en tableau HTML.</span><span class="sxs-lookup"><span data-stu-id="e7208-153">`ConvertTo-Html` can convert a collection of objects to an HTML table.</span></span>
<span data-ttu-id="e7208-154">Les propriétés calculées vous permettent de contrôler la façon dont la table est présentée.</span><span class="sxs-lookup"><span data-stu-id="e7208-154">Calculated properties allow you to control how the table is presented.</span></span>

```powershell
Get-Alias |
  ConvertTo-Html Name,
                 Definition,
                 @{
                    expr={$_.Parameters.Keys.Count}
                    align='center'
                 } |
    Out-File .\aliases.htm -Force
```

<span data-ttu-id="e7208-155">Cet exemple crée une table HTML contenant une liste d’alias PowerShell et les paramètres de nombre pour chaque commande avec alias.</span><span class="sxs-lookup"><span data-stu-id="e7208-155">This example creates an HTML table containing a list of PowerShell aliases and the number parameters for each aliased command.</span></span> <span data-ttu-id="e7208-156">Les valeurs de la colonne **ParameterCount** sont centrées.</span><span class="sxs-lookup"><span data-stu-id="e7208-156">The values of **ParameterCount** column are centered.</span></span>

### <a name="format-custom"></a><span data-ttu-id="e7208-157">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="e7208-157">Format-Custom</span></span>

<span data-ttu-id="e7208-158">`Format-Custom` fournit une vue personnalisée d’un objet dans un format semblable à une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="e7208-158">`Format-Custom` provides a custom view of an object in a format similar to a class definition.</span></span> <span data-ttu-id="e7208-159">Les objets plus complexes peuvent contenir des membres profondément imbriqués avec des types complexes.</span><span class="sxs-lookup"><span data-stu-id="e7208-159">More complex objects can contain members that are deeply nested with complex types.</span></span> <span data-ttu-id="e7208-160">Le paramètre **Depth** de `Format-Custom` spécifie la profondeur d’expansion pour toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="e7208-160">The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="e7208-161">La `depth` clé vous permet de spécifier la profondeur d’expansion par propriété.</span><span class="sxs-lookup"><span data-stu-id="e7208-161">The `depth` key allows you to specify the depth of expansion per property.</span></span>

<span data-ttu-id="e7208-162">Dans cet exemple, la `depth` clé simplifie la sortie personnalisée pour l' `Get-Date` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e7208-162">In this example, the `depth` key simplifies the custom output for the `Get-Date` cmdlet.</span></span> <span data-ttu-id="e7208-163">`Get-Date` retourne un objet **DateTime** .</span><span class="sxs-lookup"><span data-stu-id="e7208-163">`Get-Date` returns a **DateTime** object.</span></span> <span data-ttu-id="e7208-164">La propriété de **Date** de cet objet est également un objet **DateTime** , de sorte que l’objet est imbriqué.</span><span class="sxs-lookup"><span data-stu-id="e7208-164">The **Date** property of this object is also a **DateTime** object, so the object is nested.</span></span>

```powershell
Get-Date | Format-Custom @{expr={$_.Date};depth=1},TimeOfDay
```

```Output
class DateTime
{
  $_.Date =
    class DateTime
    {
      Date = 8/7/2020 12:00:00 AM
      Day = 7
      DayOfWeek = Friday
      DayOfYear = 220
      Hour = 0
      Kind = Local
      Millisecond = 0
      Minute = 0
      Month = 8
      Second = 0
      Ticks = 637323552000000000
      TimeOfDay = 00:00:00
      Year = 2020
      DateTime = Friday, August 07, 2020 12:00:00 AM
    }
  TimeOfDay =
    class TimeSpan
    {
      Ticks = 435031592302
      Days = 0
      Hours = 12
      Milliseconds = 159
      Minutes = 5
      Seconds = 3
      TotalDays = 0.503508787386574
      TotalHours = 12.0842108972778
      TotalMilliseconds = 43503159.2302
      TotalMinutes = 725.052653836667
      TotalSeconds = 43503.1592302
    }
}
```

### <a name="format-list"></a><span data-ttu-id="e7208-165">Format-List</span><span class="sxs-lookup"><span data-stu-id="e7208-165">Format-List</span></span>

<span data-ttu-id="e7208-166">Dans cet exemple, nous utilisons des propriétés calculées pour modifier le nom et le format de la sortie de `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="e7208-166">In this example, we use calculated properties to change the name and format of the output from `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem *.json -File |
  Format-List Fullname,
              @{
                 name='Modified'
                 expression={$_.LastWriteTime}
                 formatstring='O'
              },
              @{
                 name='Size'
                 expression={$_.Length/1KB}
                 formatstring='N2'
              }
```

```Output
FullName : C:\Git\PS-Docs\PowerShell-Docs\.markdownlint.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.40

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.publish.config.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.25

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.redirection.json
Modified : 2020-07-27T13:05:24.3887629-07:00
Size     : 324.60
```

### <a name="format-table"></a><span data-ttu-id="e7208-167">Format-Table</span><span class="sxs-lookup"><span data-stu-id="e7208-167">Format-Table</span></span>

<span data-ttu-id="e7208-168">Dans cet exemple, la propriété calculée ajoute une propriété de **type** utilisée pour classifier les fichiers selon le type de contenu.</span><span class="sxs-lookup"><span data-stu-id="e7208-168">In this example, the calculated property adds a **Type** property used to classify the files by the content type.</span></span>

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Format-Table Name, Length -GroupBy @{
      name='Type'
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
   Type: Metacontent

Name              Length
----              ------
ThirdPartyNotices   1229
LICENSE-CODE        1106
LICENSE            19047

   Type: Configuration

Name                                Length
----                                ------
.editorconfig                          183
.gitattributes                         419
.gitignore                             228
.markdownlint.json                    2456
.openpublishing.publish.config.json   2306
.openpublishing.redirection.json    332394
.localization-config                   232

   Type: Content

Name            Length
----            ------
README.md         3355
CONTRIBUTING.md    247

   Type: Automation

Name                      Length
----                      ------
.openpublishing.build.ps1    796
build.ps1                   7495
ci.yml                       645
ci-steps.yml                2035
daily.yml                   1271
```

### <a name="format-wide"></a><span data-ttu-id="e7208-169">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="e7208-169">Format-Wide</span></span>

<span data-ttu-id="e7208-170">L' `Format-Wide` applet de commande vous permet d’afficher la valeur d’une propriété pour les objets d’une collection sous la forme d’une liste à plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="e7208-170">The `Format-Wide` cmdlet allows you to display the value of one property for objects in a collection as a multi-column list.</span></span>

<span data-ttu-id="e7208-171">Pour cet exemple, nous souhaitons voir le nom de fichier et la taille (en kilo-octets) comme une liste étendue.</span><span class="sxs-lookup"><span data-stu-id="e7208-171">For this example, we want to see the filename and the size (in kilobytes) as a wide listing.</span></span> <span data-ttu-id="e7208-172">Étant donné que `Format-Wide` n’affiche pas plus d’une propriété, nous utilisons une propriété calculée pour combiner la valeur de deux propriétés en une seule valeur.</span><span class="sxs-lookup"><span data-stu-id="e7208-172">Since `Format-Wide` does not display more than one property, we use a calculated property to combine the value of two properties into a single value.</span></span>

```powershell
Get-ChildItem -File |
  Format-Wide -Property @{e={'{0} ({1:N2}kb)' -f $_.name,($_.length/1kb)}}
```

```Output
.editorconfig (0.18kb)                          .gitattributes (0.41kb)
.gitignore (0.22kb)                             .localization-config (0.23kb)
.markdownlint.json (2.40kb)                     .openpublishing.build.ps1 (0.78kb)
.openpublishing.publish.config.json (2.25kb)    .openpublishing.redirection.json (324.60kb)
build.ps1 (7.32kb)                              ci.yml (0.63kb)
ci-steps.yml (1.99kb)                           CONTRIBUTING.md (0.24kb)
daily.yml (1.24kb)                              LICENSE (18.60kb)
LICENSE-CODE (1.08kb)                           README.md (3.28kb)
ThirdPartyNotices (1.20kb)
```

### <a name="group-object"></a><span data-ttu-id="e7208-173">Group-Object</span><span class="sxs-lookup"><span data-stu-id="e7208-173">Group-Object</span></span>

<span data-ttu-id="e7208-174">L' `Group-Object` applet de commande affiche les objets dans des groupes en fonction de la valeur d’une propriété spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e7208-174">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span> <span data-ttu-id="e7208-175">Dans cet exemple, la propriété calculée compte le nombre de fichiers de chaque type de contenu.</span><span class="sxs-lookup"><span data-stu-id="e7208-175">In this example, the calculated property counts the number of files of each content type.</span></span>

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Group-Object -NoElement -Property @{
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
Count Name
----- ----
    5 Automation
    7 Configuration
    2 Content
    3 Metacontent
```

### <a name="select-object"></a><span data-ttu-id="e7208-176">Select-Object</span><span class="sxs-lookup"><span data-stu-id="e7208-176">Select-Object</span></span>

<span data-ttu-id="e7208-177">Vous pouvez utiliser des propriétés calculées pour ajouter des membres supplémentaires à la sortie d’objets avec l’applet de commande `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="e7208-177">You can use calculated properties to add additional members to the objects output with the `Select-Object` cmdlet.</span></span> <span data-ttu-id="e7208-178">Dans cet exemple, nous répertorions les alias PowerShell qui commencent par la lettre `C` .</span><span class="sxs-lookup"><span data-stu-id="e7208-178">In this example, we are listing the PowerShell aliases that begin with the letter `C`.</span></span> <span data-ttu-id="e7208-179">À l’aide de `Select-Object` , nous sortons l’alias, l’applet de commande à laquelle il est mappé et le nombre de paramètres définis pour l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e7208-179">Using `Select-Object`, we output the alias, the cmdlet it's mapped to, and a count for the number of parameters defined for the cmdlet.</span></span> <span data-ttu-id="e7208-180">À l’aide d’une propriété calculée, nous pouvons créer la propriété **ParameterCount** .</span><span class="sxs-lookup"><span data-stu-id="e7208-180">Using a calculated property, we can create the **ParameterCount** property.</span></span>

```powershell
$aliases = Get-Alias c* |
  Select-Object Name,
                Definition,
                @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                }
$aliases | Get-Member
$aliases
```

```Output
   TypeName: Selected.System.Management.Automation.AliasInfo

Name           MemberType   Definition
----           ----------   ----------
Equals         Method       bool Equals(System.Object obj)
GetHashCode    Method       int GetHashCode()
GetType        Method       type GetType()
ToString       Method       string ToString()
Definition     NoteProperty string Definition=Get-Content
Name           NoteProperty string Name=cat
ParameterCount NoteProperty System.Int32 ParameterCount=21

Name    Definition         ParameterCount
----    ----------         --------------
cat     Get-Content                    21
cd      Set-Location                   15
cdd     Push-MyLocation                 1
chdir   Set-Location                   15
clc     Clear-Content                  20
clear   Clear-Host                      0
clhy    Clear-History                  17
cli     Clear-Item                     20
clp     Clear-ItemProperty             22
cls     Clear-Host                      0
clv     Clear-Variable                 19
cnsn    Connect-PSSession              29
compare Compare-Object                 20
copy    Copy-Item                      24
cp      Copy-Item                      24
cpi     Copy-Item                      24
cpp     Copy-ItemProperty              23
cvpa    Convert-Path                   13
```

### <a name="sort-object"></a><span data-ttu-id="e7208-181">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="e7208-181">Sort-Object</span></span>

<span data-ttu-id="e7208-182">À l’aide des propriétés calculées, vous pouvez trier les données dans différents ordres par propriété.</span><span class="sxs-lookup"><span data-stu-id="e7208-182">Using the calculated properties, you can sort data in different orders per property.</span></span> <span data-ttu-id="e7208-183">Cet exemple trie les données d’un fichier CSV dans l’ordre croissant par **Date** .</span><span class="sxs-lookup"><span data-stu-id="e7208-183">This example sorts data from a CSV file in ascending order by **Date** .</span></span> <span data-ttu-id="e7208-184">Mais dans chaque date, il trie les lignes par ordre décroissant de **UnitsSold** .</span><span class="sxs-lookup"><span data-stu-id="e7208-184">But within each date, it sorts the rows in descending order by **UnitsSold** .</span></span>

```powershell
Import-Csv C:\temp\sales-data.csv |
  Sort-Object Date, @{expr={$_.UnitsSold}; desc=$true}, Salesperson  |
    Select-Object Date, Salesperson, UnitsSold
```

```Output
Date       Salesperson UnitsSold
----       ----------- ---------
2020-08-01 Sally       3
2020-08-01 Anne        2
2020-08-01 Fred        1
2020-08-02 Anne        6
2020-08-02 Fred        2
2020-08-02 Sally       0
2020-08-03 Anne        5
2020-08-03 Sally       3
2020-08-03 Fred        1
2020-08-04 Anne        2
2020-08-04 Fred        2
2020-08-04 Sally       2
```

## <a name="notes"></a><span data-ttu-id="e7208-185">Notes</span><span class="sxs-lookup"><span data-stu-id="e7208-185">Notes</span></span>

- <span data-ttu-id="e7208-186">Vous pouvez spécifier _directement_ le bloc de script d’expression, en tant qu’argument, au lieu de le spécifier comme `Expression` entrée dans une Hashtable.</span><span class="sxs-lookup"><span data-stu-id="e7208-186">You may specify the expression script block _directly_ , as an argument, rather than specifying it as the `Expression` entry in a hashtable.</span></span> <span data-ttu-id="e7208-187">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e7208-187">For example:</span></span>

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  <span data-ttu-id="e7208-188">Cet exemple est pratique pour les applets de commande qui ne nécessitent pas (ou prennent en charge) le nommage d’une propriété via la `Name` clé, par exemple `Sort-Object` , `Group-Object` et `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="e7208-188">This example is convenient for cmdlets that do not require (or support) naming a property via the `Name` key, such as `Sort-Object`, `Group-Object`, and `Measure-Object`.</span></span>

  <span data-ttu-id="e7208-189">Pour les applets de commande qui prennent en charge l’attribution d’un nom à la propriété, le bloc de script est converti en une chaîne et utilisé comme nom de la propriété dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="e7208-189">For cmdlets that support naming the property, the script block is converted to a string and used as the name of the property in the output.</span></span>

- <span data-ttu-id="e7208-190">`Expression` les blocs de script s’exécutent dans des portées _enfants_ , ce qui signifie que les variables de l’appelant ne peuvent pas être modifiées directement.</span><span class="sxs-lookup"><span data-stu-id="e7208-190">`Expression` script blocks run in _child_ scopes, meaning that the caller's variables cannot be directly modified.</span></span>

- <span data-ttu-id="e7208-191">La logique de pipeline est appliquée à la sortie des `Expression` blocs de script.</span><span class="sxs-lookup"><span data-stu-id="e7208-191">Pipeline logic is applied to the output from `Expression` script blocks.</span></span> <span data-ttu-id="e7208-192">Cela signifie que la génération d’un tableau à un seul élément entraîne le désencapsulage de ce tableau.</span><span class="sxs-lookup"><span data-stu-id="e7208-192">This means that outputting a single-element array causes that array to be unwrapped.</span></span>

- <span data-ttu-id="e7208-193">Pour la plupart des cmdlets, les erreurs contenues dans les blocs de script d’expression sont ignorées en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="e7208-193">For most cmdlets, errors inside expression script blocks are quietly ignored.</span></span>
  <span data-ttu-id="e7208-194">Pour `Sort-Object` , les erreurs d’instruction et de fin de script sont _générées_ , mais elles ne terminent pas l’instruction.</span><span class="sxs-lookup"><span data-stu-id="e7208-194">For `Sort-Object`, statement-terminating and script-terminating errors are _output_ but they do not terminate the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7208-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7208-195">See Also</span></span>

[<span data-ttu-id="e7208-196">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="e7208-196">about_Hash_Tables</span></span>](about_hash_tables.md)

[<span data-ttu-id="e7208-197">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="e7208-197">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="e7208-198">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="e7208-198">ConvertTo-Html</span></span>](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[<span data-ttu-id="e7208-199">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="e7208-199">Format-Custom</span></span>](xref:Microsoft.PowerShell.Utility.Format-Custom)

[<span data-ttu-id="e7208-200">Format-List</span><span class="sxs-lookup"><span data-stu-id="e7208-200">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)

[<span data-ttu-id="e7208-201">Format-Table</span><span class="sxs-lookup"><span data-stu-id="e7208-201">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="e7208-202">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="e7208-202">Format-Wide</span></span>](xref:Microsoft.PowerShell.Utility.Format-Wide)

[<span data-ttu-id="e7208-203">Group-Object</span><span class="sxs-lookup"><span data-stu-id="e7208-203">Group-Object</span></span>](xref:Microsoft.PowerShell.Utility.Group-Object)

[<span data-ttu-id="e7208-204">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="e7208-204">Measure-Object</span></span>](xref:Microsoft.PowerShell.Utility.Measure-Object)

[<span data-ttu-id="e7208-205">Select-Object</span><span class="sxs-lookup"><span data-stu-id="e7208-205">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="e7208-206">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="e7208-206">Sort-Object</span></span>](xref:Microsoft.PowerShell.Utility.Sort-Object)

[<span data-ttu-id="e7208-207">Types de format dans .NET</span><span class="sxs-lookup"><span data-stu-id="e7208-207">Format types in .NET</span></span>](/dotnet/standard/base-types/formatting-types)
