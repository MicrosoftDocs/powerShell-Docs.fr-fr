---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 030f96cc99e42e19e78e1be2c4f913889d0567b6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203266"
---
# Get-PSBreakpoint

## SYNOPSIS
Obtient les points d'arrêt définis dans la session active.

## SYNTAX

### Script (par défaut)

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### Variable

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### Commande

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### Type

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### Id

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## Description

L’applet de commande **obtenir-PSBreakpoint** obtient les points d’arrêt définis dans la session active.
Vous pouvez utiliser les paramètres d'applet de commande pour obtenir des points d'arrêt spécifiques.

Un point d'arrêt est un point dans une commande ou un script auquel l'exécution s'arrête temporairement afin que vous puissiez examiner les instructions.
L’applet de commande **PSBreakpoint** est l’une des nombreuses cmdlets conçues pour déboguer les commandes et les scripts Windows PowerShell. Pour plus d'informations sur le débogueur Windows PowerShell, consultez about_Debuggers.

## EXEMPLES

### Exemple 1 : obtenir tous les points d’arrêt pour tous les scripts et les fonctions

```
PS C:\> Get-PSBreakpoint
```

Cette commande obtient tous les points d'arrêt définis sur tous les scripts et fonctions de la session active.

### Exemple 2 : récupérer des points d’arrêt par ID

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

Cette commande obtient le point d'arrêt associé à l'ID de point d'arrêt 2.

### Exemple 3 : diriger un ID vers Get-PSBreakpoint

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

Ces commandes montrent comment obtenir un point d’arrêt en canalisant un ID de point d’arrêt vers **PSBreakpoint** .

La première commande utilise l'applet de commande Set-PSBreakpoint pour créer un point d'arrêt sur la fonction Increment dans le script Sample.ps1. Elle enregistre l’objet de point d’arrêt dans la variable $B.

La deuxième commande utilise l’opérateur point (.) pour récupérer la propriété ID de l’objet de point d’arrêt dans la variable $B. Elle utilise un opérateur de pipeline (|) pour envoyer l’ID à l’applet de commande **PSBreakpoint** .

Par conséquent, la fonction **PSBreakpoint** obtient le point d’arrêt avec l’ID spécifié.

### Exemple 4 : récupérer des points d’arrêt dans les fichiers de script spécifiés

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

Cette commande obtient tous les points d'arrêt des fichiers Sample.ps1 et SupportScript.ps1.

Cette commande n’obtient pas d’autres points d’arrêt qui peuvent être définis dans d’autres scripts ou sur des fonctions dans la session.

### Exemple 5 : récupérer des points d’arrêt dans les applets de commande spécifiées

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

Cette commande obtient tous les points d'arrêt de commande définis sur les commandes Read-Host ou Write-Host dans le fichier Sample.ps1.

### Exemple 6 : obtenir des points d’arrêt de commande dans un fichier spécifié

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

Cette commande obtient tous les points d'arrêt de commande du fichier Sample.ps1.

### Exemple 7 : récupérer des points d’arrêt par variable

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

Cette commande obtient les points d’arrêt définis sur les variables $Index et $Swap dans la session active.

### Exemple 8 : obtenir tous les points d’arrêt de ligne et de variable dans un fichier

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

Cette commande obtient tous points d'arrêt de ligne et de variable du script Sample.ps1.

## PARAMETERS

### -Command

Spécifie un tableau de points d’arrêt de commande définis sur les noms de commande spécifiés.
Entrez les noms de commande, par exemple, le nom d'une applet de commande ou d'une fonction.

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Spécifie les ID de point d’arrêt que cette applet de commande obtient.
Entrez les ID dans une liste séparée par des virgules.
Vous pouvez également diriger les ID de point d’arrêt vers **PSBreakpoint** .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Script

Spécifie un tableau de scripts qui contiennent les points d’arrêt.
Entrez le chemin d’accès (facultatif) et les noms d’un ou de plusieurs fichiers de script.
Si vous omettez le chemin d'accès, l'emplacement par défaut est le répertoire actif.

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Type

Spécifie un tableau de types de points d’arrêt que cette applet de commande obtient.
Entrez un ou plusieurs types.
Les valeurs valides pour ce paramètre sont :

- Ligne
- Commande
- Variable

Vous pouvez également diriger les types de point d’arrêt vers **PSBreakpoint** .

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Variable

Spécifie un tableau de points d’arrêt de variable définis sur les noms de variable spécifiés.
Entrez les noms de variable sans le signe dollar.

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Int32, Microsoft. PowerShell. Commands. BreakpointType

Vous pouvez diriger les ID de point d’arrêt et les types de point d’arrêt vers **PSBreakpoint** .

## SORTIES

### System. Management. Automation. Breakpoint

La méthode **PSBreakpoint retourne des** objets qui représentent les points d’arrêt de la session.

## REMARQUES

* Vous pouvez utiliser **PSBreakpoint** ou son alias, « GBP ».

## LIENS CONNEXES

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
