---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 9e7aa9efce77e4c4c917658aeb2ecaabcd67e1e6
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208533"
---
# Write-Progress

## SYNOPSIS
Affiche une barre de progression dans une fenêtre de commande PowerShell.

## SYNTAX

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## Description

L' `Write-Progress` applet de commande affiche une barre de progression dans une fenêtre de commande PowerShell qui représente l’état d’une commande ou d’un script en cours d’exécution. Vous pouvez sélectionner les indicateurs reflétés par la barre et le texte qui s'affiche au-dessus et en dessous de celle-ci.

## EXEMPLES

### Exemple 1 : afficher la progression d’une boucle for

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

Cette commande affiche la progression d'une boucle For qui compte de 1 à 100.

L' `Write-Progress` applet de commande comprend un en-tête de barre `Activity` d’État, une ligne d’État et la variable `$i` (le compteur dans la boucle for), qui indique l’exhaustivité relatif de la tâche.

### Exemple 2 : afficher la progression des boucles for imbriquées

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

Cet exemple affiche la progression de deux boucles For imbriquées, chacune d'elles étant représentée par une barre de progression.

La `Write-Progress` commande de la deuxième barre de progression comprend le paramètre **ID** qui la distingue de la première barre de progression.

Sans le paramètre **ID** , les barres de progression sont superposées les unes aux autres au lieu d’être affichées l’une en dessous de l’autre.

### Exemple 3 : afficher la progression lors de la recherche d’une chaîne

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

Cette commande affiche la progression d'une commande qui recherche la chaîne « bios » dans le journal des événements système.

La valeur du paramètre **PercentComplete** est calculée en divisant le nombre d’événements qui ont été traités `$I` par le nombre total d’événements récupérés `$Events.count` , puis en multipliant ce résultat par 100.

### Exemple 4 : afficher la progression de chaque niveau d’un processus imbriqué

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

Dans cet exemple, vous pouvez utiliser le paramètre **ParentId** pour obtenir une sortie en retrait pour afficher les relations parent/enfant dans la progression de chaque étape.

## PARAMETERS

### -Activité

Spécifie la première ligne de texte dans le titre au-dessus de la barre d'état.
Ce texte décrit l'activité dont la progression est montrée.

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

### -Terminé

Indique si la barre de progression est visible.
Si ce paramètre est omis, `Write-Progress` affiche les informations de progression.

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

### -CurrentOperation

Spécifie la ligne de texte en dessous de la barre de progression.
Ce texte décrit l'opération qui est actuellement en cours.

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

### -Id

Spécifie un ID qui distingue chaque barre de progression des autres. Utilisez ce paramètre quand vous créez plusieurs barres de progression dans une même commande. Si les barres de progression n'ont pas des ID distincts, elles sont superposées, au lieu de s'afficher dans une série.

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

### -ParentId

Spécifie l’activité parente de l’activité en cours.
Utilisez la valeur -1 si l'activité en cours n'a pas d'activité parente.

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

### -PercentComplete

Spécifie le pourcentage de l'activité qui est terminé.
Utilisez la valeur -1 si le pourcentage terminé est inconnu ou non applicable.

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

### -SecondsRemaining

Spécifie le nombre de secondes prévues restant avant la fin de l'activité.
Utilisez la valeur -1 si le nombre de secondes restantes est inconnu ou non applicable.

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

### -SourceId

Spécifie la source de l’enregistrement. Vous pouvez l’utiliser à la place de **ID** , mais ne peut pas être utilisé avec d’autres paramètres tels que **ParentId** .

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

### -État

Spécifie la deuxième ligne de texte dans le titre au-dessus de la barre d'état.
Ce texte décrit l'état actuel de l'activité.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun

`Write-Progress` ne génère pas de sortie.

## REMARQUES

Si la barre de progression n’apparaît pas, vérifiez la valeur de la `$ProgressPreference` variable. Si la valeur est définie à SilentlyContinue, la barre de progression n'est pas affichée. Pour plus d’informations sur les préférences PowerShell, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

Les paramètres de l’applet de commande correspondent aux propriétés de la classe **System. Management. Automation. ProgressRecord** . Pour plus d’informations, consultez [ProgressRecord, classe](/dotnet/api/system.management.automation.progressrecord).

## LIENS CONNEXES

[Write-Debug](Write-Debug.md)

[Écriture-erreur](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
