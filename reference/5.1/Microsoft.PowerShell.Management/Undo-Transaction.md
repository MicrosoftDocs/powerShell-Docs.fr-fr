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
# <span data-ttu-id="cf98e-103">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="cf98e-103">Undo-Transaction</span></span>

## <span data-ttu-id="cf98e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="cf98e-104">SYNOPSIS</span></span>
<span data-ttu-id="cf98e-105">Restaure la transaction active.</span><span class="sxs-lookup"><span data-stu-id="cf98e-105">Rolls back the active transaction.</span></span>

## <span data-ttu-id="cf98e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cf98e-106">SYNTAX</span></span>

```
Undo-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cf98e-107">Description</span><span class="sxs-lookup"><span data-stu-id="cf98e-107">DESCRIPTION</span></span>
<span data-ttu-id="cf98e-108">L’applet de **commande Undo-Transaction** restaure la transaction active.</span><span class="sxs-lookup"><span data-stu-id="cf98e-108">The **Undo-Transaction** cmdlet rolls back the active transaction.</span></span>
<span data-ttu-id="cf98e-109">Lorsque vous restaurez une transaction, les modifications apportées par les commandes de la transaction sont ignorées et les données sont restaurées dans leur forme d’origine.</span><span class="sxs-lookup"><span data-stu-id="cf98e-109">When you roll back a transaction, the changes that were made by the commands in the transaction are discarded and the data is restored to its original form.</span></span>

<span data-ttu-id="cf98e-110">Si la transaction comporte plusieurs abonnés, une commande **Undo-Transaction** restaure l’intégralité de la transaction pour tous les abonnés.</span><span class="sxs-lookup"><span data-stu-id="cf98e-110">If the transaction includes multiple subscribers, an **Undo-Transaction** command rolls back the whole transaction for all subscribers.</span></span>

<span data-ttu-id="cf98e-111">Les transactions sont automatiquement restaurées par défaut lorsqu’une commande figurant dans la transaction génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="cf98e-111">By default, transactions are rolled back automatically if any command in the transaction generates an error.</span></span>
<span data-ttu-id="cf98e-112">Toutefois, les transactions peuvent être démarrées à l’aide d’une préférence de restauration différente et vous pouvez utiliser cette applet de commande pour restaurer la transaction active à tout moment.</span><span class="sxs-lookup"><span data-stu-id="cf98e-112">However, transactions can be started by using a different rollback preference and you can use this cmdlet to roll back the active transaction at any time.</span></span>

<span data-ttu-id="cf98e-113">L’applet de **commande Undo-Transaction** fait partie d’un ensemble d’applets de commande qui prennent en charge la fonctionnalité des transactions dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf98e-113">The **Undo-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="cf98e-114">Pour plus d'informations, consultez about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="cf98e-114">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="cf98e-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="cf98e-115">EXAMPLES</span></span>

### <span data-ttu-id="cf98e-116">Exemple 1 : restaurer la transaction actuelle</span><span class="sxs-lookup"><span data-stu-id="cf98e-116">Example 1: Roll back the current transaction</span></span>

```
PS C:\> Undo-Transaction
```

<span data-ttu-id="cf98e-117">Cette commande restaure la transaction actuelle, active et active.</span><span class="sxs-lookup"><span data-stu-id="cf98e-117">This command rolls back the current, active, transaction.</span></span>

### <span data-ttu-id="cf98e-118">Exemple 2 : Démarrer et restaurer une transaction</span><span class="sxs-lookup"><span data-stu-id="cf98e-118">Example 2: Start and roll back a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Undo-Transaction
```

<span data-ttu-id="cf98e-119">Cet exemple démarre une transaction, puis la restaure.</span><span class="sxs-lookup"><span data-stu-id="cf98e-119">This example starts a transaction and then rolls it back.</span></span>
<span data-ttu-id="cf98e-120">Aucune modification n’est par conséquent apportée au Registre.</span><span class="sxs-lookup"><span data-stu-id="cf98e-120">As a result, no changes are made to the registry.</span></span>

### <span data-ttu-id="cf98e-121">Exemple 3 : restaurer une transaction pour tous les abonnés</span><span class="sxs-lookup"><span data-stu-id="cf98e-121">Example 3: Roll back a transaction for all subscribers</span></span>

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

<span data-ttu-id="cf98e-122">Cet exemple montre que, lorsqu’un abonné restaure une transaction, toute la transaction est restaurée pour tous les abonnés.</span><span class="sxs-lookup"><span data-stu-id="cf98e-122">This example demonstrates that when any subscriber rolls back a transaction, the whole transaction is rolled back for all subscribers.</span></span>

<span data-ttu-id="cf98e-123">La première commande change l’emplacement de la clé de Registre HKCU:\Software.</span><span class="sxs-lookup"><span data-stu-id="cf98e-123">The first command changes the location to the HKCU:\Software registry key.</span></span>

<span data-ttu-id="cf98e-124">La deuxième commande démarre une transaction.</span><span class="sxs-lookup"><span data-stu-id="cf98e-124">The second command starts a transaction.</span></span>

<span data-ttu-id="cf98e-125">La troisième commande utilise l’applet de commande New-Item pour créer une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="cf98e-125">The third command uses the New-Item cmdlet to create a new registry key.</span></span>
<span data-ttu-id="cf98e-126">La commande utilise le paramètre *UseTransaction* pour inclure la modification dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="cf98e-126">The command uses the *UseTransaction* parameter to include the change in the transaction.</span></span>

<span data-ttu-id="cf98e-127">La quatrième commande utilise l’applet de commande Get-Transaction pour obtenir la transaction active.</span><span class="sxs-lookup"><span data-stu-id="cf98e-127">The fourth command uses the Get-Transaction cmdlet to get the active transaction.</span></span>
<span data-ttu-id="cf98e-128">Notez que l’état a la valeur Active et que le nombre d’abonnés a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="cf98e-128">Notice that the status is Active and the subscriber count is 1.</span></span>

<span data-ttu-id="cf98e-129">La cinquième commande réutilise la commande Start-Transaction.</span><span class="sxs-lookup"><span data-stu-id="cf98e-129">The fifth command uses the Start-Transaction command again.</span></span>
<span data-ttu-id="cf98e-130">En général, le démarrage d’une transaction pendant qu’une autre transaction est en cours se produit lorsqu’un script utilisé par la transaction principale comprend sa propre transaction complète.</span><span class="sxs-lookup"><span data-stu-id="cf98e-130">Typically, starting a transaction while another transaction is in progress occurs when a script that is used by the main transaction includes its own complete transaction.</span></span>
<span data-ttu-id="cf98e-131">Cet exemple est exécuté de manière interactive pour que vous puissiez l’examiner par étapes.</span><span class="sxs-lookup"><span data-stu-id="cf98e-131">This example is performed interactively so that you can examine it in stages.</span></span>
<span data-ttu-id="cf98e-132">Quand vous exécutez une commande **start-transaction** alors qu’une autre transaction est en cours, les commandes joignent la transaction existante en tant que nouvel abonné et le nombre d’abonnés est incrémenté.</span><span class="sxs-lookup"><span data-stu-id="cf98e-132">When you run a **Start-Transaction** command while another transaction is in progress, the commands join the existing transaction as a new subscriber and the subscriber count is incremented.</span></span>

<span data-ttu-id="cf98e-133">La sixième commande utilise l’applet de commande **« obtient-transaction »** pour récupérer la transaction active.</span><span class="sxs-lookup"><span data-stu-id="cf98e-133">The sixth command uses the **Get-Transaction** cmdlet to get the active transaction.</span></span>
<span data-ttu-id="cf98e-134">Notez que le nombre d’abonnés a maintenant la valeur 2.</span><span class="sxs-lookup"><span data-stu-id="cf98e-134">Notice that the subscriber count is now 2.</span></span>

<span data-ttu-id="cf98e-135">La septième commande utilise **Undo-Transaction** pour restaurer la transaction.</span><span class="sxs-lookup"><span data-stu-id="cf98e-135">The seventh command uses **Undo-Transaction** to roll back the transaction.</span></span>
<span data-ttu-id="cf98e-136">Cette commande ne retourne pas d’objets.</span><span class="sxs-lookup"><span data-stu-id="cf98e-136">This command does not return any objects.</span></span>

<span data-ttu-id="cf98e-137">La dernière commande est une commande d' **extraction de transaction** qui obtient le actif, ou dans ce cas, la dernière transaction active.</span><span class="sxs-lookup"><span data-stu-id="cf98e-137">The final command is a **Get-Transaction** command that gets the active, or in this case, the most recently active, transaction.</span></span>
<span data-ttu-id="cf98e-138">Les résultats indiquent que la transaction est restaurée et que le nombre d’abonnés a la valeur 0 (ce qui signifie que la transaction a été restaurée pour tous les abonnés).</span><span class="sxs-lookup"><span data-stu-id="cf98e-138">The results show that the transaction is rolled back, and that the subscriber count is 0, showing that the transaction was rolled back for all subscribers.</span></span>

## <span data-ttu-id="cf98e-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cf98e-139">PARAMETERS</span></span>

### <span data-ttu-id="cf98e-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cf98e-140">-Confirm</span></span>
<span data-ttu-id="cf98e-141">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cf98e-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cf98e-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cf98e-142">-WhatIf</span></span>
<span data-ttu-id="cf98e-143">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cf98e-143">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="cf98e-144">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="cf98e-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cf98e-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cf98e-145">CommonParameters</span></span>
<span data-ttu-id="cf98e-146">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cf98e-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cf98e-147">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cf98e-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cf98e-148">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="cf98e-148">INPUTS</span></span>

### <span data-ttu-id="cf98e-149">Aucun</span><span class="sxs-lookup"><span data-stu-id="cf98e-149">None</span></span>
<span data-ttu-id="cf98e-150">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="cf98e-150">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="cf98e-151">SORTIES</span><span class="sxs-lookup"><span data-stu-id="cf98e-151">OUTPUTS</span></span>

### <span data-ttu-id="cf98e-152">Aucun</span><span class="sxs-lookup"><span data-stu-id="cf98e-152">None</span></span>
<span data-ttu-id="cf98e-153">Cette applet de commande ne retourne aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="cf98e-153">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="cf98e-154">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="cf98e-154">NOTES</span></span>

* <span data-ttu-id="cf98e-155">Vous ne pouvez pas restaurer une transaction qui a été validée.</span><span class="sxs-lookup"><span data-stu-id="cf98e-155">You cannot roll back a transaction that has been committed.</span></span>

  <span data-ttu-id="cf98e-156">Vous ne pouvez pas restaurer une autre transaction que la transaction active.</span><span class="sxs-lookup"><span data-stu-id="cf98e-156">You cannot roll back any transaction other than the active transaction.</span></span>
<span data-ttu-id="cf98e-157">Pour restaurer une autre transaction indépendante, vous devez commencer par valider ou restaurer la transaction active.</span><span class="sxs-lookup"><span data-stu-id="cf98e-157">To roll back a different, independent transaction, you must first commit or roll back the active transaction.</span></span>

  <span data-ttu-id="cf98e-158">La restauration de la transaction termine la transaction.</span><span class="sxs-lookup"><span data-stu-id="cf98e-158">Rolling back the transaction ends the transaction.</span></span>
<span data-ttu-id="cf98e-159">Pour réutiliser une transaction, vous devez démarrer une nouvelle transaction.</span><span class="sxs-lookup"><span data-stu-id="cf98e-159">To use a transaction again, you must start a new transaction.</span></span>

## <span data-ttu-id="cf98e-160">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="cf98e-160">RELATED LINKS</span></span>

[<span data-ttu-id="cf98e-161">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="cf98e-161">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="cf98e-162">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="cf98e-162">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="cf98e-163">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="cf98e-163">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="cf98e-164">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="cf98e-164">Use-Transaction</span></span>](Use-Transaction.md)
