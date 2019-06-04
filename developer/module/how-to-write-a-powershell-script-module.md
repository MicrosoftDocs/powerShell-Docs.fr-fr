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
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="cf40c-102">Guide pratique pour écrire un module de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf40c-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="cf40c-103">Un module de script est essentiellement n’importe quel script PowerShell valide enregistré dans une extension .psm1.</span><span class="sxs-lookup"><span data-stu-id="cf40c-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="cf40c-104">Cette extension permet au moteur de PowerShell à utiliser un nombre de règles et des applets de commande sur votre fichier.</span><span class="sxs-lookup"><span data-stu-id="cf40c-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="cf40c-105">La plupart de ces fonctionnalités est là pour vous aider à installer votre code sur d’autres systèmes, ainsi que gérer d’étendue.</span><span class="sxs-lookup"><span data-stu-id="cf40c-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="cf40c-106">Vous pouvez également utiliser un fichier de manifeste de module, qui décrire les installations encore plus complexes et des solutions.</span><span class="sxs-lookup"><span data-stu-id="cf40c-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="cf40c-107">Écriture d’un Module de Script PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf40c-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="cf40c-108">Vous créez un module de script en enregistrant un script PowerShell valide dans un fichier .psm1, puis enregistrez ce fichier dans un répertoire situé où PowerShell peut le trouver.</span><span class="sxs-lookup"><span data-stu-id="cf40c-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="cf40c-109">Dans ce dossier, que vous pouvez également placer les ressources que vous avez besoin pour exécuter votre script, ainsi qu’un fichier manifest qui décrit à PowerShell le fonctionnement de votre module.</span><span class="sxs-lookup"><span data-stu-id="cf40c-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="cf40c-110">Pour créer un PowerShell Module de base</span><span class="sxs-lookup"><span data-stu-id="cf40c-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="cf40c-111">Prenez un script PowerShell existant et enregistrez le script avec l’extension .psm1.</span><span class="sxs-lookup"><span data-stu-id="cf40c-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="cf40c-112">L’enregistrement d’un script avec le .psm1 extension signifie que vous pouvez utiliser les applets de commande du module, tel que [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), dessus.</span><span class="sxs-lookup"><span data-stu-id="cf40c-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="cf40c-113">Ces applets de commande se trouvent principalement afin que vous pouvez facilement importer et exporter votre code sur des systèmes de l’autre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cf40c-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="cf40c-114">(L’autre solution serait pour charger votre code sur les autres systèmes, puis « dot sourcer » dans la mémoire active, ce qui n’est pas une solution évolutive en particulier). Pour plus d’informations, consultez le **Variables et des applets de commande Module** section [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Notez que, par défaut, toutes les fonctions dans votre script sont accessibles aux utilisateurs qui importer votre fichier .psm1, mais les propriétés ne sont pas.</span><span class="sxs-lookup"><span data-stu-id="cf40c-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script are accessible to users who import your .psm1 file, but properties are not.</span></span>

   <span data-ttu-id="cf40c-115">Un exemple de script PowerShell, intitulé `Show-Calendar`, est disponible à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="cf40c-115">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this topic.</span></span>

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

2. <span data-ttu-id="cf40c-116">Pour contrôler l’accès utilisateur à certaines fonctions ou des propriétés, appelez [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) à la fin de votre script.</span><span class="sxs-lookup"><span data-stu-id="cf40c-116">To control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="cf40c-117">L’exemple de code en bas de la page a une seule fonction, ce qui est exposée par défaut.</span><span class="sxs-lookup"><span data-stu-id="cf40c-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="cf40c-118">Toutefois, il est recommandé que vous appelez explicitement les fonctions que vous souhaitez exposer, comme décrit dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="cf40c-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="cf40c-119">Vous pouvez également limiter ce qui est importé à l’aide d’un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="cf40c-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="cf40c-120">Pour plus d’informations, consultez [importation d’un PowerShell Module](./importing-a-powershell-module.md) et [comment écrire un manifeste de Module PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="cf40c-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="cf40c-121">Si vous avez des modules devant votre propre module de chargement, vous pouvez les utiliser avec un appel à `Import-Module`, en haut de votre propre module.</span><span class="sxs-lookup"><span data-stu-id="cf40c-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="cf40c-122">`Import-Module` est une applet de commande importe un module ciblé sur un système.</span><span class="sxs-lookup"><span data-stu-id="cf40c-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="cf40c-123">Par conséquent, il est également utilisé à un moment ultérieur dans la procédure pour installer votre propre module également.</span><span class="sxs-lookup"><span data-stu-id="cf40c-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="cf40c-124">L’exemple de code en bas de cette page n’utilise pas les modules d’importation.</span><span class="sxs-lookup"><span data-stu-id="cf40c-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="cf40c-125">Si c’était le cas, toutefois, elles sont indiquées en haut du fichier, comme décrit dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="cf40c-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="cf40c-126">Pour décrire votre module sur le système d’aide de PowerShell, vous pouvez utiliser des commentaires de l’aide standard dans le fichier ou créer un fichier d’aide supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="cf40c-126">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="cf40c-127">L’exemple de code en bas de cette rubrique inclut les informations d’aide dans les commentaires.</span><span class="sxs-lookup"><span data-stu-id="cf40c-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="cf40c-128">Vous pouvez également écrire des fichiers XML développés qui contiennent le contenu d’aide supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="cf40c-128">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="cf40c-129">Pour plus d’informations, consultez [l’aider à écrire pour Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="cf40c-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="cf40c-130">Si vous avez des modules complémentaires, des fichiers XML ou tout autre contenu que vous souhaitez empaqueter avec votre module, vous pouvez le faire avec un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="cf40c-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="cf40c-131">Un manifeste de module est un fichier qui contient les noms des autres modules, dispositions de répertoire, les numéros de contrôle de version, créer des données et autres éléments d’information.</span><span class="sxs-lookup"><span data-stu-id="cf40c-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="cf40c-132">PowerShell utilise le fichier de manifeste de module pour organiser et déployer votre solution.</span><span class="sxs-lookup"><span data-stu-id="cf40c-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="cf40c-133">Toutefois, en raison de la nature relativement simple de cet exemple, un fichier manifeste n’était pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="cf40c-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="cf40c-134">Pour plus d’informations, consultez [manifestes de Module](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="cf40c-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="cf40c-135">Pour installer et exécuter votre module, enregistrer le module dans l’un des chemins PowerShell appropriées et effectuer un appel à `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="cf40c-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="cf40c-136">Les chemins d’accès où vous pouvez installer votre module sont situés dans le `$env:PSModulePath` (variable globale).</span><span class="sxs-lookup"><span data-stu-id="cf40c-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="cf40c-137">Par exemple, un chemin d’accès commun pour enregistrer un module sur un système serait `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="cf40c-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="cf40c-138">Veillez à créer un dossier pour votre module d’exister, même si elle est uniquement un fichier .psm1 unique.</span><span class="sxs-lookup"><span data-stu-id="cf40c-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="cf40c-139">Si vous n’avez pas enregistré votre module à un de ces chemins d’accès, vous seriez obligé de passer à l’emplacement de votre module dans l’appel à `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="cf40c-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="cf40c-140">(Dans le cas contraire, PowerShell pas serait en mesure de le retrouver.) À partir de PowerShell 3.0, si vous avez placé votre module dans un des chemins de module PowerShell, vous n’avez pas besoin pour l’importer explicitement.</span><span class="sxs-lookup"><span data-stu-id="cf40c-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module in one of the PowerShell module paths, you do not need to explicitly import it.</span></span> <span data-ttu-id="cf40c-141">Vous module est chargé automatiquement lorsqu’un utilisateur appelle votre fonction.</span><span class="sxs-lookup"><span data-stu-id="cf40c-141">You module is automatically loaded when a user calls your function.</span></span>
   <span data-ttu-id="cf40c-142">Pour plus d’informations sur le chemin d’accès du module, consultez [importation d’un PowerShell Module](./importing-a-powershell-module.md) et [Variable d’environnement PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="cf40c-142">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="cf40c-143">Pour supprimer un module de service actif, effectuez un appel à [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="cf40c-143">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   <span data-ttu-id="cf40c-144">Notez que [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) supprime votre module de la mémoire active - il ne supprime pas réellement il d’où vous avez enregistré les fichiers de module.</span><span class="sxs-lookup"><span data-stu-id="cf40c-144">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="cf40c-145">Exemple de code Show-Calendar</span><span class="sxs-lookup"><span data-stu-id="cf40c-145">Show-Calendar code example</span></span>

<span data-ttu-id="cf40c-146">L’exemple suivant est un module de script simple qui contient une fonction unique nommée `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="cf40c-146">The following example is a simple script module that contains a single function named `Show-Calendar`.</span></span>
<span data-ttu-id="cf40c-147">Cette fonction affiche une représentation visuelle d’un calendrier.</span><span class="sxs-lookup"><span data-stu-id="cf40c-147">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="cf40c-148">En outre, l’exemple contient les chaînes d’aide de PowerShell pour le résumé, la description, les valeurs de paramètre et exemple.</span><span class="sxs-lookup"><span data-stu-id="cf40c-148">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="cf40c-149">Notez que la dernière ligne de code garantit que le `Show-Calendar` fonction est exportée en tant que module membre quand le module est importé.</span><span class="sxs-lookup"><span data-stu-id="cf40c-149">Note that the last line of code ensures that the `Show-Calendar` function is exported as a module member when the module is imported.</span></span>

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
