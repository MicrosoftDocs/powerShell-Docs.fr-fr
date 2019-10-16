---
title: Comment écrire un module de script PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360688"
---
# <a name="how-to-write-a-powershell-script-module"></a>Guide pratique pour écrire un module de script PowerShell

Un module de script est essentiellement tout script PowerShell valide enregistré dans une extension. psm1. Cette extension permet au moteur PowerShell d’utiliser un certain nombre de règles et d’applets de commande sur votre fichier. La plupart de ces fonctionnalités sont là pour vous aider à installer votre code sur d’autres systèmes, ainsi qu’à gérer la portée. Vous pouvez également utiliser un fichier manifeste de module, qui peut décrire des installations et des solutions encore plus complexes.

## <a name="writing-a-powershell-script-module"></a>Écriture d’un module de script PowerShell

Pour créer un module de script, enregistrez un script PowerShell valide dans un fichier. psm1, puis enregistrez ce fichier dans un répertoire situé dans lequel PowerShell peut le trouver. Dans ce dossier, vous pouvez également placer toutes les ressources dont vous avez besoin pour exécuter votre script, ainsi qu’un fichier manifeste qui décrit le fonctionnement de votre module dans PowerShell.

#### <a name="to-create-a-basic-powershell-module"></a>Pour créer un module PowerShell de base

1. Prenez un script PowerShell existant et enregistrez le script avec une extension. psm1.

   L’enregistrement d’un script avec l’extension. psm1 signifie que vous pouvez utiliser les applets de commande du module, telles que [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), sur celui-ci. Ces applets de commande existent principalement pour vous permettre d’importer et d’exporter facilement votre code sur les systèmes d’autres utilisateurs. (L’autre solution consisterait à charger votre code sur d’autres systèmes, puis à le mettre sous-source dans la mémoire active, ce qui n’est pas une solution particulièrement Scalable.) Pour plus d’informations, consultez la section sur les **applets** de commande et les variables de module dans les [modules Windows PowerShell](./understanding-a-windows-powershell-module.md) . Notez que, par défaut, toutes les fonctions de votre script sont accessibles aux utilisateurs qui importent votre fichier. psm1, mais les propriétés ne le sont pas.

   Un exemple de script PowerShell, autorisé `Show-Calendar`, est disponible à la fin de cette rubrique.

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

2. Pour contrôler l’accès utilisateur à certaines fonctions ou propriétés, appelez [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) à la fin de votre script.

   L’exemple de code en bas de la page n’a qu’une seule fonction, qui est exposée par défaut. Toutefois, il est recommandé d’appeler explicitement les fonctions que vous souhaitez exposer, comme décrit dans le code suivant :

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Vous pouvez également limiter les éléments importés à l’aide d’un manifeste de module. Pour plus d’informations, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md) et [écriture d’un manifeste de module PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Si vous avez des modules qui doivent être chargés par votre propre module, vous pouvez les utiliser avec un appel à `Import-Module`, en haut de votre propre module.

   `Import-Module` est une applet de commande qui importe un module ciblé sur un système. Par conséquent, il est également utilisé à un moment ultérieur de la procédure pour installer également votre propre module. L’exemple de code en bas de cette page n’utilise pas de modules d’importation. Dans le cas contraire, ils seraient répertoriés en haut du fichier, comme décrit dans le code suivant :

   ```powershell
   Import-Module GenericModule
   ```

4. Pour décrire votre module au système d’aide PowerShell, vous pouvez soit utiliser des commentaires d’aide standard dans le fichier, soit créer un fichier d’aide supplémentaire.

   L’exemple de code en bas de cette rubrique contient des informations d’aide dans les commentaires. Vous pouvez également écrire des fichiers XML développés qui contiennent du contenu d’aide supplémentaire. Pour plus d’informations, consultez [écriture de l’aide pour les modules Windows PowerShell](./writing-help-for-windows-powershell-modules.md).

5. Si vous avez d’autres modules, fichiers XML ou tout autre contenu que vous souhaitez empaqueter avec votre module, vous pouvez le faire avec un manifeste de module.

   Un manifeste de module est un fichier qui contient les noms d’autres modules, les dispositions de répertoire, les numéros de versioning, les données d’auteur et d’autres informations. PowerShell utilise le fichier manifeste du module pour organiser et déployer votre solution. Toutefois, en raison de la nature relativement simple de cet exemple, un fichier manifeste n’était pas nécessaire. Pour plus d’informations, consultez [manifestes de module](./how-to-write-a-powershell-module-manifest.md).

6. Pour installer et exécuter votre module, enregistrez le module dans l’un des chemins PowerShell appropriés et effectuez un appel à `Import-Module`.

   Les chemins d’accès où vous pouvez installer votre module se trouvent dans la variable globale `$env:PSModulePath`. Par exemple, un chemin d’accès commun pour enregistrer un module sur un système serait `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Veillez à créer un dossier dans lequel le module doit exister, même s’il s’agit d’un seul fichier. psm1. Si vous n’avez pas enregistré votre module dans l’un de ces chemins d’accès, vous devez passer l’emplacement de votre module dans l’appel à `Import-Module`. (Dans le cas contraire, PowerShell ne sera pas en mesure de le trouver.) À compter de PowerShell 3,0, si vous avez placé votre module dans l’un des chemins d’accès au module PowerShell, vous n’avez pas besoin de l’importer explicitement. Le module est chargé automatiquement lorsqu’un utilisateur appelle votre fonction.
   Pour plus d’informations sur le chemin d’accès au module, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md) et d’une [variable d’environnement PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Pour supprimer un module d’un service actif, effectuez un appel à [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   Notez que [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) supprime votre module de la mémoire active. il ne le supprime pas réellement de l’emplacement où vous avez enregistré les fichiers de module.

### <a name="show-calendar-code-example"></a>Show-exemple de code de calendrier

L’exemple suivant est un module de script simple qui contient une fonction unique nommée `Show-Calendar`.
Cette fonction affiche une représentation visuelle d’un calendrier. En outre, l’exemple contient les chaînes d’aide PowerShell pour le synopsis, la description, les valeurs de paramètre et l’exemple. Notez que la dernière ligne de code garantit que la fonction `Show-Calendar` est exportée en tant que membre de module lors de l’importation du module.

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
