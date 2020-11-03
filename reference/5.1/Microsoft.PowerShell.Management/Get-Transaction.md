---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Transaction
ms.openlocfilehash: bb8e9e1f204c67207f31613181f856d3bcaf8dc3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200798"
---
# Get-Transaction

## SYNOPSIS
Obtient la transaction actuelle (active).

## SYNTAX

```
Get-Transaction [<CommonParameters>]
```

## Description
L’applet de commande **obtenir-transaction** obtient un objet qui représente la transaction actuelle dans la session.

Cette applet de commande ne retourne jamais plusieurs objets, car une seule transaction est active à la fois.
Si vous démarrez une ou plusieurs transactions indépendantes (à l’aide du paramètre Independent de start-transaction), la transaction démarrée le plus récemment est active, et c’est la transaction que l’opération d' **extraction de transaction** a retournée.

Lorsque toutes les transactions actives ont été restaurées ou validées, cette applet de commande affiche la transaction qui a été active en dernier dans la session.

Cette applet de commande est l’un des ensembles d’applets de commande qui prennent en charge la fonctionnalité des transactions dans Windows PowerShell.
Pour plus d'informations, consultez about_Transactions.

## EXEMPLES

### Exemple 1 : récupération de la transaction en cours

```
PS C:\> Start-Transaction
PS C:\> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Cette commande utilise l'applet de commande Get-Transaction pour obtenir la transaction actuelle.

### Exemple 2 : afficher les propriétés et les méthodes de l’objet transaction

```
PS C:\> Get-Transaction | Get-Member

Name               MemberType Definition
----               ---------- ----------
Dispose            Method     System.Void Dispose(), System.Void Dispose(Boolean disposing)
Equals             Method     System.Boolean Equals(Object obj)
GetHashCode        Method     System.Int32 GetHashCode()
GetType            Method     System.Type GetType()
ToString           Method     System.String ToString()
IsCommitted        Property   System.Boolean IsCommitted {get;}
IsRolledBack       Property   System.Boolean IsRolledBack {get;}
RollbackPreference Property   System.Management.Automation.RollbackSeverity RollbackPreference {get;}
SubscriberCount    Property   System.Int32 SubscriberCount {get;set;}
```

Cette commande utilise l'applet de commande Get-Member pour afficher les propriétés et les méthodes de l'objet transaction.

### Exemple 3 : afficher les valeurs de propriété d’une transaction restaurée

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Undo-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ----------
Error                0                 RolledBack
```

Cette commande affiche les valeurs de propriété d'un objet transaction d'une transaction restaurée.

### Exemple 4 : afficher les valeurs de propriété d’une transaction validée

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

Cette commande affiche les valeurs de propriété d'un objet transaction d'une transaction validée.

### Exemple 5 : démarrer une transaction pendant qu’une autre est en cours

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany2 -UseTransaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

Cet exemple illustre le démarrage d'une transaction pendant qu'une autre transaction est en cours et ses effets sur l'objet transaction.
En général, cela se produit lorsqu'un script qui exécute une transaction inclut une fonction ou appelle un script qui contient une autre transaction complète.

À moins que la deuxième commande **start-transaction** inclue le paramètre *Independent* , **start-transaction** ne crée pas de nouvelle transaction.
Au lieu de cela, elle ajoute un deuxième abonné à la transaction d'origine.

La première commande **start-transaction** démarre la transaction.
Une commande New-Item avec le paramètre *UseTransaction* fait partie de la transaction.

Une deuxième commande **start-transaction** ajoute un abonné à la transaction.
La commande New-Item suivante fait également partie de la transaction.

La première commande d' **extraction de transaction** affiche la transaction multi-abonnés.
Notez que le nombre d'abonnés a la valeur 2.

La première commande Complete-Transaction ne valide pas la transaction, mais elle réduit le nombre d'abonnés à 1.

La deuxième commande **Complete-Transaction** valide la transaction.

### Exemple 6 : démarrer une transaction indépendante pendant qu’une autre est en cours

```
PS C:\>
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Start-Transaction -Independent
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
```

Cet exemple illustre le démarrage d'une transaction indépendante pendant qu'une autre transaction est en cours et ses effets sur l'objet transaction.

La première commande **start-transaction** démarre la transaction.
Une commande **New-Item** avec le paramètre *UseTransaction* fait partie de la transaction.

Une deuxième commande **start-transaction** ajoute un abonné à la transaction.
La commande **New-Item** suivante fait également partie de la transaction.

La première commande d' **extraction de transaction** affiche la transaction multi-abonnés.
Notez que le nombre d'abonnés a la valeur 2.

La commande **Complete-Transaction** réduit le nombre d’abonnés à 1, mais elle ne valide pas la transaction.

La deuxième commande **Complete-Transaction** valide la transaction.

## PARAMETERS

### CommonParameters
Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### System. Management. Automation. PSTransaction
Cette applet de commande retourne un objet qui représente la transaction actuelle.

## REMARQUES

## LIENS CONNEXES

[Complete-Transaction](Complete-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)

[Use-Transaction](Use-Transaction.md)

[New-Item](New-Item.md)
