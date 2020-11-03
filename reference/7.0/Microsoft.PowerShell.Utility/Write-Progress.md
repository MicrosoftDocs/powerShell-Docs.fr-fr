---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 35b417b35d67e5cbe0df8719ba790135645d64e1
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208493"
---
# <span data-ttu-id="abf4f-103">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="abf4f-103">Write-Progress</span></span>

## <span data-ttu-id="abf4f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="abf4f-104">SYNOPSIS</span></span>
<span data-ttu-id="abf4f-105">Affiche une barre de progression dans une fenêtre de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abf4f-105">Displays a progress bar within a PowerShell command window.</span></span>

## <span data-ttu-id="abf4f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="abf4f-106">SYNTAX</span></span>

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="abf4f-107">Description</span><span class="sxs-lookup"><span data-stu-id="abf4f-107">DESCRIPTION</span></span>

<span data-ttu-id="abf4f-108">L' `Write-Progress` applet de commande affiche une barre de progression dans une fenêtre de commande PowerShell qui représente l’état d’une commande ou d’un script en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="abf4f-108">The `Write-Progress` cmdlet displays a progress bar in a PowerShell command window that depicts the status of a running command or script.</span></span> <span data-ttu-id="abf4f-109">Vous pouvez sélectionner les indicateurs reflétés par la barre et le texte qui s'affiche au-dessus et en dessous de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="abf4f-109">You can select the indicators that the bar reflects and the text that appears above and below the progress bar.</span></span>

## <span data-ttu-id="abf4f-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="abf4f-110">EXAMPLES</span></span>

### <span data-ttu-id="abf4f-111">Exemple 1 : afficher la progression d’une boucle for</span><span class="sxs-lookup"><span data-stu-id="abf4f-111">Example 1: Display the progress of a For loop</span></span>

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

<span data-ttu-id="abf4f-112">Cette commande affiche la progression d'une boucle For qui compte de 1 à 100.</span><span class="sxs-lookup"><span data-stu-id="abf4f-112">This command displays the progress of a For loop that counts from 1 to 100.</span></span>

<span data-ttu-id="abf4f-113">L' `Write-Progress` applet de commande comprend un en-tête de barre `Activity` d’État, une ligne d’État et la variable `$i` (le compteur dans la boucle for), qui indique l’exhaustivité relatif de la tâche.</span><span class="sxs-lookup"><span data-stu-id="abf4f-113">The `Write-Progress` cmdlet includes a status bar heading `Activity`, a status line, and the variable `$i` (the counter in the For loop), which indicates the relative completeness of the task.</span></span>

### <span data-ttu-id="abf4f-114">Exemple 2 : afficher la progression des boucles for imbriquées</span><span class="sxs-lookup"><span data-stu-id="abf4f-114">Example 2: Display the progress of nested For loops</span></span>

```powershell
for($I = 1; $I -lt 101; $I++ )
{
    Write-Progress -Activity Updating -Status 'Progress->' -PercentComplete $I -CurrentOperation OuterLoop
    for($j = 1; $j -lt 101; $j++ )
    {
        Write-Progress -Id 1 -Activity Updating -Status 'Progress' -PercentComplete $j -CurrentOperation InnerLoop
    }
}
```

```Output
Updating
Progress ->
 [ooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo]
OuterLoop
Updating
Progress
 [oooooooooooooooooo                                                   ]
InnerLoop
```

<span data-ttu-id="abf4f-115">Cet exemple affiche la progression de deux boucles For imbriquées, chacune d'elles étant représentée par une barre de progression.</span><span class="sxs-lookup"><span data-stu-id="abf4f-115">This example displays the progress of two nested For loops, each of which is represented by a progress bar.</span></span>

<span data-ttu-id="abf4f-116">La `Write-Progress` commande de la deuxième barre de progression comprend le paramètre **ID** qui la distingue de la première barre de progression.</span><span class="sxs-lookup"><span data-stu-id="abf4f-116">The `Write-Progress` command for the second progress bar includes the **Id** parameter that distinguishes it from the first progress bar.</span></span>

<span data-ttu-id="abf4f-117">Sans le paramètre **ID** , les barres de progression sont superposées les unes aux autres au lieu d’être affichées l’une en dessous de l’autre.</span><span class="sxs-lookup"><span data-stu-id="abf4f-117">Without the **Id** parameter, the progress bars would be superimposed on each other instead of being displayed one below the other.</span></span>

### <span data-ttu-id="abf4f-118">Exemple 3 : afficher la progression lors de la recherche d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="abf4f-118">Example 3: Display the progress while searching for a string</span></span>

```powershell
# Use Get-EventLog to get the events in the System log and store them in the $Events variable.
$Events = Get-EventLog -LogName system
# Pipe the events to the ForEach-Object cmdlet.
$Events | ForEach-Object -Begin {
    # In the Begin block, use Clear-Host to clear the screen.
    Clear-Host
    # Set the $i counter variable to zero.
    $i = 0
    # Set the $out variable to a empty string.
    $out = ""
} -Process {
    # In the Process script block search the message property of each incoming object for "bios".
    if($_.message -like "*bios*")
    {
        # Append the matching message to the out variable.
        $out=$out + $_.Message
    }
    # Increment the $i counter variable which is used to create the progress bar.
    $i = $i+1
    # Use Write-Progress to output a progress bar.
    # The Activity and Status parameters create the first and second lines of the progress bar heading, respectively.
    Write-Progress -Activity "Searching Events" -Status "Progress:" -PercentComplete ($i/$Events.count*100)
} -End {
    # Display the matching messages using the out variable.
    $out
}
```

<span data-ttu-id="abf4f-119">Cette commande affiche la progression d'une commande qui recherche la chaîne « bios » dans le journal des événements système.</span><span class="sxs-lookup"><span data-stu-id="abf4f-119">This command displays the progress of a command to find the string "bios" in the System event log.</span></span>

<span data-ttu-id="abf4f-120">La valeur du paramètre **PercentComplete** est calculée en divisant le nombre d’événements qui ont été traités `$I` par le nombre total d’événements récupérés `$Events.count` , puis en multipliant ce résultat par 100.</span><span class="sxs-lookup"><span data-stu-id="abf4f-120">The **PercentComplete** parameter value is calculated by dividing the number of events that have been processed `$I` by the total number of events retrieved `$Events.count` and then multiplying that result by 100.</span></span>

### <span data-ttu-id="abf4f-121">Exemple 4 : afficher la progression de chaque niveau d’un processus imbriqué</span><span class="sxs-lookup"><span data-stu-id="abf4f-121">Example 4: Display progress for each level of a nested process</span></span>

```powershell
foreach ( $i in 1..10 ) {
  Write-Progress -Id 0 "Step $i"
  foreach ( $j in 1..10 ) {
    Write-Progress -Id 1 -ParentId 0 "Step $i - Substep $j"
    foreach ( $k in 1..10 ) {
      Write-Progress -Id 2  -ParentId 1 "Step $i - Substep $j - iteration $k"; start-sleep -m 150
    }
  }
}
```

```Output
Step 1
     Processing
    Step 1 - Substep 2
         Processing
        Step 1 - Substep 2 - Iteration 3
             Processing
```

<span data-ttu-id="abf4f-122">Dans cet exemple, vous pouvez utiliser le paramètre **ParentId** pour obtenir une sortie en retrait pour afficher les relations parent/enfant dans la progression de chaque étape.</span><span class="sxs-lookup"><span data-stu-id="abf4f-122">In this example you can use the **ParentId** parameter to have indented output to show parent/child relationships in the progress of each step.</span></span>

## <span data-ttu-id="abf4f-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="abf4f-123">PARAMETERS</span></span>

### <span data-ttu-id="abf4f-124">-Activité</span><span class="sxs-lookup"><span data-stu-id="abf4f-124">-Activity</span></span>

<span data-ttu-id="abf4f-125">Spécifie la première ligne de texte dans le titre au-dessus de la barre d'état.</span><span class="sxs-lookup"><span data-stu-id="abf4f-125">Specifies the first line of text in the heading above the status bar.</span></span>
<span data-ttu-id="abf4f-126">Ce texte décrit l'activité dont la progression est montrée.</span><span class="sxs-lookup"><span data-stu-id="abf4f-126">This text describes the activity whose progress is being reported.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abf4f-127">-Terminé</span><span class="sxs-lookup"><span data-stu-id="abf4f-127">-Completed</span></span>

<span data-ttu-id="abf4f-128">Indique si la barre de progression est visible.</span><span class="sxs-lookup"><span data-stu-id="abf4f-128">Indicates whether the progress bar is visible.</span></span>
<span data-ttu-id="abf4f-129">Si ce paramètre est omis, `Write-Progress` affiche les informations de progression.</span><span class="sxs-lookup"><span data-stu-id="abf4f-129">If this parameter is omitted, `Write-Progress` displays progress information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abf4f-130">-CurrentOperation</span><span class="sxs-lookup"><span data-stu-id="abf4f-130">-CurrentOperation</span></span>

<span data-ttu-id="abf4f-131">Spécifie la ligne de texte en dessous de la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="abf4f-131">Specifies the line of text below the progress bar.</span></span>
<span data-ttu-id="abf4f-132">Ce texte décrit l'opération qui est actuellement en cours.</span><span class="sxs-lookup"><span data-stu-id="abf4f-132">This text describes the operation that is currently taking place.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abf4f-133">-Id</span><span class="sxs-lookup"><span data-stu-id="abf4f-133">-Id</span></span>

<span data-ttu-id="abf4f-134">Spécifie un ID qui distingue chaque barre de progression des autres.</span><span class="sxs-lookup"><span data-stu-id="abf4f-134">Specifies an ID that distinguishes each progress bar from the others.</span></span> <span data-ttu-id="abf4f-135">Utilisez ce paramètre quand vous créez plusieurs barres de progression dans une même commande.</span><span class="sxs-lookup"><span data-stu-id="abf4f-135">Use this parameter when you are creating more than one progress bar in a single command.</span></span> <span data-ttu-id="abf4f-136">Si les barres de progression n'ont pas des ID distincts, elles sont superposées, au lieu de s'afficher dans une série.</span><span class="sxs-lookup"><span data-stu-id="abf4f-136">If the progress bars do not have different IDs, they are superimposed instead of being displayed in a series.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abf4f-137">-ParentId</span><span class="sxs-lookup"><span data-stu-id="abf4f-137">-ParentId</span></span>

<span data-ttu-id="abf4f-138">Spécifie l’activité parente de l’activité en cours.</span><span class="sxs-lookup"><span data-stu-id="abf4f-138">Specifies the parent activity of the current activity.</span></span>
<span data-ttu-id="abf4f-139">Utilisez la valeur -1 si l'activité en cours n'a pas d'activité parente.</span><span class="sxs-lookup"><span data-stu-id="abf4f-139">Use the value -1 if the current activity has no parent activity.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abf4f-140">-PercentComplete</span><span class="sxs-lookup"><span data-stu-id="abf4f-140">-PercentComplete</span></span>

<span data-ttu-id="abf4f-141">Spécifie le pourcentage de l'activité qui est terminé.</span><span class="sxs-lookup"><span data-stu-id="abf4f-141">Specifies the percentage of the activity that is completed.</span></span>
<span data-ttu-id="abf4f-142">Utilisez la valeur -1 si le pourcentage terminé est inconnu ou non applicable.</span><span class="sxs-lookup"><span data-stu-id="abf4f-142">Use the value -1 if the percentage complete is unknown or not applicable.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abf4f-143">-SecondsRemaining</span><span class="sxs-lookup"><span data-stu-id="abf4f-143">-SecondsRemaining</span></span>

<span data-ttu-id="abf4f-144">Spécifie le nombre de secondes prévues restant avant la fin de l'activité.</span><span class="sxs-lookup"><span data-stu-id="abf4f-144">Specifies the projected number of seconds remaining until the activity is completed.</span></span>
<span data-ttu-id="abf4f-145">Utilisez la valeur -1 si le nombre de secondes restantes est inconnu ou non applicable.</span><span class="sxs-lookup"><span data-stu-id="abf4f-145">Use the value -1 if the number of seconds remaining is unknown or not applicable.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abf4f-146">-SourceId</span><span class="sxs-lookup"><span data-stu-id="abf4f-146">-SourceId</span></span>

<span data-ttu-id="abf4f-147">Spécifie la source de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="abf4f-147">Specifies the source of the record.</span></span> <span data-ttu-id="abf4f-148">Vous pouvez l’utiliser à la place de **ID** , mais ne peut pas être utilisé avec d’autres paramètres tels que **ParentId** .</span><span class="sxs-lookup"><span data-stu-id="abf4f-148">You can use this in place of **Id** but cannot be used with other parameters like **ParentId** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abf4f-149">-État</span><span class="sxs-lookup"><span data-stu-id="abf4f-149">-Status</span></span>

<span data-ttu-id="abf4f-150">Spécifie la deuxième ligne de texte dans le titre au-dessus de la barre d'état.</span><span class="sxs-lookup"><span data-stu-id="abf4f-150">Specifies the second line of text in the heading above the status bar.</span></span>
<span data-ttu-id="abf4f-151">Ce texte décrit l'état actuel de l'activité.</span><span class="sxs-lookup"><span data-stu-id="abf4f-151">This text describes current state of the activity.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abf4f-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="abf4f-152">CommonParameters</span></span>

<span data-ttu-id="abf4f-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="abf4f-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="abf4f-154">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="abf4f-154">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="abf4f-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="abf4f-155">INPUTS</span></span>

### <span data-ttu-id="abf4f-156">Aucun</span><span class="sxs-lookup"><span data-stu-id="abf4f-156">None</span></span>

<span data-ttu-id="abf4f-157">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="abf4f-157">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="abf4f-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="abf4f-158">OUTPUTS</span></span>

### <span data-ttu-id="abf4f-159">Aucun</span><span class="sxs-lookup"><span data-stu-id="abf4f-159">None</span></span>

<span data-ttu-id="abf4f-160">`Write-Progress` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="abf4f-160">`Write-Progress` does not generate any output.</span></span>

## <span data-ttu-id="abf4f-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="abf4f-161">NOTES</span></span>

<span data-ttu-id="abf4f-162">Si la barre de progression n’apparaît pas, vérifiez la valeur de la `$ProgressPreference` variable.</span><span class="sxs-lookup"><span data-stu-id="abf4f-162">If the progress bar does not appear, check the value of the `$ProgressPreference` variable.</span></span> <span data-ttu-id="abf4f-163">Si la valeur est définie à SilentlyContinue, la barre de progression n'est pas affichée.</span><span class="sxs-lookup"><span data-stu-id="abf4f-163">If the value is set to SilentlyContinue, the progress bar is not displayed.</span></span> <span data-ttu-id="abf4f-164">Pour plus d’informations sur les préférences PowerShell, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="abf4f-164">For more information about PowerShell preferences, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="abf4f-165">Les paramètres de l’applet de commande correspondent aux propriétés de la classe **System. Management. Automation. ProgressRecord** .</span><span class="sxs-lookup"><span data-stu-id="abf4f-165">The parameters of the cmdlet correspond to the properties of the **System.Management.Automation.ProgressRecord** class.</span></span> <span data-ttu-id="abf4f-166">Pour plus d’informations, consultez [ProgressRecord, classe](/dotnet/api/system.management.automation.progressrecord).</span><span class="sxs-lookup"><span data-stu-id="abf4f-166">For more information, see [ProgressRecord Class](/dotnet/api/system.management.automation.progressrecord).</span></span>

## <span data-ttu-id="abf4f-167">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="abf4f-167">RELATED LINKS</span></span>

[<span data-ttu-id="abf4f-168">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="abf4f-168">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="abf4f-169">Écriture-erreur</span><span class="sxs-lookup"><span data-stu-id="abf4f-169">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="abf4f-170">Write-Host</span><span class="sxs-lookup"><span data-stu-id="abf4f-170">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="abf4f-171">Write-Output</span><span class="sxs-lookup"><span data-stu-id="abf4f-171">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="abf4f-172">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="abf4f-172">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="abf4f-173">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="abf4f-173">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="abf4f-174">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="abf4f-174">Write-Warning</span></span>](Write-Warning.md)
