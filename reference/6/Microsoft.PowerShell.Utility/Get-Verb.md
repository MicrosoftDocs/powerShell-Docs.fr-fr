---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 516ecf2b5d6e3bce2a0cda7c36c143d2ba75933a
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "93206041"
---
# Get-Verb

## SYNOPSIS
Obtient les verbes PowerShell approuvés.

## SYNTAX

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## Description

La `Get-Verb` fonction obtient les verbes dont l’utilisation est approuvée dans les commandes PowerShell.

Il est recommandé que les noms des applets de commande et des fonctions PowerShell aient le `Verb-Noun` format et incluent un verbe approuvé. Cette pratique rend les noms des commandes plus cohérents, prévisibles et plus faciles à utiliser.

Les commandes qui utilisent des verbes non approuvés, s’exécutent toujours dans PowerShell. Toutefois, lorsque vous importez un module qui comprend une commande dont le nom contient un verbe non approuvé, la `Import-Module` commande affiche un message d’avertissement.

> [!NOTE]
> La liste de verbes `Get-Verb` retournée peut ne pas être terminée. Pour obtenir une liste actualisée des verbes PowerShell approuvés avec des descriptions, consultez [verbes approuvés](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) dans le Microsoft docs.

## Exemples

### Exemple 1 : obtenir une liste de tous les verbes

```powershell
Get-Verb
```

### Exemple 2 : obtenir la liste des verbes approuvés qui commencent par « un »

```powershell
Get-Verb un*
```

```Output
Verb       AliasPrefix Group     Description
----       ----------- -----     -----------
Undo       un          Common    Sets a resource to its previous state
Unlock     uk          Common    Releases a resource that was locked
Unpublish  ub          Data      Makes a resource unavailable to others
Uninstall  us          Lifecycle Removes a resource from an indicated location
Unregister ur          Lifecycle Removes the entry for a resource from a repository
Unblock    ul          Security  Removes restrictions to a resource
Unprotect  up          Security  Removes safeguards from a resource that were added to prevent it from attack or loss
```

### Exemple 3 : récupération de tous les verbes approuvés dans le groupe de sécurité

```powershell
Get-Verb -Group Security
```

```Output
Verb      AliasPrefix Group    Description
----      ----------- -----    -----------
Block     bl          Security Restricts access to a resource
Grant     gr          Security Allows access to a resource
Protect   pt          Security Safeguards a resource from attack or loss
Revoke    rk          Security Specifies an action that does not allow access to a resource
Unblock   ul          Security Removes restrictions to a resource
Unprotect up          Security Removes safeguards from a resource that were added to prevent it from attack or loss
```

### Exemple 4 : recherche toutes les commandes dans un module qui ont des verbes non approuvés

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## PARAMETERS

### -Verbe

Obtient uniquement les verbes spécifiés. Entrez le nom d'un verbe ou d'un modèle de nom. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Common, Communications, Data, Diagnostic, Lifecycle, Other, Security

Required: False
Position: 1
Default value: All groups
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Group

Obtient uniquement les groupes spécifiés. Entrez le nom d’un groupe. Les caractères génériques ne sont pas autorisés.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All verbs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

## SORTIES

### System. Management. Automation. VerbInfo

## REMARQUES

Les verbes PowerShell sont affectés à un groupe en fonction de leur utilisation la plus courante. Les groupes sont conçus pour faciliter la recherche et la comparaison des verbes, sans limiter leur utilisation. Vous pouvez utiliser n'importe quel verbe approuvé pour n'importe quel type de commande.

Chaque verbe PowerShell est affecté à l’un des groupes suivants.

- Commun : définissez des actions génériques qui peuvent s’appliquer à presque n’importe quelle applet de commande, telle que Add.
- Communications : définissez les actions qui s’appliquent aux communications, telles que Connect.
- Données : définissez les actions qui s’appliquent à la gestion des données, telles que la sauvegarde.
- Diagnostic : définissez les actions qui s’appliquent aux diagnostics, telles que le débogage.
- Cycle de vie : définissez les actions qui s’appliquent au cycle de vie d’une applet de commande, comme complet.
- Sécurité : définissez les actions qui s’appliquent à la sécurité, telles que REVOKE.
- Autre : définissez d’autres types d’actions.

Certaines des applets de commande installées avec PowerShell, telles que `Tee-Object` et `Where-Object` , utilisent des verbes non approuvés. Ces applets de commande sont des exceptions historiques et leurs verbes sont classés comme **réservés** .

## LIENS CONNEXES

[Module d’importation](../microsoft.powershell.core/import-module.md)
