---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/07/2018
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/get-verb?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 4474bb50c2bf3be10e72d2554190208e956f9040
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "93206034"
---
# Get-Verb

## SYNOPSIS
Obtient les verbes PowerShell approuvés.

## SYNTAX

```
Get-Verb [[-verb] <String[]>] [<CommonParameters>]
```

## Description

La `Get-Verb` fonction obtient les verbes dont l’utilisation est approuvée dans les commandes PowerShell.

PowerShell recommande l’applet de commande et les noms de fonctions ont le format Verb-Noun et incluent un verbe approuvé. Cette pratique rend les noms des commandes plus cohérents, prévisibles et plus faciles à utiliser.

Les commandes qui utilisent des verbes non approuvés s’exécutent dans PowerShell. Toutefois, lorsque vous importez un module qui comprend une commande dont le nom contient un verbe non approuvé, la `Import-Module` commande affiche un message d’avertissement.

> [!NOTE]
> La liste de verbes `Get-Verb` retournée peut ne pas être terminée. Pour obtenir une liste actualisée des verbes PowerShell approuvés avec des descriptions, consultez [verbes approuvés](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) dans le Microsoft docs.

## EXEMPLES

### Exemple 1 : obtenir une liste de tous les verbes

```powershell
Get-Verb
```

### Exemple 2 : obtenir la liste des verbes approuvés qui commencent par « un »

```powershell
Get-Verb un*
```

```Output
Verb                 Group
----                 -----
Undo                 Common
Unlock               Common
Unpublish            Data
Uninstall            Lifecycle
Unregister           Lifecycle
Unblock              Security
Unprotect            Security
```

### Exemple 3 : récupération de tous les verbes approuvés dans le groupe de sécurité

```powershell
Get-Verb | Where-Object Group -EQ Security
```

```Output
Verb      Group
----      -----
Block     Security
Grant     Security
Protect   Security
Revoke    Security
Unblock   Security
Unprotect Security
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

### -verbe

Obtient uniquement les verbes spécifiés.
Entrez le nom d'un verbe ou d'un modèle de nom.
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: All verbs
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

## ENTRÉES

### Aucun

## SORTIES

### Selected.Microsoft.PowerShell.Commands.MemberDefinition

## REMARQUES

`Get-Verb` retourne une version modifiée d’un objet Microsoft. PowerShell. Commands. MemberDefinition.
L'objet ne possède pas les propriétés standard d'un objet MemberDefinition. Au lieu de cela, il possède des propriétés Verb et Group. La propriété Verb contient une chaîne avec le nom du verbe. La propriété Group contient une chaîne avec le groupe du verbe.

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

[Module d’importation](import-module.md)
