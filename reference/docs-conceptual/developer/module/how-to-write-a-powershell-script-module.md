---
title: Comment écrire un module de script PowerShell | Microsoft Docs
ms.date: 11/21/2019
ms.openlocfilehash: dc387909a9e55df9f1846b02755e284c408f7dc6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784892"
---
# <a name="how-to-write-a-powershell-script-module"></a>Guide pratique pour écrire un module de script PowerShell

Un module de script est un script PowerShell valide enregistré dans une `.psm1` extension. Cette extension permet au moteur PowerShell d’utiliser des règles et des applets de commande de module sur votre fichier. La plupart de ces fonctionnalités sont là pour vous aider à installer votre code sur d’autres systèmes, ainsi qu’à gérer la portée. Vous pouvez également utiliser un fichier manifeste de module, qui décrit des installations et des solutions plus complexes.

## <a name="writing-a-powershell-script-module"></a>Écriture d’un module de script PowerShell

Pour créer un module de script, enregistrez un script PowerShell valide dans un `.psm1` fichier. Le script et le répertoire dans lequel il est stocké doivent utiliser le même nom. Par exemple, un script nommé `MyPsScript.psm1` est stocké dans un répertoire nommé `MyPsScript` .

Le répertoire du module doit se trouver dans un chemin d’accès spécifié dans `$env:PSModulePath` . Le répertoire du module peut contenir toutes les ressources nécessaires pour exécuter le script, ainsi qu’un fichier manifeste de module qui décrit le fonctionnement de votre module dans PowerShell.

## <a name="create-a-basic-powershell-module"></a>Créer un module PowerShell de base

Les étapes suivantes décrivent comment créer un module PowerShell.

1. Enregistrer un script PowerShell avec une `.psm1` extension. Utilisez le même nom pour le script et le répertoire dans lequel le script est enregistré.

   L’enregistrement d’un script avec l' `.psm1` extension signifie que vous pouvez utiliser les applets de commande du module, telles que [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module). Les applets de commande de module existent principalement pour vous permettre d’importer et d’exporter votre code sur les systèmes d’autres utilisateurs. L’autre solution consiste à charger votre code sur d’autres systèmes, puis à le mettre en mémoire dans la mémoire active, ce qui n’est pas une solution évolutive. Pour plus d’informations, voir [fonctionnement d’un module Windows PowerShell](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).
   Par défaut, quand les utilisateurs importent votre `.psm1` fichier, toutes les fonctions de votre script sont accessibles, mais les variables ne le sont pas.

   Un exemple de script PowerShell, autorisé `Show-Calendar` , est disponible à la fin de cet article.

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. Pour contrôler l’accès utilisateur à certaines fonctions ou variables, appelez [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) à la fin de votre script.

   L’exemple de code en bas de l’article n’a qu’une seule fonction, qui est exposée par défaut. Toutefois, il est recommandé d’appeler explicitement les fonctions que vous souhaitez exposer, comme décrit dans le code suivant :

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Vous pouvez limiter les éléments importés à l’aide d’un manifeste de module. Pour plus d’informations, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md) et [écriture d’un manifeste de module PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Si vous avez des modules qui doivent être chargés par votre propre module, vous pouvez utiliser `Import-Module` , en haut de votre module.

   L' `Import-Module` applet de commande importe un module ciblé sur un système et peut être utilisé ultérieurement dans la procédure pour installer votre propre module. L’exemple de code en bas de cet article n’utilise pas de modules d’importation. Mais si c’est le cas, ils sont répertoriés en haut du fichier, comme illustré dans le code suivant :

   ```powershell
   Import-Module GenericModule
   ```

4. Pour décrire votre module au système d’aide PowerShell, vous pouvez soit utiliser des commentaires d’aide standard dans le fichier, soit créer un fichier d’aide supplémentaire.

   L’exemple de code en bas de cet article contient des informations d’aide dans les commentaires. Vous pouvez également écrire des fichiers XML développés qui contiennent du contenu d’aide supplémentaire. Pour plus d’informations, consultez [écriture de l’aide pour les modules Windows PowerShell](./writing-help-for-windows-powershell-modules.md).

5. Si vous avez d’autres modules, fichiers XML ou tout autre contenu que vous souhaitez empaqueter avec votre module, vous pouvez utiliser un manifeste de module.

   Un manifeste de module est un fichier qui contient les noms d’autres modules, les dispositions de répertoire, les numéros de versioning, les données d’auteur et d’autres informations. PowerShell utilise le fichier manifeste du module pour organiser et déployer votre solution. Pour plus d’informations, consultez [Comment écrire un manifeste de module PowerShell](./how-to-write-a-powershell-module-manifest.md).

6. Pour installer et exécuter votre module, enregistrez le module dans l’un des chemins PowerShell appropriés et utilisez `Import-Module` .

   Les chemins d’accès où vous pouvez installer votre module se trouvent dans la `$env:PSModulePath` variable globale. Par exemple, un chemin d’accès commun pour enregistrer un module sur un système est `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>` . Veillez à créer un répertoire pour votre module qui utilise le même nom que le module de script, même s’il s’agit d’un seul `.psm1` fichier. Si vous n’avez pas enregistré votre module dans l’un de ces chemins d’accès, vous devez spécifier l’emplacement du module dans la `Import-Module` commande. Dans le cas contraire, PowerShell ne serait pas en mesure de trouver le module.

   À compter de PowerShell 3,0, si vous avez placé votre module dans l’un des chemins d’accès des modules PowerShell, vous n’avez pas besoin de l’importer explicitement. Votre module est chargé automatiquement lorsqu’un utilisateur appelle votre fonction. Pour plus d’informations sur le chemin d’accès au module, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md) et [modification du chemin d’installation de PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Pour supprimer un module du service actif dans la session PowerShell active, utilisez [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   > [!NOTE]
   > `Remove-Module`supprime un module de la session PowerShell active, mais ne désinstalle pas le module ou ne supprime pas les fichiers du module.

## <a name="show-calendar-code-example"></a>Show-exemple de code de calendrier

L’exemple suivant est un module de script qui contient une seule fonction nommée `Show-Calendar` . Cette fonction affiche une représentation visuelle d’un calendrier. L’exemple contient les chaînes d’aide PowerShell pour le synopsis, la description, les valeurs de paramètre et le code. Quand le module est importé, la `Export-ModuleMember` commande garantit que la `Show-Calendar` fonction est exportée en tant que membre de module.

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
