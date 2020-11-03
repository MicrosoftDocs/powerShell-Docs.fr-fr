---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/use-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Use-Transaction
ms.openlocfilehash: db8423aef6dc4b25c4ddd13f9b29b774463c6a6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203465"
---
# Use-Transaction

## SYNOPSIS
Ajoute le bloc de script à la transaction active.

## SYNTAX

```
Use-Transaction [-TransactedScript] <ScriptBlock> [-UseTransaction] [<CommonParameters>]
```

## Description
L’applet de commande **use-transaction** ajoute un bloc de script à une transaction active.
Cela vous permet d’effectuer des scripts transactionnels à l’aide d’objets de l’infrastructure Microsoft .NET de transactions.
Le bloc de script ne peut contenir que des objets .NET Framework prenant en charge les transactions (instances de la classe Microsoft.PowerShell.Commands.Management.TransactedString, par exemple).

Le paramètre *UseTransaction* , qui est facultatif pour la plupart des applets de commande, est requis lorsque vous utilisez cette applet de commande.

**Use-transaction** est l’un des ensembles d’applets de commande qui prennent en charge la fonctionnalité des transactions dans Windows PowerShell.
Pour plus d'informations, consultez about_Transactions.

## EXEMPLES

### Exemple 1 : générer un script à l’aide d’un objet de transaction

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> $transactedString.ToString()
Hello
PS C:\> Use-Transaction -TransactedScript { $transactedString.ToString() } -UseTransaction
Hello, World
PS C:\> Complete-Transaction
PS C:\> $transactedString.ToString()
Hello, World
```

Cet exemple montre comment utiliser **use-transaction** pour écrire des scripts sur un objet de .NET Framework à transaction activée.
Dans ce cas, l’objet est un objet **TransactedString** .

La première commande utilise l’applet de commande Start-Transaction pour démarrer une transaction.

La deuxième commande utilise la commande New-Object pour créer un objet **TransactedString** .
Elle stocke l’objet dans la variable $TransactedString.

Les troisième et quatrième commandes utilisent la méthode **Append** de l’objet **TransactedString** pour ajouter du texte à la valeur de $TransactedString.
Une commande fait partie de la transaction.
L’autre commande n’est pas.

La troisième commande utilise la méthode **Append** de la chaîne traitée pour ajouter Hello à la valeur de $TransactedString.
Comme la commande ne fait pas partie de la transaction, la modification est immédiatement appliquée.

La quatrième commande utilise **use-transaction** pour ajouter du texte à la chaîne dans la transaction.
La commande utilise la méthode **Append** pour ajouter « , World » à la valeur de $TransactedString.
La commande est placée entre accolades ( {} ) pour en faire un bloc de script.
Le paramètre *UseTransaction* est obligatoire dans cette commande.

Les cinquième et sixième commandes utilisent la méthode **ToString** de l’objet **TransactedString** pour afficher la valeur de **TransactedString** sous la forme d’une chaîne.
Là encore, une commande fait partie de la transaction.
L’autre transaction n’est pas.

La cinquième commande utilise la méthode **ToString** pour afficher la valeur actuelle de la variable $TransactedString.
Comme elle ne fait pas partie de la transaction, elle n’affiche que l’état actuel de la chaîne.

La sixième commande utilise **use-transaction** pour exécuter la même commande dans la transaction.
Étant donné que la commande fait partie de la transaction, elle affiche la valeur actuelle de la chaîne dans la transaction, comme un aperçu des modifications apportées à la transaction.

La septième commande utilise l’applet de commande Complete-Transaction pour valider la transaction.

La dernière commande utilise la méthode **ToString** pour afficher la valeur résultante de la variable sous la forme d’une chaîne.

### Exemple 2 : restaurer une transaction

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> Undo-Transaction
PS C:\> $transactedString.ToString()
Hello
```

Cet exemple montre l’effet de la restauration d’une transaction qui comprend des commandes **use-transaction** .
Comme pour toutes les commandes d’une transaction, lorsque la transaction est restaurée, les modifications basées sur les transactions sont ignorées et les données restent inchangées.

La première commande utilise **start-transaction** pour démarrer une transaction.

La deuxième commande utilise **New-Object** pour créer un objet **TransactedString** .
Elle stocke l’objet dans la variable $TransactedString.

La troisième commande, qui ne fait pas partie de la transaction, utilise la méthode **Append** pour ajouter « Hello » à la valeur de $TransactedString.

La quatrième commande utilise **use-transaction** pour exécuter une autre commande qui utilise la méthode **Append** dans la transaction.
La commande utilise la méthode **Append** pour ajouter « , World » à la valeur de $TransactedString.

La cinquième commande utilise l’applet de commande Undo-Transaction pour restaurer la transaction.
Par conséquent, toutes les commandes exécutées dans la transaction sont inversées.

La dernière commande utilise la méthode **ToString** pour afficher la valeur résultante de $TransactedString sous forme de chaîne.
Les résultats indiquent que seules les modifications apportées en dehors de la transaction ont été appliquées à l’objet.

## PARAMETERS

### -TransactedScript
Spécifie le bloc de script qui est exécuté dans la transaction.
Entrez un bloc de script valide entre accolades ( { } ).
Ce paramètre est obligatoire.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseTransaction
Inclut la commande dans la transaction active.
Ce paramètre est uniquement valide au cours d’une transaction.
Pour plus d’informations, consultez about_transactions.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

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

### PSObject
Cette applet de commande retourne le résultat de la transaction.

## REMARQUES

* Le paramètre *UseTransaction* comprend la commande dans la transaction active. Étant donné que l’applet de commande **use-transaction** est toujours utilisée dans les transactions, ce paramètre est requis pour rendre l’utilisation de la commande **use-transaction** effective.

*

## LIENS CONNEXES

[Complete-Transaction](Complete-Transaction.md)

[Get-Transaction](Get-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)
