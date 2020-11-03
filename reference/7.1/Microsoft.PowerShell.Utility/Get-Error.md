---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: c29115a65b46d38039d78b10eee293e6944cede5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202838"
---
# Get-Error

## SYNOPSIS

Obtient et affiche les messages d’erreur les plus récents de la session active.

## SYNTAX

### La plus récente (par défaut)

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### Erreur

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## Description

L' `Get-Error` applet de commande obtient un objet **PSExtendedError** qui représente les détails de l’erreur actuelle de la dernière erreur qui s’est produite dans la session.

Vous pouvez utiliser `Get-Error` pour afficher un nombre spécifié d’erreurs qui se sont produites dans la session active à l’aide du paramètre le plus **récent** .

L' `Get-Error` applet de commande reçoit également des objets d’erreur d’une collection, tels que `$Error` , pour afficher plusieurs erreurs à partir de la session active.

## EXEMPLES

### Exemple 1 : récupérer les détails de l’erreur la plus récente

Dans cet exemple, `Get-Error` affiche les détails de l’erreur la plus récente qui s’est produite dans la session active.

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### Exemple 2 : récupérer le nombre spécifié de messages d’erreur qui se sont produits dans la session active

Cet exemple montre comment utiliser `Get-Error` avec le paramètre le plus **récent** . Dans cet exemple, le plus **récent** retourne les détails des 3 erreurs les plus récentes qui se sont produites dans cette session.

```powershell
Get-Error -Newest 3
```

### Exemple 3 : envoyer une collection d’erreurs pour recevoir des messages détaillés

La `$Error` variable automatique contient un tableau d’objets d’erreur dans la session active. Le tableau d’objets peut être redirigé vers `Get-Error` pour recevoir des messages d’erreur détaillés.

Dans cet exemple, `$Error` est dirigé vers l' `Get-Error` applet de commande. le résultat est la liste des messages d’erreur détaillés, comme le résultat de l’exemple 1.

```powershell
$Error | Get-Error
```

## PARAMETERS

### -Plus récent

Spécifie le nombre d’erreurs à afficher qui se sont produites dans la session active.

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Ce paramètre est utilisé pour l’entrée de pipeline.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### PSObject

Prend en charge l’entrée de n’importe quel **PSObject** , mais les résultats varient à moins qu’un objet **ErrorRecord** ou **exception** ne soit fourni.

## SORTIES

### System. Management. Automation. ErrorRecord # PSExtendedError

Sortie dans un objet **PSExtendedError** .

## REMARQUES

`Get-Error` accepte l’entrée de pipeline. Par exemple : `$Error | Get-Error`.

## LIENS CONNEXES

[about_Try_Catch_Finally](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
