---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/undo-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Undo-Transaction
ms.openlocfilehash: 1acb06ea7b05a2127b04a22c4c51b92cd68056f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203457"
---
# Undo-Transaction

## SYNOPSIS
Restaure la transaction active.

## SYNTAX

```
Undo-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet de **commande Undo-Transaction** restaure la transaction active.
Lorsque vous restaurez une transaction, les modifications apportées par les commandes de la transaction sont ignorées et les données sont restaurées dans leur forme d’origine.

Si la transaction comporte plusieurs abonnés, une commande **Undo-Transaction** restaure l’intégralité de la transaction pour tous les abonnés.

Les transactions sont automatiquement restaurées par défaut lorsqu’une commande figurant dans la transaction génère une erreur.
Toutefois, les transactions peuvent être démarrées à l’aide d’une préférence de restauration différente et vous pouvez utiliser cette applet de commande pour restaurer la transaction active à tout moment.

L’applet de **commande Undo-Transaction** fait partie d’un ensemble d’applets de commande qui prennent en charge la fonctionnalité des transactions dans Windows PowerShell.
Pour plus d'informations, consultez about_Transactions.

## EXEMPLES

### Exemple 1 : restaurer la transaction actuelle

```
PS C:\> Undo-Transaction
```

Cette commande restaure la transaction actuelle, active et active.

### Exemple 2 : Démarrer et restaurer une transaction

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Undo-Transaction
```

Cet exemple démarre une transaction, puis la restaure.
Aucune modification n’est par conséquent apportée au Registre.

### Exemple 3 : restaurer une transaction pour tous les abonnés

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                1                 Active

PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                2                 Active

PS HKCU:\Software> Undo-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                0                 RolledBack
```

Cet exemple montre que, lorsqu’un abonné restaure une transaction, toute la transaction est restaurée pour tous les abonnés.

La première commande change l’emplacement de la clé de Registre HKCU:\Software.

La deuxième commande démarre une transaction.

La troisième commande utilise l’applet de commande New-Item pour créer une clé de Registre.
La commande utilise le paramètre *UseTransaction* pour inclure la modification dans la transaction.

La quatrième commande utilise l’applet de commande Get-Transaction pour obtenir la transaction active.
Notez que l’état a la valeur Active et que le nombre d’abonnés a la valeur 1.

La cinquième commande réutilise la commande Start-Transaction.
En général, le démarrage d’une transaction pendant qu’une autre transaction est en cours se produit lorsqu’un script utilisé par la transaction principale comprend sa propre transaction complète.
Cet exemple est exécuté de manière interactive pour que vous puissiez l’examiner par étapes.
Quand vous exécutez une commande **start-transaction** alors qu’une autre transaction est en cours, les commandes joignent la transaction existante en tant que nouvel abonné et le nombre d’abonnés est incrémenté.

La sixième commande utilise l’applet de commande **« obtient-transaction »** pour récupérer la transaction active.
Notez que le nombre d’abonnés a maintenant la valeur 2.

La septième commande utilise **Undo-Transaction** pour restaurer la transaction.
Cette commande ne retourne pas d’objets.

La dernière commande est une commande d' **extraction de transaction** qui obtient le actif, ou dans ce cas, la dernière transaction active.
Les résultats indiquent que la transaction est restaurée et que le nombre d’abonnés a la valeur 0 (ce qui signifie que la transaction a été restaurée pour tous les abonnés).

## PARAMETERS

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

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun
Cette applet de commande ne retourne aucune sortie.

## REMARQUES

* Vous ne pouvez pas restaurer une transaction qui a été validée.

  Vous ne pouvez pas restaurer une autre transaction que la transaction active.
Pour restaurer une autre transaction indépendante, vous devez commencer par valider ou restaurer la transaction active.

  La restauration de la transaction termine la transaction.
Pour réutiliser une transaction, vous devez démarrer une nouvelle transaction.

## LIENS CONNEXES

[Complete-Transaction](Complete-Transaction.md)

[Get-Transaction](Get-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Use-Transaction](Use-Transaction.md)
