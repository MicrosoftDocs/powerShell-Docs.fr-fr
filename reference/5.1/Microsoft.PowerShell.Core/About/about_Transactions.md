---
description: Décrit comment gérer les opérations traitées dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_transactions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Transactions
ms.openlocfilehash: 522e0f727754b0b0153571039f3bf3966d0abf20
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207526"
---
# <a name="about-transactions"></a>À propos des transactions

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit comment gérer les opérations traitées dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les transactions sont prises en charge dans PowerShell à compter de PowerShell 2,0. Cette fonctionnalité vous permet de démarrer une transaction, d’indiquer les commandes faisant partie de la transaction et de valider ou d’annuler une transaction.

## <a name="about-transactions"></a>À PROPOS DES TRANSACTIONS

Dans PowerShell, une transaction est un ensemble d’une ou plusieurs commandes qui sont gérées en tant qu’unité logique. Une transaction peut être exécutée (« validée »), ce qui modifie les données affectées par la transaction. Ou bien, une transaction peut être complètement annulée (« restaurée ») afin que les données affectées ne soient pas modifiées par la transaction.

Étant donné que les commandes d’une transaction sont gérées en tant qu’unité, toutes les commandes sont validées, ou toutes les commandes sont restaurées.

Les transactions sont largement utilisées dans le traitement des données, notamment dans les opérations de base de données et les transactions financières. Les transactions sont le plus souvent utilisées lorsque le pire scénario d’un ensemble de commandes n’est pas qu’elles échouent, mais que certaines commandes réussissent et que d’autres échouent, laissant le système dans un état endommagé, faux ou non interprétable, difficile à réparer.

## <a name="transaction-cmdlets"></a>APPLETS DE COMMANDE DE TRANSACTION

PowerShell comprend plusieurs applets de commande conçues pour gérer les transactions.

- Start-transaction : démarre une nouvelle transaction.
- Use-transaction : ajoute une commande ou une expression à la transaction. La commande doit utiliser des objets à transaction activée.
- Undo-Transaction : restaure la transaction afin qu’aucune donnée ne soit modifiée par la transaction.
- Complete-transaction : valide la transaction. Les données affectées par la transaction sont modifiées.
- Obtenir une transaction : obtient des informations sur la transaction active.

Pour obtenir la liste des applets de commande de transaction, tapez :

```powershell
get-command *transaction
```

Pour plus d’informations sur les applets de commande, tapez :

```powershell
get-help use-transaction -detailed
```

## <a name="transaction-enabled-elements"></a>ÉLÉMENTS ACTIVÉS POUR LES TRANSACTIONS

Pour participer à une transaction, l’applet de commande et le fournisseur doivent tous deux prendre en charge les transactions. Cette fonctionnalité est intégrée aux objets qui sont affectés par la transaction.

Le fournisseur Registry PowerShell prend en charge les transactions dans Windows Vista. L’objet TransactedString (Microsoft. PowerShell. Commands. Management. TransactedString) fonctionne avec tout système d’exploitation qui exécute PowerShell.

Les autres fournisseurs PowerShell peuvent prendre en charge les transactions. Pour rechercher les fournisseurs PowerShell dans votre session qui prennent en charge les transactions, utilisez la commande suivante pour rechercher la valeur « transactions » dans la propriété capacités des fournisseurs :

```powershell
get-psprovider | where {$_.Capabilities -like "*transactions*"}
```

Pour plus d’informations sur un fournisseur, reportez-vous à l’aide du fournisseur. Pour obtenir de l’aide sur le fournisseur, tapez :

```
get-help <provider-name>
```

Par exemple, pour obtenir de l’aide sur le fournisseur de Registre, tapez :

```powershell
get-help registry
```

## <a name="the-usetransaction-parameter"></a>PARAMÈTRE USETRANSACTION

Les applets de commande qui peuvent prendre en charge les transactions ont un paramètre UseTransaction. Ce paramètre comprend la commande dans la transaction active. Vous pouvez utiliser le nom de paramètre complet ou son alias, « UseTX ».

Le paramètre ne peut être utilisé que lorsque la session contient une transaction active. Si vous entrez une commande avec le paramètre UseTransaction alors qu’il n’y a aucune transaction active, la commande échoue.

Pour rechercher des applets de commande avec le paramètre UseTransaction, tapez :

```powershell
get-help * -parameter UseTransaction
```

Dans PowerShell Core, toutes les applets de commande conçues pour fonctionner avec des fournisseurs PowerShell prennent en charge les transactions. Par conséquent, vous pouvez utiliser les applets de commande du fournisseur pour gérer les transactions.

Pour plus d’informations sur les fournisseurs PowerShell, consultez [about_Providers](about_Providers.md).

## <a name="the-transaction-object"></a>OBJET DE TRANSACTION

Les transactions sont représentées dans PowerShell par un objet de transaction, System. Management. Automation. transaction.

L'objet a les propriétés suivantes :

- RollbackPreference : contient les préférences de restauration définies pour la transaction en cours. Vous pouvez définir la préférence de restauration lorsque vous utilisez Start-Transaction pour démarrer la transaction.

  La préférence de restauration détermine les conditions dans lesquelles la transaction est restaurée automatiquement. Les valeurs valides sont Error, TerminatingError et Never. La valeur par défaut est Error.

- État : contient l’état actuel de la transaction. Les valeurs valides sont active, validée et valeur RolledBack.

- SubscriberCount : contient le nombre d’abonnés à la transaction. Un abonné est ajouté à une transaction lorsque vous démarrez une transaction alors qu’une autre transaction est en cours. Le nombre d’abonnés est décrémenté lorsqu’un abonné valide la transaction.

## <a name="active-transactions"></a>TRANSACTIONS ACTIVES

Dans PowerShell, une seule transaction est active à la fois et vous ne pouvez gérer que la transaction active. Plusieurs transactions peuvent être en cours dans la même session en même temps, mais seule la transaction la plus récemment démarrée est active.

Par conséquent, vous ne pouvez pas spécifier une transaction particulière lorsque vous utilisez les applets de commande de transaction. Les commandes s’appliquent toujours à la transaction active.

Cela est le plus évident dans le comportement de l’applet de commande Get-Transaction. Lorsque vous entrez une commande Get-Transaction, Get-Transaction obtient toujours qu’un seul objet de transaction. Cet objet est l’objet qui représente la transaction active.

Pour gérer une autre transaction, vous devez d’abord terminer la transaction active, soit en la validant, soit en la restaurant de nouveau. Dans ce cas, la transaction précédente devient active automatiquement. Les transactions sont actives dans l’ordre inverse de leur démarrage, de sorte que la dernière transaction démarrée est toujours active.

## <a name="subscribers-and-independent-transactions"></a>ABONNÉS ET TRANSACTIONS INDÉPENDANTES

Si vous démarrez une transaction alors qu’une autre transaction est en cours, par défaut, PowerShell ne démarre pas une nouvelle transaction. Au lieu de cela, il ajoute un « abonné » à la transaction en cours.

Lorsqu’une transaction a plusieurs abonnés, une seule commande Undo-Transaction à tout moment annule l’intégralité de la transaction pour tous les abonnés. Toutefois, pour valider la transaction, vous devez entrer une commande Complete-Transaction pour chaque abonné.

Pour rechercher le nombre d’abonnés à une transaction, vérifiez la propriété SubscriberCount de l’objet transaction. Par exemple, la commande suivante utilise l’applet de commande Get-Transaction pour obtenir la valeur de la propriété SubscriberCount de la transaction active :

```powershell
(Get-Transaction).SubscriberCount
```

L’ajout d’un abonné est le comportement par défaut, car la plupart des transactions qui sont démarrées alors qu’une autre transaction est en cours sont liées à la transaction d’origine. Dans le modèle classique, un script qui contient une transaction appelle un script d’assistance qui contient sa propre transaction. Étant donné que les transactions sont liées, elles doivent être restaurées ou validées en tant qu’unité.

Toutefois, vous pouvez démarrer une transaction qui est indépendante de la transaction actuelle à l’aide du paramètre Independent de l’applet de commande Start-Transaction.

Lorsque vous démarrez une transaction indépendante, Start-Transaction crée un nouvel objet de transaction et la nouvelle transaction devient la transaction active.
La transaction indépendante peut être validée ou restaurée sans affecter la transaction d’origine.

Lorsque la transaction indépendante est terminée (validée ou restaurée), la transaction d’origine redevient la transaction active.

## <a name="changing-data"></a>MODIFICATION DES DONNÉES

Lorsque vous utilisez des transactions pour modifier des données, les données affectées par la transaction ne sont pas modifiées tant que vous n’avez pas validé la transaction. Toutefois, les mêmes données peuvent être modifiées par des commandes qui ne font pas partie de la transaction.

Gardez cela à l’esprit lorsque vous utilisez des transactions pour gérer des données partagées.
En règle générale, les bases de données possèdent des mécanismes qui verrouillent les données pendant que vous les utilisez, ce qui empêche les autres utilisateurs, ainsi que d’autres commandes, scripts et fonctions, de les modifier.

Toutefois, le verrou est une fonctionnalité de la base de données. Elle n’est pas liée aux transactions. Si vous travaillez dans un système de fichiers basé sur des transactions ou dans un autre magasin de données, les données peuvent être modifiées pendant que la transaction est en cours.

## <a name="examples"></a>EXEMPLES

Les exemples de cette section utilisent le fournisseur de Registre PowerShell et supposent que vous êtes familiarisé avec celui-ci. Pour plus d’informations sur le fournisseur de Registre, tapez « obtenir-help registry ».

### <a name="example-1-committing-a-transaction"></a>EXEMPLE 1 : VALIDATION D’UNE TRANSACTION

Pour créer une transaction, utilisez l’applet de commande Start-Transaction. La commande suivante démarre une transaction avec les paramètres par défaut.

```powershell
start-transaction
```

Pour inclure des commandes dans la transaction, utilisez le paramètre UseTransaction de l’applet de commande. Par défaut, les commandes ne sont pas incluses dans la transaction.

Par exemple, la commande suivante, qui définit l’emplacement actuel dans la clé logicielle du lecteur HKCU :, n’est pas incluse dans la transaction.

```powershell
cd hkcu:\Software
```

La commande suivante, qui crée la clé MyCompany, utilise le paramètre UseTransaction de l’applet de commande New-Item pour inclure la commande dans la transaction active.

```powershell
new-item MyCompany -UseTransaction
```

La commande retourne un objet qui représente la nouvelle clé, mais comme la commande fait partie de la transaction, le registre n’est pas encore modifié.

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyCompany                      {}
```

Pour valider la transaction, utilisez l’applet de commande Complete-Transaction. Étant donné qu’elle affecte toujours la transaction active, vous ne pouvez pas spécifier la transaction.

```powershell
complete-transaction
```

La clé MyCompany est donc ajoutée au registre.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-2-rolling-back-a-transaction"></a>EXEMPLE 2 : RESTAURATION D’UNE TRANSACTION

Pour créer une transaction, utilisez l’applet de commande Start-Transaction. La commande suivante démarre une transaction avec les paramètres par défaut.

```powershell
start-transaction
```

La commande suivante, qui crée la clé MyOtherCompany, utilise le paramètre UseTransaction de l’applet de commande New-Item pour inclure la commande dans la transaction active.

```powershell
new-item MyOtherCompany -UseTransaction
```

La commande retourne un objet qui représente la nouvelle clé, mais comme la commande fait partie de la transaction, le registre n’est pas encore modifié.

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyOtherCompany                 {}
```

Pour restaurer la transaction, utilisez l’applet de commande Undo-Transaction. Étant donné qu’elle affecte toujours la transaction active, vous ne spécifiez pas la transaction.

```powershell
Undo-transaction
```

Le résultat est que la clé MyOtherCompany n’est pas ajoutée au registre.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-3-previewing-a-transaction"></a>EXEMPLE 3 : APERÇU D’UNE TRANSACTION

En règle générale, les commandes utilisées dans une transaction changent de données. Toutefois, les commandes qui obtiennent des données sont également utiles dans une transaction, car elles obtiennent des données à l’intérieur de la transaction. Cela permet d’obtenir un aperçu des modifications qui sont à l’origine de la validation de la transaction.

L’exemple suivant montre comment utiliser la commande Get-ChildItem (l’alias est « dir ») pour afficher un aperçu des modifications apportées à une transaction.

La commande suivante démarre une transaction.

```powershell
start-transaction
```

La commande suivante utilise l’applet de commande New-ItemProperty pour ajouter l’entrée de Registre MyKey à la clé MyCompany. La commande utilise le paramètre UseTransaction pour inclure la commande dans la transaction.

```powershell
new-itemproperty -path MyCompany -Name MyKey -value 123 -UseTransaction
```

La commande retourne un objet représentant la nouvelle entrée de Registre, mais l’entrée de Registre n’est pas modifiée.

```
MyKey
-----
123
```

Pour obtenir les éléments qui se trouvent actuellement dans le registre, utilisez une commande Get-ChildItem (« dir ») sans le paramètre UseTransaction. La commande suivante obtient les éléments qui commencent par « M ».

```powershell
dir m*
```

Le résultat indique qu’aucune entrée n’a encore été ajoutée à la clé MyCompany.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

Pour afficher un aperçu de l’effet de la validation de la transaction, entrez une commande Get-ChildItem (« dir ») avec le paramètre UseTransaction. Cette commande a une vue des données à partir de la transaction.

```powershell
dir m* -useTransaction
```

Le résultat indique que, si la transaction est validée, l’entrée MyKey est ajoutée à la clé MyCompany.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   1 MyCompany                      {MyKey}
```

### <a name="example-4-combining-transacted-and-non-transacted-commands"></a>EXEMPLE 4 : COMBINAISON DE COMMANDES TRANSACTIONNELLES ET NON TRANSACTIONNELLES

Vous pouvez entrer des commandes non transactionnelles au cours d’une transaction. Les commandes non transactionnelles affectent immédiatement les données, mais elles n’affectent pas la transaction.
La commande suivante démarre une transaction dans la clé de Registre HKCU : \ Software.

```powershell
start-transaction
```

Les trois commandes suivantes utilisent l’applet de commande New-Item pour ajouter des clés au registre.
La première et la troisième commande utilisent le paramètre UseTransaction pour inclure les commandes dans la transaction. La deuxième commande omet le paramètre. Étant donné que la deuxième commande n’est pas incluse dans la transaction, elle est immédiatement effective.

```powershell
new-item MyCompany1 -UseTransaction
new-item MyCompany2
new-item MyCompany3 -UseTransaction
```

Pour afficher l’état actuel du Registre, utilisez une commande Get-ChildItem (« dir ») sans le paramètre UseTransaction. Cette commande obtient les éléments qui commencent par « M ».

```powershell
dir m*
```

Le résultat indique que la clé MyCompany2 est ajoutée au registre, mais que les clés MyCompany1 et MyCompany3, qui font partie de la transaction, ne sont pas ajoutées.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0    0 MyCompany2                     {}
```

La commande suivante valide la transaction.

```powershell
complete-transaction
```

À présent, les clés ajoutées dans le cadre de la transaction s’affichent dans le registre.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
83   1 Microsoft                      {(default)}
0    0 MyCompany1                     {}
0    0 MyCompany2                     {}
0    0 MyCompany3                     {}
```

### <a name="example-5-using-automatic-rollback"></a>EXEMPLE 5 : UTILISATION DE LA RESTAURATION AUTOMATIQUE

Quand une commande dans une transaction génère une erreur de n’importe quel type, la transaction est automatiquement restaurée.

Ce comportement par défaut est conçu pour les scripts qui exécutent des transactions. Les scripts sont généralement testés correctement et incluent une logique de gestion des erreurs, de sorte que les erreurs ne sont pas attendues et doivent mettre fin à la transaction.

La première commande démarre une transaction dans la clé de Registre HKCU : \ Software.

```powershell
start-transaction
```

La commande suivante utilise l’applet de commande New-Item pour ajouter la clé MyCompany au registre. La commande utilise le paramètre UseTransaction (l’alias est « UseTX ») pour inclure la commande dans la transaction.

```powershell
New-Item MyCompany -UseTX
```

Étant donné que la clé MyCompany existe déjà dans le registre, la commande échoue et la transaction est restaurée.

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

Une commande Get-Transaction confirme que la transaction a été restaurée et que SubscriberCount est égal à 0.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 RolledBack
```

### <a name="example-6-changing-the-rollback-preference"></a>EXEMPLE 6 : MODIFICATION DE LA PRÉFÉRENCE DE RESTAURATION

Si vous souhaitez que la transaction soit plus tolérante aux erreurs, vous pouvez utiliser le paramètre RollbackPreference de Start-Transaction pour modifier la préférence.

La commande suivante démarre une transaction avec une préférence de restauration « Never ».

```powershell
start-transaction -rollbackpreference Never
```

Dans ce cas, lorsque la commande échoue, la transaction n’est pas automatiquement restaurée.

```powershell
New-Item MyCompany -UseTX
```

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

Étant donné que la transaction est toujours active, vous pouvez soumettre à nouveau la commande dans le cadre de la transaction.

```powershell
New-Item MyOtherCompany -UseTX
```

### <a name="example-7-using-the-use-transaction-cmdlet"></a>EXEMPLE 7 : UTILISATION DE L’APPLET DE COMMANDE USE-TRANSACTION

L’applet de commande Use-Transaction vous permet d’effectuer des scripts directs sur les objets de l’infrastructure de Microsoft .NET de transaction. Use-Transaction accepte un bloc de script qui ne peut contenir que des commandes et des expressions qui utilisent des objets de .NET Framework à transaction activée, tels que des instances de la classe Microsoft. PowerShell. Commands. Management. TransactedString.

La commande suivante démarre une transaction.

```powershell
start-transaction
```

La commande New-Object suivante crée une instance de la classe TransactedString et l’enregistre dans la variable $t.

```powershell
$t = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
```

La commande suivante utilise la méthode Append de l’objet TransactedString pour ajouter du texte à la chaîne. Étant donné que la commande ne fait pas partie de la transaction, la modification est immédiatement effective.

```powershell
$t.append("Windows")
```

La commande suivante utilise la même méthode Append pour ajouter du texte, mais elle ajoute le texte dans le cadre de la transaction. La commande est placée entre accolades et est définie comme valeur du paramètre ScriptBlock de use-transaction. Le paramètre UseTransaction (UseTx) est requis.

```powershell
use-transaction {$t.append(" PowerShell")} -usetx
```

Pour afficher le contenu actuel de la chaîne traitée dans $t, utilisez la méthode ToString de l’objet TransactedString.

```powershell
$t.tostring()
```

La sortie indique que seules les modifications non transactionnelles sont effectives.

```output
Windows
```

Pour afficher le contenu actuel de la chaîne traitée dans $t à partir de la transaction, incorporez l’expression dans une commande Use-Transaction.

```powershell
use-transaction {$s.tostring()} -usetx
```

La sortie affiche la vue de la transaction.

```output
PowerShell
```

La commande suivante valide la transaction.

```powershell
complete-transaction
```

Pour afficher la chaîne finale :

```
$t.tostring()
PowerShell
```

### <a name="example-8-managing-multi-subscriber-transactions"></a>EXEMPLE 8 : GESTION DES TRANSACTIONS SUR PLUSIEURS ABONNÉS

Lorsque vous démarrez une transaction alors qu’une autre transaction est en cours, PowerShell ne crée pas de deuxième transaction par défaut. Au lieu de cela, il ajoute un abonné à la transaction en cours.

Cet exemple montre comment afficher et gérer une transaction multi-abonnés.

Commencez par démarrer une transaction dans la clé HKCU : \ Software.

```powershell
start-transaction
```

La commande suivante utilise la commande Get-Transaction pour récupérer la transaction active.

```powershell
get-transaction
```

Le résultat affiche l’objet qui représente la transaction active.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

La commande suivante ajoute la clé MyCompany au registre. La commande utilise le paramètre UseTransaction pour inclure la commande dans la transaction.

```powershell
new-item MyCompany -UseTransaction
```

La commande suivante utilise la commande Start-Transaction pour démarrer une transaction. Bien que cette commande soit tapée à l’invite de commandes, ce scénario est plus susceptible de se produire lorsque vous exécutez un script qui contient une transaction.

```powershell
start-transaction
```

Une commande Get-Transaction indique que le nombre d’abonnés sur l’objet transaction est incrémenté. La valeur est maintenant 2.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

La commande suivante utilise l’applet de commande New-ItemProperty pour ajouter l’entrée de Registre MyKey à la clé MyCompany. Elle utilise le paramètre UseTransaction pour inclure la commande dans la transaction.

```powershell
new-itemproperty -path MyCompany -name MyKey -UseTransaction
```

La clé MyCompany n’existe pas dans le registre, mais cette commande est réussie, car les deux commandes font partie de la même transaction.

La commande suivante valide la transaction. Si la transaction a été annulée, la transaction est restaurée pour tous les abonnés.

```powershell
complete-transaction
```

Une commande de Get-Transaction indique que le nombre d’abonnés sur l’objet de transaction est 1, mais la valeur de l’État est toujours active (non validée).

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Pour terminer la validation de la transaction, entrez une deuxième commande Complete-Transaction. Pour valider une transaction multi-abonné, vous devez entrer une commande Complete-Transaction pour chaque commande Start-Transaction.

```powershell
complete-transaction
```

Une autre commande de Get-Transaction indique que la transaction a été validée.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 Committed
```

### <a name="example-9-managing-independent-transactions"></a>EXEMPLE 9 : GESTION DES TRANSACTIONS INDÉPENDANTES

Lorsque vous démarrez une transaction pendant qu’une autre transaction est en cours, vous pouvez utiliser le paramètre Independent de Start-Transaction pour rendre la nouvelle transaction indépendante de la transaction d’origine.

Dans ce cas, Start-Transaction crée un nouvel objet de transaction et fait de la transaction active la nouvelle transaction.

Commencez par démarrer une transaction dans la clé HKCU : \\ Software.

```powershell
start-transaction
```

La commande suivante utilise la commande Get-Transaction pour récupérer la transaction active.

```powershell
get-transaction
```

Le résultat affiche l’objet qui représente la transaction active.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

La commande suivante ajoute la clé de Registre MyCompany dans le cadre de la transaction. Elle utilise le paramètre UseTransaction (UseTx) pour inclure la commande dans la transaction active.

```powershell
new-item MyCompany -use
```

La commande suivante démarre une nouvelle transaction. La commande utilise le paramètre Independent pour indiquer que cette transaction n’est pas un abonné à la transaction active.

```powershell
start-transaction -independent
```

Lorsque vous créez une transaction indépendante, la nouvelle transaction (la plus récemment créée) devient la transaction active. Vous pouvez utiliser une commande Get-Transaction pour obtenir la transaction active.

```powershell
get-transaction
```

Notez que le SubscriberCount de la transaction est 1, ce qui indique qu’il n’y a pas d’autres abonnés et que la transaction est nouvelle.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

La nouvelle transaction doit être terminée (validée ou restaurée) pour que vous puissiez gérer la transaction d’origine.

La commande suivante ajoute la clé MyOtherCompany au registre. Elle utilise le paramètre UseTransaction (UseTx) pour inclure la commande dans la transaction active.

```powershell
new-item MyOtherCompany -usetx
```

À présent, restaurez la transaction. S’il y avait une seule transaction avec deux abonnés, la restauration de la transaction restaurait la totalité de la transaction pour tous les abonnés.

Toutefois, étant donné que ces transactions sont indépendantes, la restauration de la dernière transaction annule les modifications apportées au registre et fait de la transaction d’origine la transaction active.

```powershell
undo-transaction
```

Une commande Get-Transaction confirme que la transaction d’origine est toujours active dans la session.

```powershell
get-transaction
```

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

La commande suivante valide la transaction active.

```powershell
complete-transaction
```

Une commande Get-ChildItem indique que le registre a été modifié.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

## <a name="see-also"></a>VOIR AUSSI

[Start-Transaction](xref:Microsoft.PowerShell.Management.Start-Transaction)

[Get-Transaction](xref:Microsoft.PowerShell.Management.Get-Transaction)

[Complete-Transaction](xref:Microsoft.PowerShell.Management.Complete-Transaction)

[Undo-Transaction](xref:Microsoft.PowerShell.Management.Undo-Transaction)

[Use-Transaction](xref:Microsoft.PowerShell.Management.Use-Transaction)

[Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

[about_Providers](about_Providers.md)
