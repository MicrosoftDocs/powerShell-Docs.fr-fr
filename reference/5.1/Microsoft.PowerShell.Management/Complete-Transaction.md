---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/complete-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Complete-Transaction
ms.openlocfilehash: 20fbdd86aab07dda065492eff2da4f358fb2ffca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204065"
---
# Complete-Transaction

## SYNOPSIS
Valide la transaction active.

## SYNTAX

```
Complete-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description
L’applet **de commande Complete-Transaction** valide une transaction active.
Lorsque vous validez une transaction, les commandes de la transaction sont finalisées et les données concernées par les commandes sont modifiées.

Si la transaction comporte plusieurs abonnés, pour valider la transaction, vous devez entrer une commande **Complete-Transaction** pour chaque commande Start-Transaction.

L’applet de commande **Complete-Transaction** fait partie d’un ensemble d’applets de commande qui prennent en charge la fonctionnalité des transactions dans Windows PowerShell.
Pour plus d'informations, consultez about_Transactions.

## EXEMPLES

### Exemple 1 : valider une transaction

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}
```

Cet exemple montre ce qui se passe lorsque vous utilisez l’applet de commande **Complete-Transaction** pour valider une transaction.

La commande **start-transaction** démarre la transaction.
La commande New-Item utilise le paramètre *UseTransaction* pour inclure la commande dans la transaction.

La première commande dir (obten-ChildItem) indique que le nouvel élément n’a pas encore été ajouté au registre.

La commande **Complete-Transaction** valide la transaction, ce qui rend la modification du Registre effective.
Par conséquent, la deuxième commande dir indique que le registre a été modifié.

### Exemple 2 : valider une transaction qui a plusieurs abonnés

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
0   0 MyCompany                      {}

PS HKCU:\software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                2                Active

PS HKCU:\software> New-ItemProperty -Path MyCompany -Name MyKey -Value -UseTransaction

MyKey
-----
123

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                1                Active

PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   1 MyCompany                      {MyKey}
```

Cet exemple montre comment utiliser la méthode **Complete-Transaction** pour valider une transaction qui a plusieurs abonnés.

Pour valider une transaction multi-abonné, vous devez entrer une commande **Complete-Transaction** pour chaque commande **start-transaction** .
Les données ne sont modifiées que lorsque la commande final **Complete-Transaction** est envoyée.

À des fins de démonstration, cet exemple montre une série de commandes entrées au niveau de la ligne de commande.
Dans la pratique, les transactions sont susceptibles d’être exécutées dans des scripts, la transaction secondaire étant exécutée par un script de fonction ou d’application d’assistance appelé par le script principal.

Dans cet exemple, une commande **start-transaction** démarre la transaction.
Une commande **New-Item** avec le paramètre *UseTransaction* ajoute la clé MyCompany à la clé du logiciel.
Bien que l’applet **de commande New-Item** retourne un objet clé, les données du registre ne sont pas encore modifiées.

Une deuxième commande **start-transaction** ajoute un deuxième abonné à la transaction existante.
L’applet de commande **« obtient-transaction »** confirme que le nombre d’abonnés est 2.
Une commande New-ItemProperty avec le paramètre *UseTransaction* ajoute une entrée de Registre à la nouvelle clé MyCompany.
Là encore, la commande retourne une valeur, mais le Registre n’est pas modifié.

La première commande **Complete-Transaction** réduit le nombre d’abonnés de 1.
Cette opération est confirmée par une commande d' **extraction de transaction** .
Toutefois, aucune donnée n’est modifiée, comme l’atteste une commande dir m * ( **obtenir-ChildItem** ).

La deuxième commande **Complete-Transaction** valide la transaction entière et modifie les données dans le registre.
Elle est confirmée par une deuxième commande dir m *, qui affiche les modifications.

### Exemple 3 : exécuter une transaction qui ne modifie aucune donnée

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> dir m* -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}

PS HKCU:\software> Complete-Transaction
```

Cet exemple montre la valeur de l’utilisation de commandes « obtenir » \* et d’autres commandes qui ne modifient pas les données dans une transaction.
Lorsqu’une \* commande d’extraction est utilisée dans une transaction, elle obtient les objets qui font partie de la transaction.
Cela vous permet d’afficher un aperçu des modifications apportées à la transaction avant de les valider.

Dans cet exemple, une transaction est démarrée.
Une commande New-Item avec le paramètre *UseTransaction* ajoute une nouvelle clé au registre dans le cadre de la transaction.

Étant donné que la nouvelle clé de Registre n’est pas ajoutée au Registre tant que la commande **Complete-Transaction** n’est pas exécutée, une simple commande dir ( **obtenir-ChildItem** ) affiche le registre sans la nouvelle clé.

Toutefois, lorsque vous ajoutez le paramètre *UseTransaction* à la commande dir, la commande devient partie intégrante de la transaction et elle obtient les éléments de la transaction même s’ils ne sont pas encore ajoutés aux données.

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
Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

* Vous ne pouvez pas restaurer une transaction qui a été validée, ni valider une transaction qui a été restaurée.

  Vous ne pouvez pas restaurer une autre transaction que la transaction active.
Pour restaurer une autre transaction, vous devez commencer par valider ou restaurer la transaction active.

  En cas d’impossibilité de valider une partie d’une transaction (lorsqu’une commande dans la transaction génère une erreur, par exemple), la transaction est par défaut entièrement restaurée.

*

## LIENS CONNEXES

[Get-Transaction](Get-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)

[Use-Transaction](Use-Transaction.md)

[Get-ChildItem](Get-ChildItem.md)

[New-Item](New-Item.md)

[New-ItemProperty](New-ItemProperty.md)
