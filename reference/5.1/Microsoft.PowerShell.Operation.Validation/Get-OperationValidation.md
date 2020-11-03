---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/get-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-OperationValidation
ms.openlocfilehash: 22ff12848fb7aefaa7f684ee5d8723cc723a5879
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203430"
---
# Get-OperationValidation

## SYNOPSIS
Obtient les tests de l’infrastructure de validation des opérations.

## SYNTAX

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## Description
L’applet de commande **obtenir-OperationValidation** obtient les tests de l’infrastructure de validation des opérations pour les modules installés.

Les modules qui incluent un dossier Diagnostics sont inspectés pour rechercher les tests pester dans le sous-dossier simple ou complet, ou les deux.

## EXEMPLES

### Exemple 1 : récupérer les tests de validation de l’opération

```
PS C:\> Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

Cette commande obtient les tests de validation à partir du module nommé AddNumbers dans le dossier C:\temp\modules.

## PARAMETERS

### -ModuleName
Spécifie un tableau de noms de modules.

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

### -TestType
Spécifie un tableau de types de test.
Les valeurs valides sont simple, complète ou les deux.
La valeur par défaut est « simple, complète ».

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas diriger d’entrée vers cette applet de commande.

## SORTIES

### PSCustomObject
Le **PSCustomObject** décrit la validation.

## REMARQUES

## LIENS CONNEXES

[Invoke-OperationValidation](Invoke-OperationValidation.md)
