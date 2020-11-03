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
# <span data-ttu-id="57224-103">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="57224-103">Complete-Transaction</span></span>

## <span data-ttu-id="57224-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="57224-104">SYNOPSIS</span></span>
<span data-ttu-id="57224-105">Valide la transaction active.</span><span class="sxs-lookup"><span data-stu-id="57224-105">Commits the active transaction.</span></span>

## <span data-ttu-id="57224-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="57224-106">SYNTAX</span></span>

```
Complete-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="57224-107">Description</span><span class="sxs-lookup"><span data-stu-id="57224-107">DESCRIPTION</span></span>
<span data-ttu-id="57224-108">L’applet **de commande Complete-Transaction** valide une transaction active.</span><span class="sxs-lookup"><span data-stu-id="57224-108">The **Complete-Transaction** cmdlet commits an active transaction.</span></span>
<span data-ttu-id="57224-109">Lorsque vous validez une transaction, les commandes de la transaction sont finalisées et les données concernées par les commandes sont modifiées.</span><span class="sxs-lookup"><span data-stu-id="57224-109">When you commit a transaction, the commands in the transaction are finalized and the data affected by the commands is changed.</span></span>

<span data-ttu-id="57224-110">Si la transaction comporte plusieurs abonnés, pour valider la transaction, vous devez entrer une commande **Complete-Transaction** pour chaque commande Start-Transaction.</span><span class="sxs-lookup"><span data-stu-id="57224-110">If the transaction includes multiple subscribers, to commit the transaction, you must enter one **Complete-Transaction** command for every Start-Transaction command.</span></span>

<span data-ttu-id="57224-111">L’applet de commande **Complete-Transaction** fait partie d’un ensemble d’applets de commande qui prennent en charge la fonctionnalité des transactions dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57224-111">The **Complete-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="57224-112">Pour plus d'informations, consultez about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="57224-112">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="57224-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="57224-113">EXAMPLES</span></span>

### <span data-ttu-id="57224-114">Exemple 1 : valider une transaction</span><span class="sxs-lookup"><span data-stu-id="57224-114">Example 1: Commit a transaction</span></span>

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

<span data-ttu-id="57224-115">Cet exemple montre ce qui se passe lorsque vous utilisez l’applet de commande **Complete-Transaction** pour valider une transaction.</span><span class="sxs-lookup"><span data-stu-id="57224-115">This example shows what happens when you use the **Complete-Transaction** cmdlet to commit a transaction.</span></span>

<span data-ttu-id="57224-116">La commande **start-transaction** démarre la transaction.</span><span class="sxs-lookup"><span data-stu-id="57224-116">The **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="57224-117">La commande New-Item utilise le paramètre *UseTransaction* pour inclure la commande dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="57224-117">The New-Item command uses the *UseTransaction* parameter to include the command in the transaction.</span></span>

<span data-ttu-id="57224-118">La première commande dir (obten-ChildItem) indique que le nouvel élément n’a pas encore été ajouté au registre.</span><span class="sxs-lookup"><span data-stu-id="57224-118">The first dir (Get-ChildItem) command shows that the new item has not yet been added to the registry.</span></span>

<span data-ttu-id="57224-119">La commande **Complete-Transaction** valide la transaction, ce qui rend la modification du Registre effective.</span><span class="sxs-lookup"><span data-stu-id="57224-119">The **Complete-Transaction** command commits the transaction, which makes the registry change effective.</span></span>
<span data-ttu-id="57224-120">Par conséquent, la deuxième commande dir indique que le registre a été modifié.</span><span class="sxs-lookup"><span data-stu-id="57224-120">As a result, the second dir command shows that the registry is changed.</span></span>

### <span data-ttu-id="57224-121">Exemple 2 : valider une transaction qui a plusieurs abonnés</span><span class="sxs-lookup"><span data-stu-id="57224-121">Example 2: Commit a transaction that has more than one subscriber</span></span>

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

<span data-ttu-id="57224-122">Cet exemple montre comment utiliser la méthode **Complete-Transaction** pour valider une transaction qui a plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="57224-122">This example shows how to use **Complete-Transaction** to commit a transaction that has more than one subscriber.</span></span>

<span data-ttu-id="57224-123">Pour valider une transaction multi-abonné, vous devez entrer une commande **Complete-Transaction** pour chaque commande **start-transaction** .</span><span class="sxs-lookup"><span data-stu-id="57224-123">To commit a multi-subscriber transaction, you must enter one **Complete-Transaction** command for every **Start-Transaction** command.</span></span>
<span data-ttu-id="57224-124">Les données ne sont modifiées que lorsque la commande final **Complete-Transaction** est envoyée.</span><span class="sxs-lookup"><span data-stu-id="57224-124">The data is changed only when the final **Complete-Transaction** command is submitted.</span></span>

<span data-ttu-id="57224-125">À des fins de démonstration, cet exemple montre une série de commandes entrées au niveau de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="57224-125">For demonstration purposes, this example shows a series of commands entered at the command line.</span></span>
<span data-ttu-id="57224-126">Dans la pratique, les transactions sont susceptibles d’être exécutées dans des scripts, la transaction secondaire étant exécutée par un script de fonction ou d’application d’assistance appelé par le script principal.</span><span class="sxs-lookup"><span data-stu-id="57224-126">In practice, transactions are likely to be run in scripts, with the secondary transaction being run by a function or helper script that is called by the main script.</span></span>

<span data-ttu-id="57224-127">Dans cet exemple, une commande **start-transaction** démarre la transaction.</span><span class="sxs-lookup"><span data-stu-id="57224-127">In this example, a **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="57224-128">Une commande **New-Item** avec le paramètre *UseTransaction* ajoute la clé MyCompany à la clé du logiciel.</span><span class="sxs-lookup"><span data-stu-id="57224-128">A **New-Item** command with the *UseTransaction* parameter adds the MyCompany key to the Software key.</span></span>
<span data-ttu-id="57224-129">Bien que l’applet **de commande New-Item** retourne un objet clé, les données du registre ne sont pas encore modifiées.</span><span class="sxs-lookup"><span data-stu-id="57224-129">Although the **New-Item** cmdlet returns a key object, the data in the registry is not yet changed.</span></span>

<span data-ttu-id="57224-130">Une deuxième commande **start-transaction** ajoute un deuxième abonné à la transaction existante.</span><span class="sxs-lookup"><span data-stu-id="57224-130">A second **Start-Transaction** command adds a second subscriber to the existing transaction.</span></span>
<span data-ttu-id="57224-131">L’applet de commande **« obtient-transaction »** confirme que le nombre d’abonnés est 2.</span><span class="sxs-lookup"><span data-stu-id="57224-131">The **Get-Transaction** cmdlet confirms that the subscriber count is 2.</span></span>
<span data-ttu-id="57224-132">Une commande New-ItemProperty avec le paramètre *UseTransaction* ajoute une entrée de Registre à la nouvelle clé MyCompany.</span><span class="sxs-lookup"><span data-stu-id="57224-132">A New-ItemProperty command with the *UseTransaction* parameter adds a registry entry to the new MyCompany key.</span></span>
<span data-ttu-id="57224-133">Là encore, la commande retourne une valeur, mais le Registre n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="57224-133">Again, the command returns a value, but the registry is not changed.</span></span>

<span data-ttu-id="57224-134">La première commande **Complete-Transaction** réduit le nombre d’abonnés de 1.</span><span class="sxs-lookup"><span data-stu-id="57224-134">The first **Complete-Transaction** command reduces the subscriber count by 1.</span></span>
<span data-ttu-id="57224-135">Cette opération est confirmée par une commande d' **extraction de transaction** .</span><span class="sxs-lookup"><span data-stu-id="57224-135">This is confirmed by a **Get-Transaction** command.</span></span>
<span data-ttu-id="57224-136">Toutefois, aucune donnée n’est modifiée, comme l’atteste une commande dir m \* ( **obtenir-ChildItem** ).</span><span class="sxs-lookup"><span data-stu-id="57224-136">However, no data is changed, as evidenced by a dir m\* ( **Get-ChildItem** ) command.</span></span>

<span data-ttu-id="57224-137">La deuxième commande **Complete-Transaction** valide la transaction entière et modifie les données dans le registre.</span><span class="sxs-lookup"><span data-stu-id="57224-137">The second **Complete-Transaction** command commits the entire transaction and changes the data in the registry.</span></span>
<span data-ttu-id="57224-138">Elle est confirmée par une deuxième commande dir m \*, qui affiche les modifications.</span><span class="sxs-lookup"><span data-stu-id="57224-138">This is confirmed by a second dir m\* command, which shows the changes.</span></span>

### <span data-ttu-id="57224-139">Exemple 3 : exécuter une transaction qui ne modifie aucune donnée</span><span class="sxs-lookup"><span data-stu-id="57224-139">Example 3: Perform a transaction that does not change any data</span></span>

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

<span data-ttu-id="57224-140">Cet exemple montre la valeur de l’utilisation de commandes « obtenir » \* et d’autres commandes qui ne modifient pas les données dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="57224-140">This example shows the value of using Get-\* commands, and other commands that do not change data, in a transaction.</span></span>
<span data-ttu-id="57224-141">Lorsqu’une \* commande d’extraction est utilisée dans une transaction, elle obtient les objets qui font partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="57224-141">When a Get-\* command is used in a transaction, it gets the objects that are part of the transaction.</span></span>
<span data-ttu-id="57224-142">Cela vous permet d’afficher un aperçu des modifications apportées à la transaction avant de les valider.</span><span class="sxs-lookup"><span data-stu-id="57224-142">This allows you to preview the changes in the transaction before the changes are committed.</span></span>

<span data-ttu-id="57224-143">Dans cet exemple, une transaction est démarrée.</span><span class="sxs-lookup"><span data-stu-id="57224-143">In this example, a transaction is started.</span></span>
<span data-ttu-id="57224-144">Une commande New-Item avec le paramètre *UseTransaction* ajoute une nouvelle clé au registre dans le cadre de la transaction.</span><span class="sxs-lookup"><span data-stu-id="57224-144">A New-Item command with the *UseTransaction* parameter adds a new key to the registry as part of the transaction.</span></span>

<span data-ttu-id="57224-145">Étant donné que la nouvelle clé de Registre n’est pas ajoutée au Registre tant que la commande **Complete-Transaction** n’est pas exécutée, une simple commande dir ( **obtenir-ChildItem** ) affiche le registre sans la nouvelle clé.</span><span class="sxs-lookup"><span data-stu-id="57224-145">Because the new registry key is not added to the registry until the **Complete-Transaction** command is run, a simple dir ( **Get-ChildItem** ) command shows the registry without the new key.</span></span>

<span data-ttu-id="57224-146">Toutefois, lorsque vous ajoutez le paramètre *UseTransaction* à la commande dir, la commande devient partie intégrante de la transaction et elle obtient les éléments de la transaction même s’ils ne sont pas encore ajoutés aux données.</span><span class="sxs-lookup"><span data-stu-id="57224-146">However, when you add the *UseTransaction* parameter to the dir command, the command becomes part of the transaction, and it gets the items in the transaction even if they are not yet added to the data.</span></span>

## <span data-ttu-id="57224-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="57224-147">PARAMETERS</span></span>

### <span data-ttu-id="57224-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="57224-148">-Confirm</span></span>
<span data-ttu-id="57224-149">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="57224-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="57224-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="57224-150">-WhatIf</span></span>
<span data-ttu-id="57224-151">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="57224-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="57224-152">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="57224-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="57224-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="57224-153">CommonParameters</span></span>
<span data-ttu-id="57224-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="57224-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="57224-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="57224-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="57224-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="57224-156">INPUTS</span></span>

### <span data-ttu-id="57224-157">Aucun</span><span class="sxs-lookup"><span data-stu-id="57224-157">None</span></span>
<span data-ttu-id="57224-158">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="57224-158">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="57224-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="57224-159">OUTPUTS</span></span>

### <span data-ttu-id="57224-160">Aucun</span><span class="sxs-lookup"><span data-stu-id="57224-160">None</span></span>
<span data-ttu-id="57224-161">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="57224-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="57224-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="57224-162">NOTES</span></span>

* <span data-ttu-id="57224-163">Vous ne pouvez pas restaurer une transaction qui a été validée, ni valider une transaction qui a été restaurée.</span><span class="sxs-lookup"><span data-stu-id="57224-163">You cannot roll back a transaction that has been committed, or commit a transaction that has been rolled back.</span></span>

  <span data-ttu-id="57224-164">Vous ne pouvez pas restaurer une autre transaction que la transaction active.</span><span class="sxs-lookup"><span data-stu-id="57224-164">You cannot roll back any transaction other than the active transaction.</span></span>
<span data-ttu-id="57224-165">Pour restaurer une autre transaction, vous devez commencer par valider ou restaurer la transaction active.</span><span class="sxs-lookup"><span data-stu-id="57224-165">To roll back a different transaction, you must first commit or roll back the active transaction.</span></span>

  <span data-ttu-id="57224-166">En cas d’impossibilité de valider une partie d’une transaction (lorsqu’une commande dans la transaction génère une erreur, par exemple), la transaction est par défaut entièrement restaurée.</span><span class="sxs-lookup"><span data-stu-id="57224-166">By default, if any part of a transaction cannot be committed, such as when a command in the transaction results in an error, the entire transaction is rolled back.</span></span>

*

## <span data-ttu-id="57224-167">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="57224-167">RELATED LINKS</span></span>

[<span data-ttu-id="57224-168">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="57224-168">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="57224-169">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="57224-169">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="57224-170">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="57224-170">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="57224-171">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="57224-171">Use-Transaction</span></span>](Use-Transaction.md)

[<span data-ttu-id="57224-172">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="57224-172">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="57224-173">New-Item</span><span class="sxs-lookup"><span data-stu-id="57224-173">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="57224-174">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="57224-174">New-ItemProperty</span></span>](New-ItemProperty.md)
