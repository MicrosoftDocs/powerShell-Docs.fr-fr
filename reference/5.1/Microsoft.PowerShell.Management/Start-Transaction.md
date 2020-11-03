---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transaction
ms.openlocfilehash: 53be131f45f15e5d2053b183040dc7b3dca4a14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203482"
---
# Start-Transaction

## SYNOPSIS
Démarre une transaction.

## SYNTAX

```
Start-Transaction [-Timeout <Int32>] [-Independent] [-RollbackPreference <RollbackSeverity>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## Description
L’applet de commande **start-transaction** démarre une transaction, qui est une série de commandes gérées en tant qu’unité.
Une transaction peut être terminée ou validée.
Elle peut également être complètement annulée, ou restaurée, de sorte que toutes les données modifiées par la transaction sont restaurées à leur état d’origine.
Comme les commandes figurant dans une transaction sont gérées en bloc, toutes les commandes sont soit validées soit restaurées.

Par défaut, si une commande de la transaction génère une erreur, les transactions sont restaurées automatiquement.
Vous pouvez utiliser le paramètre *RollbackPreference* pour modifier ce comportement.

Les applets de commande utilisées dans une transaction doivent être conçues pour prendre en charge les transactions.
Les applets de commande qui prennent en charge les transactions ont un paramètre *UseTransaction* .
Pour exécuter des transactions dans un fournisseur, le fournisseur doit prendre en charge les transactions.
Le fournisseur de Registre Windows PowerShell dans Windows Vista et les versions ultérieures du système d’exploitation Windows prend en charge les transactions.
Vous pouvez également utiliser la classe **Microsoft. PowerShell. Commands. Management. TransactedString** pour inclure des expressions dans les transactions sur toute version du système Windows qui prend en charge Windows PowerShell.
D’autres fournisseurs Windows PowerShell peuvent également prendre en charge les transactions.

Une seule transaction peut être active à la fois.
Si vous démarrez une nouvelle transaction indépendante pendant qu’une transaction est en cours, la nouvelle transaction devient la transaction active et vous devez valider ou restaurer la nouvelle transaction avant d’apporter des modifications à la transaction d’origine.

L’applet de commande **start-transaction** fait partie d’un ensemble d’applets de commande qui prennent en charge la fonctionnalité des transactions dans Windows PowerShell.
Pour plus d'informations, consultez about_Transactions.

## EXEMPLES

### Exemple 1 : Démarrer et restaurer une transaction

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Undo-Transaction
```

Ces commandes démarrent une transaction, puis la restaurent.
Comme la transaction est restaurée, aucune modification n’est apportée au Registre.

### Exemple 2 : Démarrer et terminer une transaction

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
```

Ces commandes démarrent une transaction, puis l’exécutent.
Aucune modification n’est apportée au Registre tant que la commande **Complete-Transaction** n’est pas utilisée.

### Exemple 3 : utiliser des préférences de restauration différentes

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

# Start-Transaction (-rollbackpreference error)

PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name ContosoCompany -UseTransaction

PS HKCU:\software> New-Item -Path . -Name "Contoso" -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  -Path . -Name ContosoCompany -UseTransaction

# Start-Transaction (-rollbackpreference never)

PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction

New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany                 {}
PS HKCU:\Software> Complete-Transaction

# Succeeds
```

Cet exemple illustre l’effet de la modification de la valeur du paramètre *RollbackPreference* .

Dans le premier jeu de commandes, **start-transaction** n’utilise pas *RollbackPreference* .
Par conséquent, la valeur par défaut (Error) est utilisée.
Lorsqu’une erreur se produit dans une commande de transaction, autrement dit, si le chemin d’accès spécifié n’existe pas, la transaction est automatiquement restaurée.

Dans le deuxième jeu de commandes, **start-transaction** utilise *RollbackPreference* avec la valeur Never.
Lorsqu’une erreur se produit dans une commande de transaction, la transaction est par conséquent encore active et peut être exécutée.

Étant donné que la plupart des transactions doivent être exécutées sans erreur, la valeur par défaut de *RollbackPreference* est généralement préférée.

### Exemple 4 : utilisez cette applet de commande pendant qu’une transaction est en cours

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction
PS HKCU:\software> Get-Transaction
PS HKCU:\software> New-Item "ContosoCompany2" -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\Software> Get-Transaction
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

Cet exemple montre l’effet de l’utilisation de **start-transaction** pendant qu’une transaction est en cours.
L’effet est similaire à la jonction de la transaction en cours.

Bien qu’il s’agisse d’une commande simplifiée, ce scénario se produit souvent lorsque la transaction implique l’exécution d’un script qui inclut une transaction complète.

La première commande **start-transaction** démarre la transaction.
La première commande **New-Item** fait partie de la transaction.

La deuxième commande **start-transaction** ajoute un nouvel abonné à la transaction.
La commande **obtenir-transaction** retourne désormais une transaction avec un nombre d’abonnés de 2.
La deuxième commande **New-Item** fait partie de la même transaction.

Aucune modification n’est apportée au Registre tant que l’intégralité de la transaction n’est pas terminée.
Pour terminer la transaction, vous devez entrer deux commandes **Complete-Transaction** , une pour chaque abonné.
Si vous deviez restaurer la transaction à tout moment, toute la transaction est restaurée pour les deux abonnés.

### Exemple 5 : démarrer une transaction indépendante pendant qu’une transaction est en cours

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -Independent
PS HKCU:\software> Get-Transaction
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
MyKey
-----
123
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   1 MyCompany                      {MyKey}
```

Cet exemple montre l’effet de l’utilisation du paramètre *Independent* de **start-transaction** pour démarrer une transaction pendant qu’une autre transaction est en cours.
Dans ce cas, la nouvelle transaction est restaurée sans affecter la transaction d’origine.

Même si les transactions sont logiquement indépendantes, comme une seule transaction peut être active à la fois, vous devez restaurer ou valider la transaction la plus récente avant de reprendre le travail sur la transaction d’origine.

Le premier jeu de commandes démarre une transaction.
La commande **New-Item** fait partie de la première transaction.

Dans le deuxième jeu de commandes, la commande **start-transaction** utilise le paramètre *Independent* .
La commande **obtenir une transaction** qui suit affiche l’objet transaction de la transaction active, qui est la plus récente.
Le nombre d’abonnés est égal à 1, ce qui indique que les transactions ne sont pas liées.

Lorsque la transaction active est restaurée à l’aide d’une commande **Undo-Transaction** , la transaction d’origine redevient active.

La commande **New-ItemProperty** , qui fait partie de la transaction d’origine, se termine sans erreur et la transaction d’origine peut être exécutée à l’aide de la commande **Complete-Transaction** .
Le Registre est par conséquent modifié.

### Exemple 6 : exécuter des commandes qui ne font pas partie d’une transaction

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany1" -UseTransaction
PS HKCU:\software> New-Item "ContosoCompany2"
PS HKCU:\software> New-Item "ContosoCompany3" -UseTransaction
PS HKCU:\software> dir contoso*
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany2                {}

PS HKCU:\Software> Complete-Transaction
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany1                     {}
0   0 ContosoCompany2                     {}
0   0 ContosoCompany3                     {}
```

Cet exemple montre que les commandes qui sont envoyées pendant qu’une transaction est en cours peuvent être incluses ou non dans la transaction.
Seules les commandes qui utilisent le paramètre *UseTransaction* font partie de la transaction.

La première et la troisième commandes **New-Item** utilisent le paramètre *UseTransaction* .
Ces commandes font partie de la transaction.
Étant donné que la deuxième commande **New-Item** n’utilise pas le paramètre *UseTransaction* , elle ne fait pas partie de la transaction.

La première commande dir montre l’effet.
La deuxième commande **New-Item** est exécutée immédiatement, mais la première et la troisième commandes **New-Item** ne sont pas effectives tant que la transaction n’est pas validée.

La commande **Complete-Transaction** valide la transaction.
Par conséquent, la deuxième commande dir indique que tous les nouveaux éléments sont ajoutés au registre.

### Exemple 7 : restaurer une transaction qui ne se termine pas dans un délai spécifié

```
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> Get-Transaction
PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> > Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----------
Error                1                 RolledBack

PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  MyCompany -UseTransaction
```

Cette commande utilise le paramètre *timeout* de **start-transaction** pour démarrer une transaction qui doit être effectuée dans les deux minutes.
Si la transaction n’est pas terminée lorsque le délai d’attente expire, elle est automatiquement restaurée.

Lorsque le délai d’attente expire, vous n’êtes pas notifié, mais la propriété **Status** de l’objet transaction est définie sur valeur RolledBack et les commandes qui utilisent le paramètre *UseTransaction* échouent.

## PARAMETERS

### -Indépendant
Indique que cette applet de commande démarre une transaction qui est indépendante de toutes les transactions en cours.
Par défaut, si vous utilisez **start-transaction** pendant qu’une autre transaction est en cours, un nouvel abonné est ajouté à la transaction en cours.
Ce paramètre prend uniquement effet lorsqu’une transaction est déjà en cours dans la session.

Par défaut, si vous utilisez **start-transaction** pendant qu’une transaction est en cours, l’objet transaction existant est réutilisé et le nombre d’abonnés est incrémenté.
L’effet est similaire à la jonction de la transaction d’origine.
Une commande Undo-Transaction restaure l’ensemble de la transaction.
Pour exécuter la transaction, vous devez entrer une commande Complete-Transaction pour chaque abonné.
Comme la plupart des transactions qui sont simultanément en cours sont liées, la valeur par défaut est suffisante dans la majorité des cas.

Si vous spécifiez le paramètre *Independent* , cette applet de commande crée une nouvelle transaction qui peut être terminée ou annulée sans affecter la transaction d’origine.
Comme une seule transaction peut être active à la fois, vous devez toutefois exécuter ou restaurer la nouvelle transaction avant de reprendre le travail sur la transaction d’origine.

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

### -RollbackPreference
Spécifie les conditions dans lesquelles une transaction est automatiquement restaurée.
Les valeurs valides pour ce paramètre sont :

- Erreur.
la transaction est automatiquement restaurée en cas d'erreur avec ou sans fin d'exécution.
- TerminatingError.
la transaction est automatiquement restaurée en cas d'erreur avec fin d'exécution.
- Jamais.
la transaction n'est jamais restaurée automatiquement.

La valeur par défaut est Error.

```yaml
Type: System.Management.Automation.RollbackSeverity
Parameter Sets: (All)
Aliases:
Accepted values: Error, TerminatingError, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Timeout
Spécifie la durée maximale d’activité de la transaction (en minutes).
Lorsque le délai d’attente expire, la transaction est automatiquement restaurée.

Par défaut, aucun délai d’attente n’est défini pour les transactions qui sont démarrées au niveau de la ligne de commande.
Lorsque les transactions sont démarrées par un script, le délai d’attente par défaut est de 30 minutes.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutMins

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

### Aucun
Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun
Cette applet de commande ne génère aucune sortie.

## REMARQUES

## LIENS CONNEXES

[Complete-Transaction](Complete-Transaction.md)

[Get-Transaction](Get-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)

[Use-Transaction](Use-Transaction.md)
