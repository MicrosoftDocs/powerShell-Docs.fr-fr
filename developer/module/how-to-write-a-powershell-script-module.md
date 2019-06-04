---
title: Comment écrire un Module de Script PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470802"
---
# <a name="how-to-write-a-powershell-script-module"></a>Guide pratique pour écrire un module de script PowerShell

Un module de script est essentiellement n’importe quel script PowerShell valide enregistré dans une extension .psm1. Cette extension permet au moteur de PowerShell à utiliser un nombre de règles et des applets de commande sur votre fichier. La plupart de ces fonctionnalités est là pour vous aider à installer votre code sur d’autres systèmes, ainsi que gérer d’étendue. Vous pouvez également utiliser un fichier de manifeste de module, qui décrire les installations encore plus complexes et des solutions.

## <a name="writing-a-powershell-script-module"></a>Écriture d’un Module de Script PowerShell

Vous créez un module de script en enregistrant un script PowerShell valide dans un fichier .psm1, puis enregistrez ce fichier dans un répertoire situé où PowerShell peut le trouver. Dans ce dossier, que vous pouvez également placer les ressources que vous avez besoin pour exécuter votre script, ainsi qu’un fichier manifest qui décrit à PowerShell le fonctionnement de votre module.

#### <a name="to-create-a-basic-powershell-module"></a>Pour créer un PowerShell Module de base

1. Prenez un script PowerShell existant et enregistrez le script avec l’extension .psm1.

   L’enregistrement d’un script avec le .psm1 extension signifie que vous pouvez utiliser les applets de commande du module, tel que [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), dessus. Ces applets de commande se trouvent principalement afin que vous pouvez facilement importer et exporter votre code sur des systèmes de l’autre utilisateur. (L’autre solution serait pour charger votre code sur les autres systèmes, puis « dot sourcer » dans la mémoire active, ce qui n’est pas une solution évolutive en particulier). Pour plus d’informations, consultez le **Variables et des applets de commande Module** section [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Notez que, par défaut, toutes les fonctions dans votre script sont accessibles aux utilisateurs qui importer votre fichier .psm1, mais les propriétés ne sont pas.

   Un exemple de script PowerShell, intitulé `Show-Calendar`, est disponible à la fin de cette rubrique.

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

2. Pour contrôler l’accès utilisateur à certaines fonctions ou des propriétés, appelez [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) à la fin de votre script.

   L’exemple de code en bas de la page a une seule fonction, ce qui est exposée par défaut. Toutefois, il est recommandé que vous appelez explicitement les fonctions que vous souhaitez exposer, comme décrit dans le code suivant :

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Vous pouvez également limiter ce qui est importé à l’aide d’un manifeste de module. Pour plus d’informations, consultez [importation d’un PowerShell Module](./importing-a-powershell-module.md) et [comment écrire un manifeste de Module PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Si vous avez des modules devant votre propre module de chargement, vous pouvez les utiliser avec un appel à `Import-Module`, en haut de votre propre module.

   `Import-Module` est une applet de commande importe un module ciblé sur un système. Par conséquent, il est également utilisé à un moment ultérieur dans la procédure pour installer votre propre module également. L’exemple de code en bas de cette page n’utilise pas les modules d’importation. Si c’était le cas, toutefois, elles sont indiquées en haut du fichier, comme décrit dans le code suivant :

   ```powershell
   Import-Module GenericModule
   ```

4. Pour décrire votre module sur le système d’aide de PowerShell, vous pouvez utiliser des commentaires de l’aide standard dans le fichier ou créer un fichier d’aide supplémentaire.

   L’exemple de code en bas de cette rubrique inclut les informations d’aide dans les commentaires. Vous pouvez également écrire des fichiers XML développés qui contiennent le contenu d’aide supplémentaire. Pour plus d’informations, consultez [l’aider à écrire pour Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).

5. Si vous avez des modules complémentaires, des fichiers XML ou tout autre contenu que vous souhaitez empaqueter avec votre module, vous pouvez le faire avec un manifeste de module.

   Un manifeste de module est un fichier qui contient les noms des autres modules, dispositions de répertoire, les numéros de contrôle de version, créer des données et autres éléments d’information. PowerShell utilise le fichier de manifeste de module pour organiser et déployer votre solution. Toutefois, en raison de la nature relativement simple de cet exemple, un fichier manifeste n’était pas nécessaire. Pour plus d’informations, consultez [manifestes de Module](./how-to-write-a-powershell-module-manifest.md).

6. Pour installer et exécuter votre module, enregistrer le module dans l’un des chemins PowerShell appropriées et effectuer un appel à `Import-Module`.

   Les chemins d’accès où vous pouvez installer votre module sont situés dans le `$env:PSModulePath` (variable globale). Par exemple, un chemin d’accès commun pour enregistrer un module sur un système serait `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Veillez à créer un dossier pour votre module d’exister, même si elle est uniquement un fichier .psm1 unique. Si vous n’avez pas enregistré votre module à un de ces chemins d’accès, vous seriez obligé de passer à l’emplacement de votre module dans l’appel à `Import-Module`. (Dans le cas contraire, PowerShell pas serait en mesure de le retrouver.) À partir de PowerShell 3.0, si vous avez placé votre module dans un des chemins de module PowerShell, vous n’avez pas besoin pour l’importer explicitement. Vous module est chargé automatiquement lorsqu’un utilisateur appelle votre fonction.
   Pour plus d’informations sur le chemin d’accès du module, consultez [importation d’un PowerShell Module](./importing-a-powershell-module.md) et [Variable d’environnement PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Pour supprimer un module de service actif, effectuez un appel à [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   Notez que [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) supprime votre module de la mémoire active - il ne supprime pas réellement il d’où vous avez enregistré les fichiers de module.

### <a name="show-calendar-code-example"></a>Exemple de code Show-Calendar

L’exemple suivant est un module de script simple qui contient une fonction unique nommée `Show-Calendar`.
Cette fonction affiche une représentation visuelle d’un calendrier. En outre, l’exemple contient les chaînes d’aide de PowerShell pour le résumé, la description, les valeurs de paramètre et exemple. Notez que la dernière ligne de code garantit que le `Show-Calendar` fonction est exportée en tant que module membre quand le module est importé.

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
