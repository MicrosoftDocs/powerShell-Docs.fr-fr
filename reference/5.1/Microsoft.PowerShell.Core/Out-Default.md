---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: 5e434b6af523da25b0128f6d8e85a196eaf09ff2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202713"
---
# Out-Default

## SYNOPSIS
Envoie la sortie au formateur par défaut et à l'applet de commande de sortie par défaut.

## SYNTAX

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## Description

PowerShell ajoute automatiquement `Out-Default` à la fin de chaque pipeline. `Out-Default` décide comment mettre en forme et sortir le flux d’objet. Si le flux d’objet est un flux de chaînes, les dirige `Out-Default` directement vers `Out-Host` qui appellent les API appropriées fournies par l’hôte. Si le flux d’objet ne contient pas de chaînes, `Out-Default` inspecte l’objet pour déterminer ce qu’il doit faire.
Tout d’abord, il examine le type d’objet et détermine s’il existe une _vue_ inscrite pour ce type d’objet.

PowerShell définit le schéma XML et un mécanisme (l’applet de commande `Update-FormatData` ) où tout le monde peut inscrire des vues pour un type d’objet. Vous pouvez spécifier des vues **larges** , des **listes** , des **tables** ou des vues **personnalisées** pour tout type d’objet. Les vues spécifient les propriétés à afficher et leur mode d’affichage. Si une vue est inscrite, elle définit le formateur à utiliser. Ainsi, si la vue inscrite est une vue de **table** , `Out-Default` transmet les objets à `Format-Table | Out-Host` . `Format-Table` transforme les objets en un flux d’enregistrements de mise en forme (piloté par les données dans la définition de la vue) et `Out-Host` transforme les enregistrements de mise en forme en appels sur l’interface hôte.

## EXEMPLES

### Exemple 1

Bien que cette applet de commande ne soit pas destinée à être exécutée directement par l’utilisateur final, elle peut avoir la valeur.

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## PARAMETERS

### -InputObject

Accepte une entrée dans l'applet de commande.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Transcription

Détermine si la sortie doit être envoyée aux services de transcription de PowerShell.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Format-Custom](../Microsoft.PowerShell.Utility/Format-Custom.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Format-Wide](../Microsoft.PowerShell.Utility/Format-Wide.md)

[about_Format.ps1xml](About/about_Format.ps1xml.md)

[Fonctionnement de la mise en forme et du sortir de PowerShell](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)
