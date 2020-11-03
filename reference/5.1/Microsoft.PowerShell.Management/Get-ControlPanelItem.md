---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ControlPanelItem
ms.openlocfilehash: 51bc04b4de901a611330266b6b0f58471f998432
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204025"
---
# Get-ControlPanelItem

## SYNOPSIS
Obtient les éléments du panneau de commande.

## SYNTAX

### RegularName (par défaut)

```
Get-ControlPanelItem [[-Name] <String[]>] [-Category <String[]>] [<CommonParameters>]
```

### CanonicalName

```
Get-ControlPanelItem -CanonicalName <String[]> [-Category <String[]>] [<CommonParameters>]
```

## Description

L' `Get-ControlPanelItem` applet de commande obtient les éléments du panneau de configuration sur l’ordinateur local. Vous pouvez l’utiliser pour rechercher des éléments du Panneau de configuration par nom, catégorie ou description, même sur des systèmes sans interface utilisateur.

Cette applet de commande obtient uniquement les éléments du panneau de configuration qui peuvent être ouverts sur le système. Sur les ordinateurs qui ne disposent pas du panneau de configuration ou de l’Explorateur de fichiers, cette applet de commande obtient uniquement les éléments du panneau de configuration qui peuvent être ouverts sans ces composants.

Cette applet de commande a été introduite dans Windows PowerShell 3.0. Il fonctionne uniquement sur Windows 8 et Windows Server 2012 et versions ultérieures.

## EXEMPLES

### Exemple 1 : Obtenir tous les éléments du Panneau de configuration

Cette commande obtient tous les éléments du Panneau de configuration présents sur l’ordinateur local.

```powershell
Get-ControlPanelItem
```

```Output
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and...
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s...
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo...
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin...
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana...
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden...
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...
...
```

### Exemple 2 : Obtenir les éléments du Panneau de configuration par nom

Cet exemple obtient les éléments du panneau de configuration dont le nom contient le programme ou l’application.

```powershell
Get-ControlPanelItem -Name "*Program*", "*App*"
```

### Exemple 3 : Obtenir les éléments du Panneau de configuration par catégorie

Cette commande obtient tous les éléments du panneau de configuration dans les catégories dont le nom contient la sécurité.

```powershell
Get-ControlPanelItem -Category "*Security*"
```

### Exemple 4 : Ouvrir un élément du Panneau de configuration

Cet exemple ouvre l’élément du panneau de configuration du pare-feu Windows sur l’ordinateur local.

```powershell
Get-ControlPanelItem -Name "Windows Firewall" | Show-ControlPanelItem
```

L' `Get-ControlPanelItem` applet de commande obtient l’élément du panneau de configuration. L’applet de commande l' `Show-ControlPanelItem` ouvre.

### Exemple 5 : Obtenir les éléments du Panneau de configuration sur un ordinateur distant

Cet exemple obtient l’Chiffrement de lecteur BitLocker élément du panneau de configuration sur l’ordinateur distant SERVEUR01.
L' `Invoke-Command` applet de commande exécute l' `Get-ControlPanelItem` applet de commande à distance.

```powershell
Invoke-Command -ComputerName "Server01" {Get-ControlPanelItem -Name "BitLocker*" }
```

### Exemple 6 : Rechercher les descriptions des éléments du Panneau de configuration

Cet exemple recherche la propriété **Description** des éléments du panneau de configuration pour n’afficher que ceux qui contiennent le nom de l' **appareil** .

```powershell
Get-ControlPanelItem | Where-Object {$_.Description -like "*Device*"}
```

```Output
Name                    CanonicalName                 Category    Description
----                    -------------                 --------    -----------
AutoPlay                Microsoft.AutoPlay            {Hardware}  Change default settings fo...
Devices and Printers    Microsoft.DevicesAndPrinters  {Hardware}  View and manage devices, p...
Sound                   Microsoft.Sound               {Hardware}  Configure your audio devic...
```

L' `Get-ControlPanelItem` applet de commande obtient tous les éléments du panneau de configuration. L' `Where-Object` applet de commande filtre les éléments selon la valeur de la propriété **Description** .

## PARAMETERS

### -CanonicalName

Spécifie, sous forme de tableau de chaînes, les éléments du panneau de configuration par leurs noms canoniques ou modèles de nom que cette applet de commande obtient. Les caractères génériques sont autorisés. Si vous entrez plusieurs noms, cette applet de commande obtient les éléments du panneau de configuration qui correspondent à l’un des noms, comme si les éléments de la liste de noms étaient séparés par un opérateur « or ».

Par défaut, cette applet de commande obtient tous les éléments du panneau de configuration du système.

```yaml
Type: System.String[]
Parameter Sets: CanonicalName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Catégorie

Spécifie, sous forme de tableau de chaînes, les catégories des éléments du panneau de configuration dans les catégories spécifiées que cette applet de commande obtient. Entrez un nom de catégorie ou un modèle de nom. Les caractères génériques sont autorisés. Si vous entrez plusieurs noms, cette applet de commande obtient les éléments du panneau de configuration qui correspondent à l’un des noms, comme si les éléments de la liste de noms étaient séparés par un opérateur « or ». Par défaut, cette applet de commande obtient tous les éléments du panneau de configuration du système.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

Spécifie, sous forme de tableau de chaînes, les noms ou modèles de nom du panneau de configuration que cette applet de commande obtient.
Les caractères génériques sont autorisés. Vous pouvez également diriger un nom ou un modèle de nom vers cette applet de commande.

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger un nom ou un modèle de nom vers cette applet de commande.

## SORTIES

### Microsoft. PowerShell. Commands. ControlPanelItem

Cette applet de commande obtient les éléments du panneau de configuration sur l’ordinateur local.

## REMARQUES

## LIENS CONNEXES

[Show-ControlPanelItem](Show-ControlPanelItem.md)
