---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-ControlPanelItem
ms.openlocfilehash: 368e385d51437f9ac93b700c929b185dce30a644
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203489"
---
# Show-ControlPanelItem

## SYNOPSIS
Ouvre les éléments du panneau de commande.

## SYNTAX

### RegularName (par défaut)

```
Show-ControlPanelItem [-Name] <String[]> [<CommonParameters>]
```

### CanonicalName

```
Show-ControlPanelItem -CanonicalName <String[]> [<CommonParameters>]
```

### ControlPanelItem

```
Show-ControlPanelItem [[-InputObject] <ControlPanelItem[]>] [<CommonParameters>]
```

## Description

L' `Show-ControlPanelItem` applet de commande ouvre les éléments du panneau de configuration sur l’ordinateur local. Vous pouvez l’utiliser pour ouvrir des éléments du panneau de configuration par nom, catégorie ou description, même sur des systèmes qui n’ont pas d’interface utilisateur. Vous pouvez diriger les éléments du panneau de configuration de l' `Get-ControlPanelItem` applet de commande vers `Show-ControlPanelItem` .

`Show-ControlPanelItem` recherche uniquement les éléments du panneau de configuration qui peuvent être ouverts sur le système. Sur les ordinateurs qui ne disposent pas **du panneau de configuration** ou de l' **Explorateur de fichiers** , `Show-ControlPanelItem` recherche uniquement les éléments du panneau de configuration qui peuvent être ouverts sans ces composants.

Cette applet de commande a été introduite dans Windows PowerShell 3,0 et fonctionne sur Windows 8, Windows Server 2012 et versions ultérieures.

## EXEMPLES

### Exemple 1 : afficher un élément du panneau de configuration

Cet exemple lance l’élément du panneau de configuration de l' **exécution automatique** .

```powershell
Show-ControlPanelItem -Name "AutoPlay"
```

### Exemple 2 : diriger un élément du panneau de configuration vers cette applet de commande

Cet exemple ouvre l’élément du panneau de configuration du **pare-feu Windows Defender** sur l’ordinateur local.
Le nom de l’élément du panneau de configuration du pare-feu Windows a changé par rapport aux versions de Windows. Cet exemple utilise un modèle de caractère générique pour Rechercher l’élément du panneau de configuration.

```powershell
Get-ControlPanelItem -Name "*Firewall" | Show-ControlPanelItem
```

`Get-ControlPanelItem` Obtient l’élément du panneau de configuration et l’applet de commande l' `Show-ControlPanelItem` ouvre.

### Exemple 3 : Utiliser un nom de fichier pour ouvrir un élément du Panneau de configuration

Cet exemple ouvre l’élément **programmes et fonctionnalités** du panneau de configuration en utilisant son nom d’application.

```powershell
appwiz.cpl
```

Cette méthode est une alternative à l’utilisation d’une `Show-ControlPanelItem` commande.

> [!NOTE]
> Dans PowerShell, vous pouvez omettre l’extension de fichier. cpl pour les fichiers du panneau de configuration, car elle est incluse dans la valeur de la `$env:PathExt` variable d’environnement.

## PARAMETERS

### -CanonicalName

Spécifie les éléments du panneau de configuration à l’aide des noms canoniques ou modèles de nom spécifiés. Les caractères génériques sont autorisés. Si vous entrez plusieurs noms, cette applet de commande ouvre les éléments du panneau de configuration qui correspondent à l’un des noms, comme si les éléments de la liste de noms étaient séparés par un opérateur **or** .

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

### -InputObject

Spécifie les éléments du panneau de configuration à ouvrir en envoyant des objets éléments du panneau de configuration. Entrez une variable qui contient les objets éléments du panneau de configuration, ou tapez une commande ou une expression qui obtient les objets éléments du panneau de configuration, tels que `Get-ControlPanelItem` .

```yaml
Type: Microsoft.PowerShell.Commands.ControlPanelItem[]
Parameter Sets: ControlPanelItem
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Spécifie les noms des éléments du panneau de configuration. Les caractères génériques sont autorisés. Si vous entrez plusieurs noms, cette applet de commande ouvre les éléments du panneau de configuration qui correspondent à l’un des noms, comme si les éléments de la liste de noms étaient séparés par un opérateur **or** .

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. String, Microsoft. PowerShell. Commands. ControlPanelItem

Vous pouvez diriger un nom ou un objet élément du panneau de configuration vers cette applet de commande.

## SORTIES

### Aucun

Cette applet de commande ne retourne aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Get-ControlPanelItem](Get-ControlPanelItem.md)
