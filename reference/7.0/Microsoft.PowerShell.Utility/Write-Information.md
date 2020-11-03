---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: 9fe1e66cbd8ae55e0a26d9702998564dcd7f9450
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208497"
---
# Write-Information

## SYNOPSIS

Spécifie la manière dont PowerShell gère les données de flux d’informations pour une commande.

## SYNTAX

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## Description

L' `Write-Information` applet de commande spécifie la manière dont PowerShell gère les données de flux d’informations pour une commande.

Windows PowerShell 5,0 introduit un nouveau flux d’informations structurées. Vous pouvez utiliser ce flux pour transmettre des données structurées entre un script et ses appelants ou l’application hôte.
`Write-Information` vous permet d’ajouter un message d’information au flux et de spécifier la manière dont PowerShell gère les données de flux d’informations pour une commande. Les flux d’informations fonctionnent également pour les `PowerShell.Streams` tâches, les travaux et les tâches planifiées.

> [!NOTE]
> Le flux d’informations ne suit pas la Convention standard de préfixe de ses messages avec « [nom du flux] : ». Cela était prévu à des fins de brièveté et de préversion visuelle.

La `$InformationPreference` valeur de la variable de préférence détermine si le message que vous fournissez à `Write-Information` est affiché au point attendu dans l’opération d’un script. Étant donné que la valeur par défaut de cette variable est `SilentlyContinue` , par défaut, les messages d’information ne sont pas affichés. Si vous ne souhaitez pas modifier la valeur de `$InformationPreference` , vous pouvez remplacer sa valeur en ajoutant le `InformationAction` paramètre commun à votre commande. Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) et [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

> [!NOTE]
> À compter de Windows PowerShell 5,0, `Write-Host` est un wrapper de `Write-Information` ce qui vous permet d’utiliser `Write-Host` pour émettre une sortie vers le flux d’informations. Cela permet la **capture** ou la **suppression** des données écrites à l’aide de `Write-Host` tout en préservant la compatibilité descendante. Pour plus d’informations [, consultez Write-Host](Write-Host.md)

`Write-Information` est également une activité de flux de travail prise en charge dans PowerShell 5. x.

## EXEMPLES

### Exemple 1 : écrire des informations pour obtenir des résultats

Dans cet exemple, vous affichez un message d’information « obtention de vos fonctionnalités ! » après avoir exécuté la `Get-WindowsFeature` commande pour rechercher toutes les fonctionnalités dont la valeur de nom commence par « p ».
Étant donné que la `$InformationPreference` variable est toujours définie sur sa valeur par défaut, `SilentlyContinue` , vous ajoutez le `InformationAction` paramètre pour remplacer la `$InformationPreference` valeur et afficher le message. La `InformationAction` valeur est continuer, ce qui signifie que votre message s’affiche, mais le script ou la commande se poursuit, s’il n’est pas encore terminé.

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### Exemple 2 : écrire des informations et les baliser

Dans cet exemple, vous utilisez `Write-Information` pour informer les utilisateurs qu’ils doivent exécuter une autre commande une fois qu’ils ont terminé d’exécuter la commande actuelle. L’exemple ajoute les instructions de balise au message d’information. Après l’exécution de cette commande, si vous recherchez des messages marqués dans le flux d’informations, le message spécifié ici figure parmi les résultats.

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### Exemple 3 : écrire des informations dans un fichier

Dans cet exemple, vous redirigez le flux d’informations de la fonction vers un à `Info.txt` l’aide du code `6>` . Lorsque vous ouvrez le `Info.txt` fichier, le texte « ici » s’affiche.

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

### Exemple 4 : passer un objet pour écrire des informations

Dans cet exemple, vous pouvez utiliser `Write-Information` pour écrire les 10 premiers processus d’utilisation du processeur à partir de la `Get-Process` sortie d’objet qui a franchi plusieurs pipelines.

```powershell
Get-Process | Sort-Object CPU -Descending |
    Select-Object Id, ProcessName, CPU -First 10 |
        Write-Information -InformationAction Continue
```

```Output
@{Id=12692; ProcessName=chrome; CPU=39431.296875}
@{Id=21292; ProcessName=OUTLOOK; CPU=23991.875}
@{Id=10548; ProcessName=CefSharp.BrowserSubprocess; CPU=20546.203125}
@{Id=312848; ProcessName=Taskmgr; CPU=13173.1875}
@{Id=10848; ProcessName=SnapClient; CPU=7014.265625}
@{Id=9760; ProcessName=Receiver; CPU=6792.359375}
@{Id=12040; ProcessName=Teams; CPU=5605.578125}
@{Id=498388; ProcessName=chrome; CPU=3062.453125}
@{Id=6900; ProcessName=chrome; CPU=2546.9375}
@{Id=9044; ProcessName=explorer; CPU=2358.765625}
```

## PARAMETERS

### -MessageData

Spécifie un message d’information que vous souhaitez afficher aux utilisateurs lorsqu’ils exécutent un script ou une commande. Pour de meilleurs résultats, mettez le message d’information entre guillemets.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Tags

Spécifie une chaîne simple que vous pouvez utiliser pour trier et filtrer les messages que vous avez ajoutés au flux d’informations avec `Write-Information` . Ce paramètre fonctionne de la même façon que le paramètre **Tags** dans `New-ModuleManifest` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.Object

`Write-Information` accepte les objets redirigés à passer au flux d’informations.

## SORTIES

### System. Management. Automation. InformationRecord

## REMARQUES

## LIENS CONNEXES

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)

[Write-Output](Write-Output.md)
