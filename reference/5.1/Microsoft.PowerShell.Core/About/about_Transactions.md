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
# <a name="about-transactions"></a><span data-ttu-id="2ba71-104">À propos des transactions</span><span class="sxs-lookup"><span data-stu-id="2ba71-104">About Transactions</span></span>

## <a name="short-description"></a><span data-ttu-id="2ba71-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="2ba71-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="2ba71-106">Décrit comment gérer les opérations traitées dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ba71-106">Describes how to manage transacted operations in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="2ba71-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="2ba71-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="2ba71-108">Les transactions sont prises en charge dans PowerShell à compter de PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="2ba71-108">Transactions are supported in PowerShell beginning in PowerShell 2.0.</span></span> <span data-ttu-id="2ba71-109">Cette fonctionnalité vous permet de démarrer une transaction, d’indiquer les commandes faisant partie de la transaction et de valider ou d’annuler une transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-109">This feature enables you to start a transaction, to indicate which commands are part of the transaction, and to commit or roll back a transaction.</span></span>

## <a name="about-transactions"></a><span data-ttu-id="2ba71-110">À PROPOS DES TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="2ba71-110">ABOUT TRANSACTIONS</span></span>

<span data-ttu-id="2ba71-111">Dans PowerShell, une transaction est un ensemble d’une ou plusieurs commandes qui sont gérées en tant qu’unité logique.</span><span class="sxs-lookup"><span data-stu-id="2ba71-111">In PowerShell, a transaction is a set of one or more commands that are managed as a logical unit.</span></span> <span data-ttu-id="2ba71-112">Une transaction peut être exécutée (« validée »), ce qui modifie les données affectées par la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-112">A transaction can be completed ("committed"), which changes data affected by the transaction.</span></span> <span data-ttu-id="2ba71-113">Ou bien, une transaction peut être complètement annulée (« restaurée ») afin que les données affectées ne soient pas modifiées par la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-113">Or, a transaction can be completely undone ("rolled back") so that the affected data is not changed by the transaction.</span></span>

<span data-ttu-id="2ba71-114">Étant donné que les commandes d’une transaction sont gérées en tant qu’unité, toutes les commandes sont validées, ou toutes les commandes sont restaurées.</span><span class="sxs-lookup"><span data-stu-id="2ba71-114">Because the commands in a transaction are managed as a unit, either all commands are committed, or all commands are rolled back.</span></span>

<span data-ttu-id="2ba71-115">Les transactions sont largement utilisées dans le traitement des données, notamment dans les opérations de base de données et les transactions financières.</span><span class="sxs-lookup"><span data-stu-id="2ba71-115">Transactions are widely used in data processing, most notably in database operations and for financial transactions.</span></span> <span data-ttu-id="2ba71-116">Les transactions sont le plus souvent utilisées lorsque le pire scénario d’un ensemble de commandes n’est pas qu’elles échouent, mais que certaines commandes réussissent et que d’autres échouent, laissant le système dans un état endommagé, faux ou non interprétable, difficile à réparer.</span><span class="sxs-lookup"><span data-stu-id="2ba71-116">Transactions are most often used when the worst-case scenario for a set of commands is not that they all fail, but that some commands succeed while others fail, leaving the system in a damaged, false, or uninterpretable state that is difficult to repair.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="2ba71-117">APPLETS DE COMMANDE DE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="2ba71-117">TRANSACTION CMDLETS</span></span>

<span data-ttu-id="2ba71-118">PowerShell comprend plusieurs applets de commande conçues pour gérer les transactions.</span><span class="sxs-lookup"><span data-stu-id="2ba71-118">PowerShell includes several cmdlets designed for managing transactions.</span></span>

- <span data-ttu-id="2ba71-119">Start-transaction : démarre une nouvelle transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-119">Start-Transaction: Starts a new transaction.</span></span>
- <span data-ttu-id="2ba71-120">Use-transaction : ajoute une commande ou une expression à la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-120">Use-Transaction: Adds a command or expression to the transaction.</span></span> <span data-ttu-id="2ba71-121">La commande doit utiliser des objets à transaction activée.</span><span class="sxs-lookup"><span data-stu-id="2ba71-121">The command must use transaction-enabled objects.</span></span>
- <span data-ttu-id="2ba71-122">Undo-Transaction : restaure la transaction afin qu’aucune donnée ne soit modifiée par la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-122">Undo-Transaction: Rolls back the transaction so that no data is changed by the transaction.</span></span>
- <span data-ttu-id="2ba71-123">Complete-transaction : valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-123">Complete-Transaction: Commits the transaction.</span></span> <span data-ttu-id="2ba71-124">Les données affectées par la transaction sont modifiées.</span><span class="sxs-lookup"><span data-stu-id="2ba71-124">The data affected by the transaction is changed.</span></span>
- <span data-ttu-id="2ba71-125">Obtenir une transaction : obtient des informations sur la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-125">Get-Transaction: Gets information about the active transaction.</span></span>

<span data-ttu-id="2ba71-126">Pour obtenir la liste des applets de commande de transaction, tapez :</span><span class="sxs-lookup"><span data-stu-id="2ba71-126">For a list of transaction cmdlets, type:</span></span>

```powershell
get-command *transaction
```

<span data-ttu-id="2ba71-127">Pour plus d’informations sur les applets de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="2ba71-127">For detailed information about the cmdlets, type:</span></span>

```powershell
get-help use-transaction -detailed
```

## <a name="transaction-enabled-elements"></a><span data-ttu-id="2ba71-128">ÉLÉMENTS ACTIVÉS POUR LES TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="2ba71-128">TRANSACTION-ENABLED ELEMENTS</span></span>

<span data-ttu-id="2ba71-129">Pour participer à une transaction, l’applet de commande et le fournisseur doivent tous deux prendre en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="2ba71-129">To participate in a transaction, both the cmdlet and the provider must support transactions.</span></span> <span data-ttu-id="2ba71-130">Cette fonctionnalité est intégrée aux objets qui sont affectés par la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-130">This feature is built in to the objects that are affected by the transaction.</span></span>

<span data-ttu-id="2ba71-131">Le fournisseur Registry PowerShell prend en charge les transactions dans Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="2ba71-131">The PowerShell Registry provider supports transactions in Windows Vista.</span></span> <span data-ttu-id="2ba71-132">L’objet TransactedString (Microsoft. PowerShell. Commands. Management. TransactedString) fonctionne avec tout système d’exploitation qui exécute PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ba71-132">The TransactedString object (Microsoft.PowerShell.Commands.Management.TransactedString) works with any operating system that runs PowerShell.</span></span>

<span data-ttu-id="2ba71-133">Les autres fournisseurs PowerShell peuvent prendre en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="2ba71-133">Other PowerShell providers can support transactions.</span></span> <span data-ttu-id="2ba71-134">Pour rechercher les fournisseurs PowerShell dans votre session qui prennent en charge les transactions, utilisez la commande suivante pour rechercher la valeur « transactions » dans la propriété capacités des fournisseurs :</span><span class="sxs-lookup"><span data-stu-id="2ba71-134">To find the PowerShell providers in your session that support transactions, use the following command to find the "Transactions" value in the Capabilities property of providers:</span></span>

```powershell
get-psprovider | where {$_.Capabilities -like "*transactions*"}
```

<span data-ttu-id="2ba71-135">Pour plus d’informations sur un fournisseur, reportez-vous à l’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="2ba71-135">For more information about a provider, see the Help for the provider.</span></span> <span data-ttu-id="2ba71-136">Pour obtenir de l’aide sur le fournisseur, tapez :</span><span class="sxs-lookup"><span data-stu-id="2ba71-136">To get provider Help, type:</span></span>

```
get-help <provider-name>
```

<span data-ttu-id="2ba71-137">Par exemple, pour obtenir de l’aide sur le fournisseur de Registre, tapez :</span><span class="sxs-lookup"><span data-stu-id="2ba71-137">For example, to get Help for the Registry provider, type:</span></span>

```powershell
get-help registry
```

## <a name="the-usetransaction-parameter"></a><span data-ttu-id="2ba71-138">PARAMÈTRE USETRANSACTION</span><span class="sxs-lookup"><span data-stu-id="2ba71-138">THE USETRANSACTION PARAMETER</span></span>

<span data-ttu-id="2ba71-139">Les applets de commande qui peuvent prendre en charge les transactions ont un paramètre UseTransaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-139">Cmdlets that can support transactions have a UseTransaction parameter.</span></span> <span data-ttu-id="2ba71-140">Ce paramètre comprend la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-140">This parameter includes the command in the active transaction.</span></span> <span data-ttu-id="2ba71-141">Vous pouvez utiliser le nom de paramètre complet ou son alias, « UseTX ».</span><span class="sxs-lookup"><span data-stu-id="2ba71-141">You can use the full parameter name or its alias, "usetx".</span></span>

<span data-ttu-id="2ba71-142">Le paramètre ne peut être utilisé que lorsque la session contient une transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-142">The parameter can be used only when the session contains an active transaction.</span></span> <span data-ttu-id="2ba71-143">Si vous entrez une commande avec le paramètre UseTransaction alors qu’il n’y a aucune transaction active, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="2ba71-143">If you enter a command with the UseTransaction parameter when there is no active transaction, the command fails.</span></span>

<span data-ttu-id="2ba71-144">Pour rechercher des applets de commande avec le paramètre UseTransaction, tapez :</span><span class="sxs-lookup"><span data-stu-id="2ba71-144">To find cmdlets with the UseTransaction parameter, type:</span></span>

```powershell
get-help * -parameter UseTransaction
```

<span data-ttu-id="2ba71-145">Dans PowerShell Core, toutes les applets de commande conçues pour fonctionner avec des fournisseurs PowerShell prennent en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="2ba71-145">In PowerShell core, all of the cmdlets designed to work with PowerShell providers support transactions.</span></span> <span data-ttu-id="2ba71-146">Par conséquent, vous pouvez utiliser les applets de commande du fournisseur pour gérer les transactions.</span><span class="sxs-lookup"><span data-stu-id="2ba71-146">As a result, you can use the provider cmdlets to manage transactions.</span></span>

<span data-ttu-id="2ba71-147">Pour plus d’informations sur les fournisseurs PowerShell, consultez [about_Providers](about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="2ba71-147">For more information about PowerShell providers, see [about_Providers](about_Providers.md).</span></span>

## <a name="the-transaction-object"></a><span data-ttu-id="2ba71-148">OBJET DE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="2ba71-148">THE TRANSACTION OBJECT</span></span>

<span data-ttu-id="2ba71-149">Les transactions sont représentées dans PowerShell par un objet de transaction, System. Management. Automation. transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-149">Transactions are represented in PowerShell by a transaction object, System.Management.Automation.Transaction.</span></span>

<span data-ttu-id="2ba71-150">L'objet a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ba71-150">The object has the following properties:</span></span>

- <span data-ttu-id="2ba71-151">RollbackPreference : contient les préférences de restauration définies pour la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="2ba71-151">RollbackPreference: Contains the rollback preference set for the current transaction.</span></span> <span data-ttu-id="2ba71-152">Vous pouvez définir la préférence de restauration lorsque vous utilisez Start-Transaction pour démarrer la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-152">You can set the rollback preference when you use Start-Transaction to start the transaction.</span></span>

  <span data-ttu-id="2ba71-153">La préférence de restauration détermine les conditions dans lesquelles la transaction est restaurée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="2ba71-153">The rollback preference determines the conditions under which the transaction is rolled back automatically.</span></span> <span data-ttu-id="2ba71-154">Les valeurs valides sont Error, TerminatingError et Never.</span><span class="sxs-lookup"><span data-stu-id="2ba71-154">Valid values are Error, TerminatingError, and Never.</span></span> <span data-ttu-id="2ba71-155">La valeur par défaut est Error.</span><span class="sxs-lookup"><span data-stu-id="2ba71-155">The default value is Error.</span></span>

- <span data-ttu-id="2ba71-156">État : contient l’état actuel de la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-156">Status: Contains the current status of the transaction.</span></span> <span data-ttu-id="2ba71-157">Les valeurs valides sont active, validée et valeur RolledBack.</span><span class="sxs-lookup"><span data-stu-id="2ba71-157">Valid values are Active, Committed, and RolledBack.</span></span>

- <span data-ttu-id="2ba71-158">SubscriberCount : contient le nombre d’abonnés à la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-158">SubscriberCount: Contains the number of subscribers to the transaction.</span></span> <span data-ttu-id="2ba71-159">Un abonné est ajouté à une transaction lorsque vous démarrez une transaction alors qu’une autre transaction est en cours.</span><span class="sxs-lookup"><span data-stu-id="2ba71-159">A subscriber is added to a transaction when you start a transaction while another transaction is in progress.</span></span> <span data-ttu-id="2ba71-160">Le nombre d’abonnés est décrémenté lorsqu’un abonné valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-160">The subscriber count is decremented when a subscriber commits the transaction.</span></span>

## <a name="active-transactions"></a><span data-ttu-id="2ba71-161">TRANSACTIONS ACTIVES</span><span class="sxs-lookup"><span data-stu-id="2ba71-161">ACTIVE TRANSACTIONS</span></span>

<span data-ttu-id="2ba71-162">Dans PowerShell, une seule transaction est active à la fois et vous ne pouvez gérer que la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-162">In PowerShell, only one transaction is active at a time, and you can manage only the active transaction.</span></span> <span data-ttu-id="2ba71-163">Plusieurs transactions peuvent être en cours dans la même session en même temps, mais seule la transaction la plus récemment démarrée est active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-163">Multiple transactions can be in progress in the same session at the same time, but only the most-recently started transaction is active.</span></span>

<span data-ttu-id="2ba71-164">Par conséquent, vous ne pouvez pas spécifier une transaction particulière lorsque vous utilisez les applets de commande de transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-164">As a result, you cannot specify a particular transaction when using the transaction cmdlets.</span></span> <span data-ttu-id="2ba71-165">Les commandes s’appliquent toujours à la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-165">Commands always apply to the active transaction.</span></span>

<span data-ttu-id="2ba71-166">Cela est le plus évident dans le comportement de l’applet de commande Get-Transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-166">This is most evident in the behavior of the Get-Transaction cmdlet.</span></span> <span data-ttu-id="2ba71-167">Lorsque vous entrez une commande Get-Transaction, Get-Transaction obtient toujours qu’un seul objet de transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-167">When you enter a Get-Transaction command, Get-Transaction always gets only one transaction object.</span></span> <span data-ttu-id="2ba71-168">Cet objet est l’objet qui représente la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-168">This object is the object that represents the active transaction.</span></span>

<span data-ttu-id="2ba71-169">Pour gérer une autre transaction, vous devez d’abord terminer la transaction active, soit en la validant, soit en la restaurant de nouveau.</span><span class="sxs-lookup"><span data-stu-id="2ba71-169">To manage a different transaction, you must first finish the active transaction, either by committing it or rolling it back.</span></span> <span data-ttu-id="2ba71-170">Dans ce cas, la transaction précédente devient active automatiquement.</span><span class="sxs-lookup"><span data-stu-id="2ba71-170">When you do this, the previous transaction becomes active automatically.</span></span> <span data-ttu-id="2ba71-171">Les transactions sont actives dans l’ordre inverse de leur démarrage, de sorte que la dernière transaction démarrée est toujours active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-171">Transactions become active in the reverse of order of which they are started, so that the most recently started transaction is always active.</span></span>

## <a name="subscribers-and-independent-transactions"></a><span data-ttu-id="2ba71-172">ABONNÉS ET TRANSACTIONS INDÉPENDANTES</span><span class="sxs-lookup"><span data-stu-id="2ba71-172">SUBSCRIBERS AND INDEPENDENT TRANSACTIONS</span></span>

<span data-ttu-id="2ba71-173">Si vous démarrez une transaction alors qu’une autre transaction est en cours, par défaut, PowerShell ne démarre pas une nouvelle transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-173">If you start a transaction while another transaction is in progress, by default, PowerShell does not start a new transaction.</span></span> <span data-ttu-id="2ba71-174">Au lieu de cela, il ajoute un « abonné » à la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="2ba71-174">Instead, it adds a "subscriber" to the current transaction.</span></span>

<span data-ttu-id="2ba71-175">Lorsqu’une transaction a plusieurs abonnés, une seule commande Undo-Transaction à tout moment annule l’intégralité de la transaction pour tous les abonnés.</span><span class="sxs-lookup"><span data-stu-id="2ba71-175">When a transaction has multiple subscribers, a single Undo-Transaction command at any point rolls back the entire transaction for all subscribers.</span></span> <span data-ttu-id="2ba71-176">Toutefois, pour valider la transaction, vous devez entrer une commande Complete-Transaction pour chaque abonné.</span><span class="sxs-lookup"><span data-stu-id="2ba71-176">However, to commit the transaction, you must enter a Complete-Transaction command for every subscriber.</span></span>

<span data-ttu-id="2ba71-177">Pour rechercher le nombre d’abonnés à une transaction, vérifiez la propriété SubscriberCount de l’objet transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-177">To find the number of subscribers to a transaction, check the SubscriberCount property of the transaction object.</span></span> <span data-ttu-id="2ba71-178">Par exemple, la commande suivante utilise l’applet de commande Get-Transaction pour obtenir la valeur de la propriété SubscriberCount de la transaction active :</span><span class="sxs-lookup"><span data-stu-id="2ba71-178">For example, the following command uses the Get-Transaction cmdlet to get the value of the SubscriberCount property of the active transaction:</span></span>

```powershell
(Get-Transaction).SubscriberCount
```

<span data-ttu-id="2ba71-179">L’ajout d’un abonné est le comportement par défaut, car la plupart des transactions qui sont démarrées alors qu’une autre transaction est en cours sont liées à la transaction d’origine.</span><span class="sxs-lookup"><span data-stu-id="2ba71-179">Adding a subscriber is the default behavior because most transactions that are started while another transaction is in progress are related to the original transaction.</span></span> <span data-ttu-id="2ba71-180">Dans le modèle classique, un script qui contient une transaction appelle un script d’assistance qui contient sa propre transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-180">In the typical model, a script that contains a transaction calls a helper script that contains its own transaction.</span></span> <span data-ttu-id="2ba71-181">Étant donné que les transactions sont liées, elles doivent être restaurées ou validées en tant qu’unité.</span><span class="sxs-lookup"><span data-stu-id="2ba71-181">Because the transactions are related, they should be rolled back or committed as a unit.</span></span>

<span data-ttu-id="2ba71-182">Toutefois, vous pouvez démarrer une transaction qui est indépendante de la transaction actuelle à l’aide du paramètre Independent de l’applet de commande Start-Transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-182">However, you can start a transaction that is independent of the current transaction by using the Independent parameter of the Start-Transaction cmdlet.</span></span>

<span data-ttu-id="2ba71-183">Lorsque vous démarrez une transaction indépendante, Start-Transaction crée un nouvel objet de transaction et la nouvelle transaction devient la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-183">When you start an independent transaction, Start-Transaction creates a new transaction object, and the new transaction becomes the active transaction.</span></span>
<span data-ttu-id="2ba71-184">La transaction indépendante peut être validée ou restaurée sans affecter la transaction d’origine.</span><span class="sxs-lookup"><span data-stu-id="2ba71-184">The independent transaction can be committed or rolled back without affecting the original transaction.</span></span>

<span data-ttu-id="2ba71-185">Lorsque la transaction indépendante est terminée (validée ou restaurée), la transaction d’origine redevient la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-185">When the independent transaction is finished (committed or rolled back), the original transaction becomes the active transaction again.</span></span>

## <a name="changing-data"></a><span data-ttu-id="2ba71-186">MODIFICATION DES DONNÉES</span><span class="sxs-lookup"><span data-stu-id="2ba71-186">CHANGING DATA</span></span>

<span data-ttu-id="2ba71-187">Lorsque vous utilisez des transactions pour modifier des données, les données affectées par la transaction ne sont pas modifiées tant que vous n’avez pas validé la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-187">When you use transactions to change data, the data that is affected by the transaction is not changed until you commit the transaction.</span></span> <span data-ttu-id="2ba71-188">Toutefois, les mêmes données peuvent être modifiées par des commandes qui ne font pas partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-188">However, the same data can be changed by commands that are not part of the transaction.</span></span>

<span data-ttu-id="2ba71-189">Gardez cela à l’esprit lorsque vous utilisez des transactions pour gérer des données partagées.</span><span class="sxs-lookup"><span data-stu-id="2ba71-189">Keep this in mind when you are using transactions to manage shared data.</span></span>
<span data-ttu-id="2ba71-190">En règle générale, les bases de données possèdent des mécanismes qui verrouillent les données pendant que vous les utilisez, ce qui empêche les autres utilisateurs, ainsi que d’autres commandes, scripts et fonctions, de les modifier.</span><span class="sxs-lookup"><span data-stu-id="2ba71-190">Typically, databases have mechanisms that lock the data while you are working on it, preventing other users, and other commands, scripts, and functions, from changing it.</span></span>

<span data-ttu-id="2ba71-191">Toutefois, le verrou est une fonctionnalité de la base de données.</span><span class="sxs-lookup"><span data-stu-id="2ba71-191">However, the lock is a feature of the database.</span></span> <span data-ttu-id="2ba71-192">Elle n’est pas liée aux transactions.</span><span class="sxs-lookup"><span data-stu-id="2ba71-192">It is not related to transactions.</span></span> <span data-ttu-id="2ba71-193">Si vous travaillez dans un système de fichiers basé sur des transactions ou dans un autre magasin de données, les données peuvent être modifiées pendant que la transaction est en cours.</span><span class="sxs-lookup"><span data-stu-id="2ba71-193">If you are working in a transaction-enabled file system or other data store, the data can be changed while the transaction is in progress.</span></span>

## <a name="examples"></a><span data-ttu-id="2ba71-194">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="2ba71-194">EXAMPLES</span></span>

<span data-ttu-id="2ba71-195">Les exemples de cette section utilisent le fournisseur de Registre PowerShell et supposent que vous êtes familiarisé avec celui-ci.</span><span class="sxs-lookup"><span data-stu-id="2ba71-195">The examples in this section use the PowerShell Registry provider and assume that you are familiar with it.</span></span> <span data-ttu-id="2ba71-196">Pour plus d’informations sur le fournisseur de Registre, tapez « obtenir-help registry ».</span><span class="sxs-lookup"><span data-stu-id="2ba71-196">For information about the Registry provider, type "get-help registry".</span></span>

### <a name="example-1-committing-a-transaction"></a><span data-ttu-id="2ba71-197">EXEMPLE 1 : VALIDATION D’UNE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="2ba71-197">EXAMPLE 1: COMMITTING A TRANSACTION</span></span>

<span data-ttu-id="2ba71-198">Pour créer une transaction, utilisez l’applet de commande Start-Transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-198">To create a transaction, use the Start-Transaction cmdlet.</span></span> <span data-ttu-id="2ba71-199">La commande suivante démarre une transaction avec les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ba71-199">The following command starts a transaction with the default settings.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="2ba71-200">Pour inclure des commandes dans la transaction, utilisez le paramètre UseTransaction de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="2ba71-200">To include commands in the transaction, use the UseTransaction parameter of the cmdlet.</span></span> <span data-ttu-id="2ba71-201">Par défaut, les commandes ne sont pas incluses dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-201">By default, commands are not included in the transaction,</span></span>

<span data-ttu-id="2ba71-202">Par exemple, la commande suivante, qui définit l’emplacement actuel dans la clé logicielle du lecteur HKCU :, n’est pas incluse dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-202">For example, the following command, which sets the current location in the Software key of the HKCU: drive, is not included in the transaction.</span></span>

```powershell
cd hkcu:\Software
```

<span data-ttu-id="2ba71-203">La commande suivante, qui crée la clé MyCompany, utilise le paramètre UseTransaction de l’applet de commande New-Item pour inclure la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-203">The following command, which creates the MyCompany key, uses the UseTransaction parameter of the New-Item cmdlet to include the command in the active transaction.</span></span>

```powershell
new-item MyCompany -UseTransaction
```

<span data-ttu-id="2ba71-204">La commande retourne un objet qui représente la nouvelle clé, mais comme la commande fait partie de la transaction, le registre n’est pas encore modifié.</span><span class="sxs-lookup"><span data-stu-id="2ba71-204">The command returns an object that represents the new key, but because the command is part of the transaction, the registry is not yet changed.</span></span>

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyCompany                      {}
```

<span data-ttu-id="2ba71-205">Pour valider la transaction, utilisez l’applet de commande Complete-Transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-205">To commit the transaction, use the Complete-Transaction cmdlet.</span></span> <span data-ttu-id="2ba71-206">Étant donné qu’elle affecte toujours la transaction active, vous ne pouvez pas spécifier la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-206">Because it always affects the active transaction, you cannot specify the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="2ba71-207">La clé MyCompany est donc ajoutée au registre.</span><span class="sxs-lookup"><span data-stu-id="2ba71-207">As a result, the MyCompany key is added to the registry.</span></span>

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

### <a name="example-2-rolling-back-a-transaction"></a><span data-ttu-id="2ba71-208">EXEMPLE 2 : RESTAURATION D’UNE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="2ba71-208">EXAMPLE 2: ROLLING BACK A TRANSACTION</span></span>

<span data-ttu-id="2ba71-209">Pour créer une transaction, utilisez l’applet de commande Start-Transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-209">To create a transaction, use the Start-Transaction cmdlet.</span></span> <span data-ttu-id="2ba71-210">La commande suivante démarre une transaction avec les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ba71-210">The following command starts a transaction with the default settings.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="2ba71-211">La commande suivante, qui crée la clé MyOtherCompany, utilise le paramètre UseTransaction de l’applet de commande New-Item pour inclure la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-211">The following command, which creates the MyOtherCompany key, uses the UseTransaction parameter of the New-Item cmdlet to include the command in the active transaction.</span></span>

```powershell
new-item MyOtherCompany -UseTransaction
```

<span data-ttu-id="2ba71-212">La commande retourne un objet qui représente la nouvelle clé, mais comme la commande fait partie de la transaction, le registre n’est pas encore modifié.</span><span class="sxs-lookup"><span data-stu-id="2ba71-212">The command returns an object that represents the new key, but because the command is part of the transaction, the registry is not yet changed.</span></span>

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyOtherCompany                 {}
```

<span data-ttu-id="2ba71-213">Pour restaurer la transaction, utilisez l’applet de commande Undo-Transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-213">To roll back the transaction, use the Undo-Transaction cmdlet.</span></span> <span data-ttu-id="2ba71-214">Étant donné qu’elle affecte toujours la transaction active, vous ne spécifiez pas la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-214">Because it always affects the active transaction, you do not specify the transaction.</span></span>

```powershell
Undo-transaction
```

<span data-ttu-id="2ba71-215">Le résultat est que la clé MyOtherCompany n’est pas ajoutée au registre.</span><span class="sxs-lookup"><span data-stu-id="2ba71-215">The result is that the MyOtherCompany key is not added to the registry.</span></span>

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

### <a name="example-3-previewing-a-transaction"></a><span data-ttu-id="2ba71-216">EXEMPLE 3 : APERÇU D’UNE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="2ba71-216">EXAMPLE 3: PREVIEWING A TRANSACTION</span></span>

<span data-ttu-id="2ba71-217">En règle générale, les commandes utilisées dans une transaction changent de données.</span><span class="sxs-lookup"><span data-stu-id="2ba71-217">Typically, the commands used in a transaction change data.</span></span> <span data-ttu-id="2ba71-218">Toutefois, les commandes qui obtiennent des données sont également utiles dans une transaction, car elles obtiennent des données à l’intérieur de la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-218">However, the commands that get data are useful in a transaction, too, because they get data inside of the transaction.</span></span> <span data-ttu-id="2ba71-219">Cela permet d’obtenir un aperçu des modifications qui sont à l’origine de la validation de la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-219">This provides a preview of the changes that committing the transaction would cause.</span></span>

<span data-ttu-id="2ba71-220">L’exemple suivant montre comment utiliser la commande Get-ChildItem (l’alias est « dir ») pour afficher un aperçu des modifications apportées à une transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-220">The following example shows how to use the Get-ChildItem command (the alias is "dir") to preview the changes in a transaction.</span></span>

<span data-ttu-id="2ba71-221">La commande suivante démarre une transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-221">The following command starts a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="2ba71-222">La commande suivante utilise l’applet de commande New-ItemProperty pour ajouter l’entrée de Registre MyKey à la clé MyCompany.</span><span class="sxs-lookup"><span data-stu-id="2ba71-222">The following command uses the New-ItemProperty cmdlet to add the MyKey registry entry to the MyCompany key.</span></span> <span data-ttu-id="2ba71-223">La commande utilise le paramètre UseTransaction pour inclure la commande dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-223">The command uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-itemproperty -path MyCompany -Name MyKey -value 123 -UseTransaction
```

<span data-ttu-id="2ba71-224">La commande retourne un objet représentant la nouvelle entrée de Registre, mais l’entrée de Registre n’est pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="2ba71-224">The command returns an object representing the new registry entry, but the registry entry is not changed.</span></span>

```
MyKey
-----
123
```

<span data-ttu-id="2ba71-225">Pour obtenir les éléments qui se trouvent actuellement dans le registre, utilisez une commande Get-ChildItem (« dir ») sans le paramètre UseTransaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-225">To get the items that are currently in the registry, use a Get-ChildItem command ("dir") without the UseTransaction parameter.</span></span> <span data-ttu-id="2ba71-226">La commande suivante obtient les éléments qui commencent par « M ».</span><span class="sxs-lookup"><span data-stu-id="2ba71-226">The following command gets items that begin with "M."</span></span>

```powershell
dir m*
```

<span data-ttu-id="2ba71-227">Le résultat indique qu’aucune entrée n’a encore été ajoutée à la clé MyCompany.</span><span class="sxs-lookup"><span data-stu-id="2ba71-227">The result shows that no entries have yet been added to the MyCompany key.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

<span data-ttu-id="2ba71-228">Pour afficher un aperçu de l’effet de la validation de la transaction, entrez une commande Get-ChildItem (« dir ») avec le paramètre UseTransaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-228">To preview the effect of committing the transaction, enter a Get-ChildItem ("dir") command with the UseTransaction parameter.</span></span> <span data-ttu-id="2ba71-229">Cette commande a une vue des données à partir de la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-229">This command has a view of the data from within the transaction.</span></span>

```powershell
dir m* -useTransaction
```

<span data-ttu-id="2ba71-230">Le résultat indique que, si la transaction est validée, l’entrée MyKey est ajoutée à la clé MyCompany.</span><span class="sxs-lookup"><span data-stu-id="2ba71-230">The result shows that, if the transaction is committed, the MyKey entry will be added to the MyCompany key.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   1 MyCompany                      {MyKey}
```

### <a name="example-4-combining-transacted-and-non-transacted-commands"></a><span data-ttu-id="2ba71-231">EXEMPLE 4 : COMBINAISON DE COMMANDES TRANSACTIONNELLES ET NON TRANSACTIONNELLES</span><span class="sxs-lookup"><span data-stu-id="2ba71-231">EXAMPLE 4: COMBINING TRANSACTED AND NON-TRANSACTED COMMANDS</span></span>

<span data-ttu-id="2ba71-232">Vous pouvez entrer des commandes non transactionnelles au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-232">You can enter non-transacted commands during a transaction.</span></span> <span data-ttu-id="2ba71-233">Les commandes non transactionnelles affectent immédiatement les données, mais elles n’affectent pas la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-233">The non-transacted commands affect the data immediately, but they do not affect the transaction.</span></span>
<span data-ttu-id="2ba71-234">La commande suivante démarre une transaction dans la clé de Registre HKCU : \ Software.</span><span class="sxs-lookup"><span data-stu-id="2ba71-234">The following command starts a transaction in the HKCU:\Software registry key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="2ba71-235">Les trois commandes suivantes utilisent l’applet de commande New-Item pour ajouter des clés au registre.</span><span class="sxs-lookup"><span data-stu-id="2ba71-235">The next three commands use the New-Item cmdlet to add keys to the registry.</span></span>
<span data-ttu-id="2ba71-236">La première et la troisième commande utilisent le paramètre UseTransaction pour inclure les commandes dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-236">The first and third commands use the UseTransaction parameter to include the commands in the transaction.</span></span> <span data-ttu-id="2ba71-237">La deuxième commande omet le paramètre.</span><span class="sxs-lookup"><span data-stu-id="2ba71-237">The second command omits the parameter.</span></span> <span data-ttu-id="2ba71-238">Étant donné que la deuxième commande n’est pas incluse dans la transaction, elle est immédiatement effective.</span><span class="sxs-lookup"><span data-stu-id="2ba71-238">Because the second command is not included in the transaction, it is effective immediately.</span></span>

```powershell
new-item MyCompany1 -UseTransaction
new-item MyCompany2
new-item MyCompany3 -UseTransaction
```

<span data-ttu-id="2ba71-239">Pour afficher l’état actuel du Registre, utilisez une commande Get-ChildItem (« dir ») sans le paramètre UseTransaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-239">To view the current state of the registry, use a Get-ChildItem ("dir") command without the UseTransaction parameter.</span></span> <span data-ttu-id="2ba71-240">Cette commande obtient les éléments qui commencent par « M ».</span><span class="sxs-lookup"><span data-stu-id="2ba71-240">This command gets items that begin with "M."</span></span>

```powershell
dir m*
```

<span data-ttu-id="2ba71-241">Le résultat indique que la clé MyCompany2 est ajoutée au registre, mais que les clés MyCompany1 et MyCompany3, qui font partie de la transaction, ne sont pas ajoutées.</span><span class="sxs-lookup"><span data-stu-id="2ba71-241">The result shows that the MyCompany2 key is added to the registry, but the MyCompany1 and MyCompany3 keys, which are part of the transaction, are not added.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0    0 MyCompany2                     {}
```

<span data-ttu-id="2ba71-242">La commande suivante valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-242">The following command commits the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="2ba71-243">À présent, les clés ajoutées dans le cadre de la transaction s’affichent dans le registre.</span><span class="sxs-lookup"><span data-stu-id="2ba71-243">Now, the keys that were added as part of the transaction appear in the registry.</span></span>

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

### <a name="example-5-using-automatic-rollback"></a><span data-ttu-id="2ba71-244">EXEMPLE 5 : UTILISATION DE LA RESTAURATION AUTOMATIQUE</span><span class="sxs-lookup"><span data-stu-id="2ba71-244">EXAMPLE 5: USING AUTOMATIC ROLLBACK</span></span>

<span data-ttu-id="2ba71-245">Quand une commande dans une transaction génère une erreur de n’importe quel type, la transaction est automatiquement restaurée.</span><span class="sxs-lookup"><span data-stu-id="2ba71-245">When a command in a transaction generates an error of any kind, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="2ba71-246">Ce comportement par défaut est conçu pour les scripts qui exécutent des transactions.</span><span class="sxs-lookup"><span data-stu-id="2ba71-246">This default behavior is designed for scripts that run transactions.</span></span> <span data-ttu-id="2ba71-247">Les scripts sont généralement testés correctement et incluent une logique de gestion des erreurs, de sorte que les erreurs ne sont pas attendues et doivent mettre fin à la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-247">Scripts are typically well tested and include error-handling logic, so errors are not expected and should terminate the transaction.</span></span>

<span data-ttu-id="2ba71-248">La première commande démarre une transaction dans la clé de Registre HKCU : \ Software.</span><span class="sxs-lookup"><span data-stu-id="2ba71-248">The first command starts a transaction in the HKCU:\Software registry key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="2ba71-249">La commande suivante utilise l’applet de commande New-Item pour ajouter la clé MyCompany au registre.</span><span class="sxs-lookup"><span data-stu-id="2ba71-249">The following command uses the New-Item cmdlet to add the MyCompany key to the registry.</span></span> <span data-ttu-id="2ba71-250">La commande utilise le paramètre UseTransaction (l’alias est « UseTX ») pour inclure la commande dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-250">The command uses the UseTransaction parameter (the alias is "usetx") to include the command in the transaction.</span></span>

```powershell
New-Item MyCompany -UseTX
```

<span data-ttu-id="2ba71-251">Étant donné que la clé MyCompany existe déjà dans le registre, la commande échoue et la transaction est restaurée.</span><span class="sxs-lookup"><span data-stu-id="2ba71-251">Because the MyCompany key already exists in the registry, the command fails, and the transaction is rolled back.</span></span>

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

<span data-ttu-id="2ba71-252">Une commande Get-Transaction confirme que la transaction a été restaurée et que SubscriberCount est égal à 0.</span><span class="sxs-lookup"><span data-stu-id="2ba71-252">A Get-Transaction command confirms that the transaction has been rolled back and that the SubscriberCount is 0.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 RolledBack
```

### <a name="example-6-changing-the-rollback-preference"></a><span data-ttu-id="2ba71-253">EXEMPLE 6 : MODIFICATION DE LA PRÉFÉRENCE DE RESTAURATION</span><span class="sxs-lookup"><span data-stu-id="2ba71-253">EXAMPLE 6: CHANGING THE ROLLBACK PREFERENCE</span></span>

<span data-ttu-id="2ba71-254">Si vous souhaitez que la transaction soit plus tolérante aux erreurs, vous pouvez utiliser le paramètre RollbackPreference de Start-Transaction pour modifier la préférence.</span><span class="sxs-lookup"><span data-stu-id="2ba71-254">If you want the transaction to be more error tolerant, you can use the RollbackPreference parameter of Start-Transaction to change the preference.</span></span>

<span data-ttu-id="2ba71-255">La commande suivante démarre une transaction avec une préférence de restauration « Never ».</span><span class="sxs-lookup"><span data-stu-id="2ba71-255">The following command starts a transaction with a rollback preference of "Never".</span></span>

```powershell
start-transaction -rollbackpreference Never
```

<span data-ttu-id="2ba71-256">Dans ce cas, lorsque la commande échoue, la transaction n’est pas automatiquement restaurée.</span><span class="sxs-lookup"><span data-stu-id="2ba71-256">In this case, when the command fails, the transaction is not automatically rolled back.</span></span>

```powershell
New-Item MyCompany -UseTX
```

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

<span data-ttu-id="2ba71-257">Étant donné que la transaction est toujours active, vous pouvez soumettre à nouveau la commande dans le cadre de la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-257">Because the transaction is still active, you can resubmit the command as part of the transaction.</span></span>

```powershell
New-Item MyOtherCompany -UseTX
```

### <a name="example-7-using-the-use-transaction-cmdlet"></a><span data-ttu-id="2ba71-258">EXEMPLE 7 : UTILISATION DE L’APPLET DE COMMANDE USE-TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="2ba71-258">EXAMPLE 7: USING THE USE-TRANSACTION CMDLET</span></span>

<span data-ttu-id="2ba71-259">L’applet de commande Use-Transaction vous permet d’effectuer des scripts directs sur les objets de l’infrastructure de Microsoft .NET de transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-259">The Use-Transaction cmdlet enables you to do direct scripting against transaction-enabled Microsoft .NET Framework objects.</span></span> <span data-ttu-id="2ba71-260">Use-Transaction accepte un bloc de script qui ne peut contenir que des commandes et des expressions qui utilisent des objets de .NET Framework à transaction activée, tels que des instances de la classe Microsoft. PowerShell. Commands. Management. TransactedString.</span><span class="sxs-lookup"><span data-stu-id="2ba71-260">Use-Transaction takes a script block that can only contain commands and expressions that use transaction-enabled .NET Framework objects, such as instances of the Microsoft.PowerShell.Commands.Management.TransactedString class.</span></span>

<span data-ttu-id="2ba71-261">La commande suivante démarre une transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-261">The following command starts a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="2ba71-262">La commande New-Object suivante crée une instance de la classe TransactedString et l’enregistre dans la variable $t.</span><span class="sxs-lookup"><span data-stu-id="2ba71-262">The following New-Object command creates an instance of the TransactedString class and saves it in the $t variable.</span></span>

```powershell
$t = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
```

<span data-ttu-id="2ba71-263">La commande suivante utilise la méthode Append de l’objet TransactedString pour ajouter du texte à la chaîne.</span><span class="sxs-lookup"><span data-stu-id="2ba71-263">The following command uses the Append method of the TransactedString object to add text to the string.</span></span> <span data-ttu-id="2ba71-264">Étant donné que la commande ne fait pas partie de la transaction, la modification est immédiatement effective.</span><span class="sxs-lookup"><span data-stu-id="2ba71-264">Because the command is not part of the transaction, the change is effective immediately.</span></span>

```powershell
$t.append("Windows")
```

<span data-ttu-id="2ba71-265">La commande suivante utilise la même méthode Append pour ajouter du texte, mais elle ajoute le texte dans le cadre de la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-265">The following command uses the same Append method to add text, but it adds the text as part of the transaction.</span></span> <span data-ttu-id="2ba71-266">La commande est placée entre accolades et est définie comme valeur du paramètre ScriptBlock de use-transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-266">The command is enclosed in braces, and it is set as the value of the ScriptBlock parameter of Use-Transaction.</span></span> <span data-ttu-id="2ba71-267">Le paramètre UseTransaction (UseTx) est requis.</span><span class="sxs-lookup"><span data-stu-id="2ba71-267">The UseTransaction parameter (UseTx) is required.</span></span>

```powershell
use-transaction {$t.append(" PowerShell")} -usetx
```

<span data-ttu-id="2ba71-268">Pour afficher le contenu actuel de la chaîne traitée dans $t, utilisez la méthode ToString de l’objet TransactedString.</span><span class="sxs-lookup"><span data-stu-id="2ba71-268">To see the current content of the transacted string in $t, use the ToString method of the TransactedString object.</span></span>

```powershell
$t.tostring()
```

<span data-ttu-id="2ba71-269">La sortie indique que seules les modifications non transactionnelles sont effectives.</span><span class="sxs-lookup"><span data-stu-id="2ba71-269">The output shows that only the non-transacted changes are effective.</span></span>

```output
Windows
```

<span data-ttu-id="2ba71-270">Pour afficher le contenu actuel de la chaîne traitée dans $t à partir de la transaction, incorporez l’expression dans une commande Use-Transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-270">To see the current content of the transacted string in $t from within the transaction, embed the expression in a Use-Transaction command.</span></span>

```powershell
use-transaction {$s.tostring()} -usetx
```

<span data-ttu-id="2ba71-271">La sortie affiche la vue de la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-271">The output shows the transaction view.</span></span>

```output
PowerShell
```

<span data-ttu-id="2ba71-272">La commande suivante valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-272">The following command commits the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="2ba71-273">Pour afficher la chaîne finale :</span><span class="sxs-lookup"><span data-stu-id="2ba71-273">To see the final string:</span></span>

```
$t.tostring()
PowerShell
```

### <a name="example-8-managing-multi-subscriber-transactions"></a><span data-ttu-id="2ba71-274">EXEMPLE 8 : GESTION DES TRANSACTIONS SUR PLUSIEURS ABONNÉS</span><span class="sxs-lookup"><span data-stu-id="2ba71-274">EXAMPLE 8: MANAGING MULTI-SUBSCRIBER TRANSACTIONS</span></span>

<span data-ttu-id="2ba71-275">Lorsque vous démarrez une transaction alors qu’une autre transaction est en cours, PowerShell ne crée pas de deuxième transaction par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ba71-275">When you start a transaction while another transaction is in progress, PowerShell does not create a second transaction by default.</span></span> <span data-ttu-id="2ba71-276">Au lieu de cela, il ajoute un abonné à la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="2ba71-276">Instead, it adds a subscriber to the current transaction.</span></span>

<span data-ttu-id="2ba71-277">Cet exemple montre comment afficher et gérer une transaction multi-abonnés.</span><span class="sxs-lookup"><span data-stu-id="2ba71-277">This example shows how to view and manage a multi-subscriber transaction.</span></span>

<span data-ttu-id="2ba71-278">Commencez par démarrer une transaction dans la clé HKCU : \ Software.</span><span class="sxs-lookup"><span data-stu-id="2ba71-278">Begin by starting a transaction in the HKCU:\Software key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="2ba71-279">La commande suivante utilise la commande Get-Transaction pour récupérer la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-279">The following command uses the Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="2ba71-280">Le résultat affiche l’objet qui représente la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-280">The result shows the object that represents the active transaction.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="2ba71-281">La commande suivante ajoute la clé MyCompany au registre.</span><span class="sxs-lookup"><span data-stu-id="2ba71-281">The following command adds the MyCompany key to the registry.</span></span> <span data-ttu-id="2ba71-282">La commande utilise le paramètre UseTransaction pour inclure la commande dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-282">The command uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-item MyCompany -UseTransaction
```

<span data-ttu-id="2ba71-283">La commande suivante utilise la commande Start-Transaction pour démarrer une transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-283">The following command uses the Start-Transaction command to start a transaction.</span></span> <span data-ttu-id="2ba71-284">Bien que cette commande soit tapée à l’invite de commandes, ce scénario est plus susceptible de se produire lorsque vous exécutez un script qui contient une transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-284">Although this command is typed at the command prompt, this scenario is more likely to happen when you run a script that contains a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="2ba71-285">Une commande Get-Transaction indique que le nombre d’abonnés sur l’objet transaction est incrémenté.</span><span class="sxs-lookup"><span data-stu-id="2ba71-285">A Get-Transaction command shows that the subscriber count on the transaction object is incremented.</span></span> <span data-ttu-id="2ba71-286">La valeur est maintenant 2.</span><span class="sxs-lookup"><span data-stu-id="2ba71-286">The value is now 2.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

<span data-ttu-id="2ba71-287">La commande suivante utilise l’applet de commande New-ItemProperty pour ajouter l’entrée de Registre MyKey à la clé MyCompany.</span><span class="sxs-lookup"><span data-stu-id="2ba71-287">The next command uses the New-ItemProperty cmdlet to add the MyKey registry entry to the MyCompany key.</span></span> <span data-ttu-id="2ba71-288">Elle utilise le paramètre UseTransaction pour inclure la commande dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-288">It uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-itemproperty -path MyCompany -name MyKey -UseTransaction
```

<span data-ttu-id="2ba71-289">La clé MyCompany n’existe pas dans le registre, mais cette commande est réussie, car les deux commandes font partie de la même transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-289">The MyCompany key does not exist in the registry, but this command succeeds because the two commands are part of the same transaction.</span></span>

<span data-ttu-id="2ba71-290">La commande suivante valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-290">The following command commits the transaction.</span></span> <span data-ttu-id="2ba71-291">Si la transaction a été annulée, la transaction est restaurée pour tous les abonnés.</span><span class="sxs-lookup"><span data-stu-id="2ba71-291">If it rolled back the transaction, the transaction would be rolled back for all the subscribers.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="2ba71-292">Une commande de Get-Transaction indique que le nombre d’abonnés sur l’objet de transaction est 1, mais la valeur de l’État est toujours active (non validée).</span><span class="sxs-lookup"><span data-stu-id="2ba71-292">A Get-Transaction command shows that the subscriber count on the transaction object is 1, but the value of Status is still Active (not Committed).</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="2ba71-293">Pour terminer la validation de la transaction, entrez une deuxième commande Complete-Transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-293">To finish committing the transaction, enter a second Complete- Transaction command.</span></span> <span data-ttu-id="2ba71-294">Pour valider une transaction multi-abonné, vous devez entrer une commande Complete-Transaction pour chaque commande Start-Transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-294">To commit a multi-subscriber transaction, you must enter one Complete-Transaction command for each Start-Transaction command.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="2ba71-295">Une autre commande de Get-Transaction indique que la transaction a été validée.</span><span class="sxs-lookup"><span data-stu-id="2ba71-295">Another Get-Transaction command shows that the transaction has been committed.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 Committed
```

### <a name="example-9-managing-independent-transactions"></a><span data-ttu-id="2ba71-296">EXEMPLE 9 : GESTION DES TRANSACTIONS INDÉPENDANTES</span><span class="sxs-lookup"><span data-stu-id="2ba71-296">EXAMPLE 9: MANAGING INDEPENDENT TRANSACTIONS</span></span>

<span data-ttu-id="2ba71-297">Lorsque vous démarrez une transaction pendant qu’une autre transaction est en cours, vous pouvez utiliser le paramètre Independent de Start-Transaction pour rendre la nouvelle transaction indépendante de la transaction d’origine.</span><span class="sxs-lookup"><span data-stu-id="2ba71-297">When you start a transaction while another transaction is in progress, you can use the Independent parameter of Start-Transaction to make the new transaction independent of the original transaction.</span></span>

<span data-ttu-id="2ba71-298">Dans ce cas, Start-Transaction crée un nouvel objet de transaction et fait de la transaction active la nouvelle transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-298">When you do, Start-Transaction creates a new transaction object and makes the new transaction the active transaction.</span></span>

<span data-ttu-id="2ba71-299">Commencez par démarrer une transaction dans la clé HKCU : \\ Software.</span><span class="sxs-lookup"><span data-stu-id="2ba71-299">Begin by starting a transaction in the HKCU:\\Software key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="2ba71-300">La commande suivante utilise la commande Get-Transaction pour récupérer la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-300">The following command uses the Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="2ba71-301">Le résultat affiche l’objet qui représente la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-301">The result shows the object that represents the active transaction.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="2ba71-302">La commande suivante ajoute la clé de Registre MyCompany dans le cadre de la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-302">The following command adds the MyCompany registry key as part of the transaction.</span></span> <span data-ttu-id="2ba71-303">Elle utilise le paramètre UseTransaction (UseTx) pour inclure la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-303">It uses the UseTransaction parameter (UseTx) to include the command in the active transaction.</span></span>

```powershell
new-item MyCompany -use
```

<span data-ttu-id="2ba71-304">La commande suivante démarre une nouvelle transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-304">The following command starts a new transaction.</span></span> <span data-ttu-id="2ba71-305">La commande utilise le paramètre Independent pour indiquer que cette transaction n’est pas un abonné à la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-305">The command uses the Independent parameter to indicate that this transaction is not a subscriber to the active transaction.</span></span>

```powershell
start-transaction -independent
```

<span data-ttu-id="2ba71-306">Lorsque vous créez une transaction indépendante, la nouvelle transaction (la plus récemment créée) devient la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-306">When you create an independent transaction, the new (most-recently created) transaction becomes the active transaction.</span></span> <span data-ttu-id="2ba71-307">Vous pouvez utiliser une commande Get-Transaction pour obtenir la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-307">You can use a Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="2ba71-308">Notez que le SubscriberCount de la transaction est 1, ce qui indique qu’il n’y a pas d’autres abonnés et que la transaction est nouvelle.</span><span class="sxs-lookup"><span data-stu-id="2ba71-308">Note that the SubscriberCount of the transaction is 1, indicating that there are no other subscribers and that the transaction is new.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="2ba71-309">La nouvelle transaction doit être terminée (validée ou restaurée) pour que vous puissiez gérer la transaction d’origine.</span><span class="sxs-lookup"><span data-stu-id="2ba71-309">The new transaction must be finished (either committed or rolled back) before you can manage the original transaction.</span></span>

<span data-ttu-id="2ba71-310">La commande suivante ajoute la clé MyOtherCompany au registre.</span><span class="sxs-lookup"><span data-stu-id="2ba71-310">The following command adds the MyOtherCompany key to the registry.</span></span> <span data-ttu-id="2ba71-311">Elle utilise le paramètre UseTransaction (UseTx) pour inclure la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-311">It uses the UseTransaction parameter (UseTx) to include the command in the active transaction.</span></span>

```powershell
new-item MyOtherCompany -usetx
```

<span data-ttu-id="2ba71-312">À présent, restaurez la transaction.</span><span class="sxs-lookup"><span data-stu-id="2ba71-312">Now, roll back the transaction.</span></span> <span data-ttu-id="2ba71-313">S’il y avait une seule transaction avec deux abonnés, la restauration de la transaction restaurait la totalité de la transaction pour tous les abonnés.</span><span class="sxs-lookup"><span data-stu-id="2ba71-313">If there were a single transaction with two subscribers, rolling back the transaction would roll back the entire transaction for all the subscribers.</span></span>

<span data-ttu-id="2ba71-314">Toutefois, étant donné que ces transactions sont indépendantes, la restauration de la dernière transaction annule les modifications apportées au registre et fait de la transaction d’origine la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-314">However, because these transactions are independent, rolling back the newest transaction cancels the registry changes and makes the original transaction the active transaction.</span></span>

```powershell
undo-transaction
```

<span data-ttu-id="2ba71-315">Une commande Get-Transaction confirme que la transaction d’origine est toujours active dans la session.</span><span class="sxs-lookup"><span data-stu-id="2ba71-315">A Get-Transaction command confirms that the original transaction is still active in the session.</span></span>

```powershell
get-transaction
```

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="2ba71-316">La commande suivante valide la transaction active.</span><span class="sxs-lookup"><span data-stu-id="2ba71-316">The following command commits the active transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="2ba71-317">Une commande Get-ChildItem indique que le registre a été modifié.</span><span class="sxs-lookup"><span data-stu-id="2ba71-317">A Get-ChildItem command shows that the registry has been changed.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2ba71-318">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="2ba71-318">SEE ALSO</span></span>

[<span data-ttu-id="2ba71-319">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="2ba71-319">Start-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Start-Transaction)

[<span data-ttu-id="2ba71-320">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="2ba71-320">Get-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Get-Transaction)

[<span data-ttu-id="2ba71-321">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="2ba71-321">Complete-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Complete-Transaction)

[<span data-ttu-id="2ba71-322">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="2ba71-322">Undo-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Undo-Transaction)

[<span data-ttu-id="2ba71-323">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="2ba71-323">Use-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Use-Transaction)

[<span data-ttu-id="2ba71-324">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="2ba71-324">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

[<span data-ttu-id="2ba71-325">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2ba71-325">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

[<span data-ttu-id="2ba71-326">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2ba71-326">about_Providers</span></span>](about_Providers.md)
