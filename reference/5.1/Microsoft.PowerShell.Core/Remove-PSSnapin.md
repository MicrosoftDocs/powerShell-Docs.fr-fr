---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSnapin
ms.openlocfilehash: e74aff3e52c61f41a54664efbab9c0f195b0d409
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202677"
---
# Remove-PSSnapin

## SYNOPSIS
Supprime des composants logiciels enfichables Windows PowerShell de la session active.

## SYNTAX

```
Remove-PSSnapin [-Name] <String[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **Remove-PSSnapin** supprime un composant logiciel enfichable Windows PowerShell de la session active.
Vous pouvez l’utiliser pour supprimer les composants logiciels enfichables que vous avez ajoutés à Windows PowerShell. vous ne pouvez pas utiliser cette applet de commande pour supprimer les composants logiciels enfichables qui sont installés avec Windows PowerShell.

Une fois que vous avez supprimé un composant logiciel enfichable de la session active, le composant logiciel enfichable est toujours chargé, mais les applets de commande et les fournisseurs du composant logiciel enfichable ne sont plus disponibles dans la session.

## EXEMPLES

### Exemple 1 : supprimer un composant logiciel enfichable

```
PS C:\> remove-pssnapin -Name Microsoft.Exchange
```

Cette commande supprime le composant logiciel enfichable **Microsoft. Exchange** de la session active.
Une fois l'exécution de la commande terminée, les applets de commande et les fournisseurs pris en charge par le composant logiciel enfichable ne sont plus disponibles dans la session.

### Exemple 2 : supprimer les composants logiciels enfichables à l’aide de noms avec le pipeline

```
PS C:\> Get-PSSnapIn smp* | Remove-PSSnapIn
```

Cette commande supprime les composants logiciels enfichables Windows PowerShell dont les noms commencent par SMP à partir de la session active.

La commande utilise l’applet de commande **« obtient-PSSnapin »** pour récupérer les objets qui représentent les composants logiciels enfichables. L’opérateur de pipeline (|) envoie les résultats à l’applet de commande **Remove-PSSnapin** , qui les supprime de la session.
Les fournisseurs et les applets de commande pris en charge par ce composant logiciel enfichable ne sont plus disponibles dans la session.

Lorsque vous dirigez des objets vers **Remove-PSSnapin** , les noms des objets sont associés au paramètre *Name* , qui accepte les objets du pipeline qui ont une propriété **Name** .

### Exemple 3 : supprimer des composants logiciels enfichables à l’aide de noms

```
PS C:\> Remove-PSSnapin -Name *event*
```

Cette commande supprime tous les composants logiciels enfichables Windows PowerShell dont les noms incluent Event.

## PARAMETERS

### -Name
Spécifie les noms des composants logiciels enfichables Windows PowerShell à supprimer de la session active.
Les caractères génériques (*) sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru
Retourne un objet qui représente le composant logiciel enfichable.
Par défaut, cette applet de commande ne génère aucun résultat.

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

### -Confirm
Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSSnapInInfo
Vous pouvez diriger un objet de composant logiciel enfichable vers cette applet de commande.

## SORTIES

### Aucun, System. Management. Automation. PSSnapInInfo
Cette applet de commande génère un objet **System. Management. Automation. PSSnapInInfo** qui représente le composant logiciel enfichable, si vous spécifiez le paramètre *PassThru* .
Par défaut, **Remove-PSSnapin** ne génère pas de sortie.

## REMARQUES

* **Remove-PSSnapin** ne vérifie pas la version de Windows PowerShell avant de supprimer un composant logiciel enfichable de la session. Si un composant logiciel enfichable ne peut pas être supprimé, un avertissement s'affiche avant l'échec de la commande.
* **Remove-PSSnapin** affecte uniquement la session active. Si vous avez ajouté une commande Add-PSSnapin à votre profil Windows PowerShell, vous devez la supprimer pour retirer le composant logiciel enfichable des futures sessions. Pour obtenir des instructions, tapez `Get-Help about_Profiles` .

## LIENS CONNEXES

[Add-PSSnapin](Add-PSSnapin.md)

[Get-PSSnapin](Get-PSSnapin.md)
