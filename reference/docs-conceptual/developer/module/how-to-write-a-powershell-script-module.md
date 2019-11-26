---
title: Comment écrire un module de script PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: 7742eedd67283535b9e5898adc74d0d48faf68fe
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416262"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="52000-102">Guide pratique pour écrire un module de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="52000-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="52000-103">Un module de script est un script PowerShell valide enregistré dans une extension de `.psm1`.</span><span class="sxs-lookup"><span data-stu-id="52000-103">A script module is any valid PowerShell script saved in a `.psm1` extension.</span></span> <span data-ttu-id="52000-104">Cette extension permet au moteur PowerShell d’utiliser des règles et des applets de commande de module sur votre fichier.</span><span class="sxs-lookup"><span data-stu-id="52000-104">This extension allows the PowerShell engine to use rules and module cmdlets on your file.</span></span> <span data-ttu-id="52000-105">La plupart de ces fonctionnalités sont là pour vous aider à installer votre code sur d’autres systèmes, ainsi qu’à gérer la portée.</span><span class="sxs-lookup"><span data-stu-id="52000-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="52000-106">Vous pouvez également utiliser un fichier manifeste de module, qui décrit des installations et des solutions plus complexes.</span><span class="sxs-lookup"><span data-stu-id="52000-106">You can also use a module manifest file, which describes more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="52000-107">Écriture d’un module de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="52000-107">Writing a PowerShell script module</span></span>

<span data-ttu-id="52000-108">Pour créer un module de script, enregistrez un script PowerShell valide dans un fichier de `.psm1`.</span><span class="sxs-lookup"><span data-stu-id="52000-108">To create a script module, save a valid PowerShell script to a `.psm1` file.</span></span> <span data-ttu-id="52000-109">Le script et le répertoire dans lequel il est stocké doivent utiliser le même nom.</span><span class="sxs-lookup"><span data-stu-id="52000-109">The script and the directory where it's stored must use the same name.</span></span> <span data-ttu-id="52000-110">Par exemple, un script nommé `MyPsScript.psm1` est stocké dans un répertoire nommé `MyPsScript`.</span><span class="sxs-lookup"><span data-stu-id="52000-110">For example, a script named `MyPsScript.psm1` is stored in a directory named `MyPsScript`.</span></span>

<span data-ttu-id="52000-111">Le répertoire du module doit se trouver dans un chemin d’accès spécifié dans `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="52000-111">The module's directory needs to be in a path specified in `$env:PSModulePath`.</span></span> <span data-ttu-id="52000-112">Le répertoire du module peut contenir toutes les ressources nécessaires pour exécuter le script, ainsi qu’un fichier manifeste de module qui décrit le fonctionnement de votre module dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52000-112">The module's directory can contain any resources that are needed to run the script, and a module manifest file that describes to PowerShell how your module works.</span></span>

## <a name="create-a-basic-powershell-module"></a><span data-ttu-id="52000-113">Créer un module PowerShell de base</span><span class="sxs-lookup"><span data-stu-id="52000-113">Create a basic PowerShell module</span></span>

<span data-ttu-id="52000-114">Les étapes suivantes décrivent comment créer un module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52000-114">The following steps describe how to create a PowerShell module.</span></span>

1. <span data-ttu-id="52000-115">Enregistrer un script PowerShell avec une extension de `.psm1`.</span><span class="sxs-lookup"><span data-stu-id="52000-115">Save a PowerShell script with a `.psm1` extension.</span></span> <span data-ttu-id="52000-116">Utilisez le même nom pour le script et le répertoire dans lequel le script est enregistré.</span><span class="sxs-lookup"><span data-stu-id="52000-116">Use the same name for the script and the directory where the script is saved.</span></span>

   <span data-ttu-id="52000-117">L’enregistrement d’un script avec l’extension `.psm1` signifie que vous pouvez utiliser les applets de commande du module, telles que [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="52000-117">Saving a script with the `.psm1` extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span> <span data-ttu-id="52000-118">Les applets de commande de module existent principalement pour vous permettre d’importer et d’exporter votre code sur les systèmes d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="52000-118">The module cmdlets exist primarily so that you can import and export your code onto other user's systems.</span></span> <span data-ttu-id="52000-119">L’autre solution consiste à charger votre code sur d’autres systèmes, puis à le mettre en mémoire dans la mémoire active, ce qui n’est pas une solution évolutive.</span><span class="sxs-lookup"><span data-stu-id="52000-119">The alternate solution would be to load your code on other systems and then dot-source it into active memory, which isn't a scalable solution.</span></span> <span data-ttu-id="52000-120">Pour plus d’informations, voir [fonctionnement d’un module Windows PowerShell](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span><span class="sxs-lookup"><span data-stu-id="52000-120">For more information, see [Understanding a Windows PowerShell Module](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span></span>
   <span data-ttu-id="52000-121">Par défaut, quand les utilisateurs importent votre fichier `.psm1`, toutes les fonctions de votre script sont accessibles, mais les variables ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="52000-121">By default, when users import your `.psm1` file, all functions in your script are accessible, but variables aren't.</span></span>

   <span data-ttu-id="52000-122">Un exemple de script PowerShell, autorisé `Show-Calendar`, est disponible à la fin de cet article.</span><span class="sxs-lookup"><span data-stu-id="52000-122">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this article.</span></span>

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

2. <span data-ttu-id="52000-123">Pour contrôler l’accès utilisateur à certaines fonctions ou variables, appelez [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) à la fin de votre script.</span><span class="sxs-lookup"><span data-stu-id="52000-123">To control user access to certain functions or variables, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="52000-124">L’exemple de code en bas de l’article n’a qu’une seule fonction, qui est exposée par défaut.</span><span class="sxs-lookup"><span data-stu-id="52000-124">The example code at the bottom of the article has only one function, which by default would be exposed.</span></span> <span data-ttu-id="52000-125">Toutefois, il est recommandé d’appeler explicitement les fonctions que vous souhaitez exposer, comme décrit dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="52000-125">However, it's recommended you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="52000-126">Vous pouvez limiter les éléments importés à l’aide d’un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="52000-126">You can restrict what's imported using a module manifest.</span></span> <span data-ttu-id="52000-127">Pour plus d’informations, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md) et [écriture d’un manifeste de module PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="52000-127">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="52000-128">Si vous avez des modules qui doivent être chargés par votre propre module, vous pouvez utiliser `Import-Module`, en haut de votre module.</span><span class="sxs-lookup"><span data-stu-id="52000-128">If you have modules that your own module needs to load, you can use `Import-Module`, at the top of your module.</span></span>

   <span data-ttu-id="52000-129">L’applet de commande `Import-Module` importe un module ciblé sur un système et peut être utilisé ultérieurement dans la procédure pour installer votre propre module.</span><span class="sxs-lookup"><span data-stu-id="52000-129">The `Import-Module` cmdlet imports a targeted module onto a system, and can be used at a later point in the procedure to install your own module.</span></span> <span data-ttu-id="52000-130">L’exemple de code en bas de cet article n’utilise pas de modules d’importation.</span><span class="sxs-lookup"><span data-stu-id="52000-130">The sample code at the bottom of this article doesn't use any import modules.</span></span> <span data-ttu-id="52000-131">Mais si c’est le cas, ils sont répertoriés en haut du fichier, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="52000-131">But if it did, they would be listed at the top of the file, as shown in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="52000-132">Pour décrire votre module au système d’aide PowerShell, vous pouvez soit utiliser des commentaires d’aide standard dans le fichier, soit créer un fichier d’aide supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="52000-132">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="52000-133">L’exemple de code en bas de cet article contient des informations d’aide dans les commentaires.</span><span class="sxs-lookup"><span data-stu-id="52000-133">The code sample at the bottom of this article includes the help information in the comments.</span></span> <span data-ttu-id="52000-134">Vous pouvez également écrire des fichiers XML développés qui contiennent du contenu d’aide supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="52000-134">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="52000-135">Pour plus d’informations, consultez [écriture de l’aide pour les modules Windows PowerShell](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="52000-135">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="52000-136">Si vous avez d’autres modules, fichiers XML ou tout autre contenu que vous souhaitez empaqueter avec votre module, vous pouvez utiliser un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="52000-136">If you have additional modules, XML files, or other content you want to package with your module, you can use a module manifest.</span></span>

   <span data-ttu-id="52000-137">Un manifeste de module est un fichier qui contient les noms d’autres modules, les dispositions de répertoire, les numéros de versioning, les données d’auteur et d’autres informations.</span><span class="sxs-lookup"><span data-stu-id="52000-137">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="52000-138">PowerShell utilise le fichier manifeste du module pour organiser et déployer votre solution.</span><span class="sxs-lookup"><span data-stu-id="52000-138">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="52000-139">Pour plus d’informations, consultez [Comment écrire un manifeste de module PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="52000-139">For more information, see [How to write a PowerShell module manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="52000-140">Pour installer et exécuter votre module, enregistrez le module dans l’un des chemins PowerShell appropriés et utilisez `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="52000-140">To install and run your module, save the module to one of the appropriate PowerShell paths, and use `Import-Module`.</span></span>

   <span data-ttu-id="52000-141">Les chemins d’accès où vous pouvez installer votre module se trouvent dans la variable globale `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="52000-141">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="52000-142">Par exemple, un chemin d’accès commun pour enregistrer un module sur un système est `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="52000-142">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="52000-143">Veillez à créer un répertoire pour votre module qui utilise le même nom que le module de script, même s’il s’agit d’un seul fichier de `.psm1`.</span><span class="sxs-lookup"><span data-stu-id="52000-143">Be sure to create a directory for your module that uses the same name as the script module, even if it's only a single `.psm1` file.</span></span> <span data-ttu-id="52000-144">Si vous n’avez pas enregistré votre module dans l’un de ces chemins d’accès, vous devez spécifier l’emplacement du module dans la commande `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="52000-144">If you didn't save your module to one of these paths, you would have to specify the module's location in the `Import-Module` command.</span></span> <span data-ttu-id="52000-145">Dans le cas contraire, PowerShell ne serait pas en mesure de trouver le module.</span><span class="sxs-lookup"><span data-stu-id="52000-145">Otherwise, PowerShell wouldn't be able to find the module.</span></span>

   <span data-ttu-id="52000-146">À compter de PowerShell 3,0, si vous avez placé votre module dans l’un des chemins d’accès des modules PowerShell, vous n’avez pas besoin de l’importer explicitement.</span><span class="sxs-lookup"><span data-stu-id="52000-146">Starting with PowerShell 3.0, if you've placed your module in one of the PowerShell module paths, you don't need to explicitly import it.</span></span> <span data-ttu-id="52000-147">Votre module est chargé automatiquement lorsqu’un utilisateur appelle votre fonction.</span><span class="sxs-lookup"><span data-stu-id="52000-147">Your module is automatically loaded when a user calls your function.</span></span> <span data-ttu-id="52000-148">Pour plus d’informations sur le chemin d’accès au module, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md) et [modification du chemin d’installation de PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="52000-148">For more information about the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="52000-149">Pour supprimer un module du service actif dans la session PowerShell active, utilisez [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="52000-149">To remove a module from active service in the current PowerShell session, use [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   > [!NOTE]
   > <span data-ttu-id="52000-150">`Remove-Module` supprime un module de la session PowerShell active, mais ne désinstalle pas le module ou ne supprime pas les fichiers du module.</span><span class="sxs-lookup"><span data-stu-id="52000-150">`Remove-Module` removes a module from the current PowerShell session, but doesn't uninstall the module or delete the module's files.</span></span>

## <a name="show-calendar-code-example"></a><span data-ttu-id="52000-151">Show-exemple de code de calendrier</span><span class="sxs-lookup"><span data-stu-id="52000-151">Show-Calendar code example</span></span>

<span data-ttu-id="52000-152">L’exemple suivant est un module de script qui contient une fonction unique nommée `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="52000-152">The following example is a script module that contains a single function named `Show-Calendar`.</span></span> <span data-ttu-id="52000-153">Cette fonction affiche une représentation visuelle d’un calendrier.</span><span class="sxs-lookup"><span data-stu-id="52000-153">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="52000-154">L’exemple contient les chaînes d’aide PowerShell pour le synopsis, la description, les valeurs de paramètre et le code.</span><span class="sxs-lookup"><span data-stu-id="52000-154">The sample contains the PowerShell Help strings for the synopsis, description, parameter values, and code.</span></span> <span data-ttu-id="52000-155">Quand le module est importé, la commande `Export-ModuleMember` garantit que la fonction `Show-Calendar` est exportée en tant que membre de module.</span><span class="sxs-lookup"><span data-stu-id="52000-155">When the module is imported, the `Export-ModuleMember` command ensures that the `Show-Calendar` function is exported as a module member.</span></span>

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
