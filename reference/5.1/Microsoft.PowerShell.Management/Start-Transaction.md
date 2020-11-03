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
# <span data-ttu-id="c10c9-103">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="c10c9-103">Start-Transaction</span></span>

## <span data-ttu-id="c10c9-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c10c9-104">SYNOPSIS</span></span>
<span data-ttu-id="c10c9-105">Démarre une transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-105">Starts a transaction.</span></span>

## <span data-ttu-id="c10c9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c10c9-106">SYNTAX</span></span>

```
Start-Transaction [-Timeout <Int32>] [-Independent] [-RollbackPreference <RollbackSeverity>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c10c9-107">Description</span><span class="sxs-lookup"><span data-stu-id="c10c9-107">DESCRIPTION</span></span>
<span data-ttu-id="c10c9-108">L’applet de commande **start-transaction** démarre une transaction, qui est une série de commandes gérées en tant qu’unité.</span><span class="sxs-lookup"><span data-stu-id="c10c9-108">The **Start-Transaction** cmdlet starts a transaction, which is a series of commands that are managed as a unit.</span></span>
<span data-ttu-id="c10c9-109">Une transaction peut être terminée ou validée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-109">A transaction can be completed, or committed.</span></span>
<span data-ttu-id="c10c9-110">Elle peut également être complètement annulée, ou restaurée, de sorte que toutes les données modifiées par la transaction sont restaurées à leur état d’origine.</span><span class="sxs-lookup"><span data-stu-id="c10c9-110">Alternatively, it can be completely undone, or rolled back, so that any data changed by the transaction is restored to its original state.</span></span>
<span data-ttu-id="c10c9-111">Comme les commandes figurant dans une transaction sont gérées en bloc, toutes les commandes sont soit validées soit restaurées.</span><span class="sxs-lookup"><span data-stu-id="c10c9-111">Because the commands in a transaction are managed as a unit, either all commands are committed or all commands are rolled back.</span></span>

<span data-ttu-id="c10c9-112">Par défaut, si une commande de la transaction génère une erreur, les transactions sont restaurées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c10c9-112">By default, if any command in the transaction generates an error, transactions are rolled back automatically.</span></span>
<span data-ttu-id="c10c9-113">Vous pouvez utiliser le paramètre *RollbackPreference* pour modifier ce comportement.</span><span class="sxs-lookup"><span data-stu-id="c10c9-113">You can use the *RollbackPreference* parameter to change this behavior.</span></span>

<span data-ttu-id="c10c9-114">Les applets de commande utilisées dans une transaction doivent être conçues pour prendre en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="c10c9-114">The cmdlets used in a transaction must be designed to support transactions.</span></span>
<span data-ttu-id="c10c9-115">Les applets de commande qui prennent en charge les transactions ont un paramètre *UseTransaction* .</span><span class="sxs-lookup"><span data-stu-id="c10c9-115">Cmdlets that support transactions have a *UseTransaction* parameter.</span></span>
<span data-ttu-id="c10c9-116">Pour exécuter des transactions dans un fournisseur, le fournisseur doit prendre en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="c10c9-116">To perform transactions in a provider, the provider must support transactions.</span></span>
<span data-ttu-id="c10c9-117">Le fournisseur de Registre Windows PowerShell dans Windows Vista et les versions ultérieures du système d’exploitation Windows prend en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="c10c9-117">The Windows PowerShell Registry provider in Windows Vista and later versions of the Windows operating system supports transactions.</span></span>
<span data-ttu-id="c10c9-118">Vous pouvez également utiliser la classe **Microsoft. PowerShell. Commands. Management. TransactedString** pour inclure des expressions dans les transactions sur toute version du système Windows qui prend en charge Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c10c9-118">You can also use the **Microsoft.PowerShell.Commands.Management.TransactedString** class to include expressions in transactions on any version of the Windows system that supports Windows PowerShell.</span></span>
<span data-ttu-id="c10c9-119">D’autres fournisseurs Windows PowerShell peuvent également prendre en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="c10c9-119">Other Windows PowerShell providers can also support transactions.</span></span>

<span data-ttu-id="c10c9-120">Une seule transaction peut être active à la fois.</span><span class="sxs-lookup"><span data-stu-id="c10c9-120">Only one transaction can be active at a time.</span></span>
<span data-ttu-id="c10c9-121">Si vous démarrez une nouvelle transaction indépendante pendant qu’une transaction est en cours, la nouvelle transaction devient la transaction active et vous devez valider ou restaurer la nouvelle transaction avant d’apporter des modifications à la transaction d’origine.</span><span class="sxs-lookup"><span data-stu-id="c10c9-121">If you start a new, independent transaction while a transaction is in progress, the new transaction becomes the active transaction, and you must commit or roll back the new transaction before you make any changes to the original transaction.</span></span>

<span data-ttu-id="c10c9-122">L’applet de commande **start-transaction** fait partie d’un ensemble d’applets de commande qui prennent en charge la fonctionnalité des transactions dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c10c9-122">**Start-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="c10c9-123">Pour plus d'informations, consultez about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="c10c9-123">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="c10c9-124">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c10c9-124">EXAMPLES</span></span>

### <span data-ttu-id="c10c9-125">Exemple 1 : Démarrer et restaurer une transaction</span><span class="sxs-lookup"><span data-stu-id="c10c9-125">Example 1: Start and roll back a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Undo-Transaction
```

<span data-ttu-id="c10c9-126">Ces commandes démarrent une transaction, puis la restaurent.</span><span class="sxs-lookup"><span data-stu-id="c10c9-126">These commands start and then roll back a transaction.</span></span>
<span data-ttu-id="c10c9-127">Comme la transaction est restaurée, aucune modification n’est apportée au Registre.</span><span class="sxs-lookup"><span data-stu-id="c10c9-127">Because the transaction is rolled back, no changes are made to the registry.</span></span>

### <span data-ttu-id="c10c9-128">Exemple 2 : Démarrer et terminer une transaction</span><span class="sxs-lookup"><span data-stu-id="c10c9-128">Example 2: Start and complete a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
```

<span data-ttu-id="c10c9-129">Ces commandes démarrent une transaction, puis l’exécutent.</span><span class="sxs-lookup"><span data-stu-id="c10c9-129">These commands start and then complete a transaction.</span></span>
<span data-ttu-id="c10c9-130">Aucune modification n’est apportée au Registre tant que la commande **Complete-Transaction** n’est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-130">No changes are made to the registry until the **Complete-Transaction** command is used.</span></span>

### <span data-ttu-id="c10c9-131">Exemple 3 : utiliser des préférences de restauration différentes</span><span class="sxs-lookup"><span data-stu-id="c10c9-131">Example 3: Use different rollback preferences</span></span>

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

<span data-ttu-id="c10c9-132">Cet exemple illustre l’effet de la modification de la valeur du paramètre *RollbackPreference* .</span><span class="sxs-lookup"><span data-stu-id="c10c9-132">This example demonstrates the effect of changing the *RollbackPreference* parameter value.</span></span>

<span data-ttu-id="c10c9-133">Dans le premier jeu de commandes, **start-transaction** n’utilise pas *RollbackPreference* .</span><span class="sxs-lookup"><span data-stu-id="c10c9-133">In the first set of commands, **Start-Transaction** does not use *RollbackPreference* .</span></span>
<span data-ttu-id="c10c9-134">Par conséquent, la valeur par défaut (Error) est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-134">As a result, the default value (Error) is used.</span></span>
<span data-ttu-id="c10c9-135">Lorsqu’une erreur se produit dans une commande de transaction, autrement dit, si le chemin d’accès spécifié n’existe pas, la transaction est automatiquement restaurée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-135">When an error occurs in a transaction command, that is, the specified path does not exist, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="c10c9-136">Dans le deuxième jeu de commandes, **start-transaction** utilise *RollbackPreference* avec la valeur Never.</span><span class="sxs-lookup"><span data-stu-id="c10c9-136">In the second set of commands, **Start-Transaction** uses *RollbackPreference* with a value of Never.</span></span>
<span data-ttu-id="c10c9-137">Lorsqu’une erreur se produit dans une commande de transaction, la transaction est par conséquent encore active et peut être exécutée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-137">As a result, when an error occurs in a transaction command, the transaction is still active and can be completed successfully.</span></span>

<span data-ttu-id="c10c9-138">Étant donné que la plupart des transactions doivent être exécutées sans erreur, la valeur par défaut de *RollbackPreference* est généralement préférée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-138">Because most transactions must be performed without error, the default value of *RollbackPreference* is typically preferred.</span></span>

### <span data-ttu-id="c10c9-139">Exemple 4 : utilisez cette applet de commande pendant qu’une transaction est en cours</span><span class="sxs-lookup"><span data-stu-id="c10c9-139">Example 4: Use this cmdlet while a transaction is in progress</span></span>

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

<span data-ttu-id="c10c9-140">Cet exemple montre l’effet de l’utilisation de **start-transaction** pendant qu’une transaction est en cours.</span><span class="sxs-lookup"><span data-stu-id="c10c9-140">This example shows the effect of using **Start-Transaction** while a transaction is in progress.</span></span>
<span data-ttu-id="c10c9-141">L’effet est similaire à la jonction de la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="c10c9-141">The effect is much like joining the transaction in progress.</span></span>

<span data-ttu-id="c10c9-142">Bien qu’il s’agisse d’une commande simplifiée, ce scénario se produit souvent lorsque la transaction implique l’exécution d’un script qui inclut une transaction complète.</span><span class="sxs-lookup"><span data-stu-id="c10c9-142">Although this is a simplified command, this scenario frequently occurs when the transaction involves running a script that includes a complete transaction.</span></span>

<span data-ttu-id="c10c9-143">La première commande **start-transaction** démarre la transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-143">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="c10c9-144">La première commande **New-Item** fait partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-144">The first **New-Item** command is part of the transaction.</span></span>

<span data-ttu-id="c10c9-145">La deuxième commande **start-transaction** ajoute un nouvel abonné à la transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-145">The second **Start-Transaction** command adds a new subscriber to the transaction.</span></span>
<span data-ttu-id="c10c9-146">La commande **obtenir-transaction** retourne désormais une transaction avec un nombre d’abonnés de 2.</span><span class="sxs-lookup"><span data-stu-id="c10c9-146">The **Get-Transaction** command now returns a transaction with a subscriber count of 2.</span></span>
<span data-ttu-id="c10c9-147">La deuxième commande **New-Item** fait partie de la même transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-147">The second **New-Item** command is part of the same transaction.</span></span>

<span data-ttu-id="c10c9-148">Aucune modification n’est apportée au Registre tant que l’intégralité de la transaction n’est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-148">No changes are made to the registry until the whole transaction is completed.</span></span>
<span data-ttu-id="c10c9-149">Pour terminer la transaction, vous devez entrer deux commandes **Complete-Transaction** , une pour chaque abonné.</span><span class="sxs-lookup"><span data-stu-id="c10c9-149">To complete the transaction, you must enter two **Complete-Transaction** commands, one for each subscriber.</span></span>
<span data-ttu-id="c10c9-150">Si vous deviez restaurer la transaction à tout moment, toute la transaction est restaurée pour les deux abonnés.</span><span class="sxs-lookup"><span data-stu-id="c10c9-150">If you were to roll back the transaction at any point, all the transaction would be rolled back for both subscribers.</span></span>

### <span data-ttu-id="c10c9-151">Exemple 5 : démarrer une transaction indépendante pendant qu’une transaction est en cours</span><span class="sxs-lookup"><span data-stu-id="c10c9-151">Example 5: Start an independent transaction while one is in progress</span></span>

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

<span data-ttu-id="c10c9-152">Cet exemple montre l’effet de l’utilisation du paramètre *Independent* de **start-transaction** pour démarrer une transaction pendant qu’une autre transaction est en cours.</span><span class="sxs-lookup"><span data-stu-id="c10c9-152">This example shows the effect of using the *Independent* parameter of **Start-Transaction** to start a transaction while another transaction is in progress.</span></span>
<span data-ttu-id="c10c9-153">Dans ce cas, la nouvelle transaction est restaurée sans affecter la transaction d’origine.</span><span class="sxs-lookup"><span data-stu-id="c10c9-153">In this case, the new transaction is rolled back without affecting the original transaction.</span></span>

<span data-ttu-id="c10c9-154">Même si les transactions sont logiquement indépendantes, comme une seule transaction peut être active à la fois, vous devez restaurer ou valider la transaction la plus récente avant de reprendre le travail sur la transaction d’origine.</span><span class="sxs-lookup"><span data-stu-id="c10c9-154">Although the transactions are logically independent, because only one transaction can be active at a time, you must roll back or commit the newest transaction before resuming work on the original transaction.</span></span>

<span data-ttu-id="c10c9-155">Le premier jeu de commandes démarre une transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-155">The first set of commands starts a transaction.</span></span>
<span data-ttu-id="c10c9-156">La commande **New-Item** fait partie de la première transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-156">The **New-Item** command is part of the first transaction.</span></span>

<span data-ttu-id="c10c9-157">Dans le deuxième jeu de commandes, la commande **start-transaction** utilise le paramètre *Independent* .</span><span class="sxs-lookup"><span data-stu-id="c10c9-157">In the second set of commands, the **Start-Transaction** command uses the *Independent* parameter.</span></span>
<span data-ttu-id="c10c9-158">La commande **obtenir une transaction** qui suit affiche l’objet transaction de la transaction active, qui est la plus récente.</span><span class="sxs-lookup"><span data-stu-id="c10c9-158">The **Get-Transaction** command that follows shows the transaction object for the active transaction, which is the newest one.</span></span>
<span data-ttu-id="c10c9-159">Le nombre d’abonnés est égal à 1, ce qui indique que les transactions ne sont pas liées.</span><span class="sxs-lookup"><span data-stu-id="c10c9-159">The subscriber count is equal to 1, that shows that the transactions are unrelated.</span></span>

<span data-ttu-id="c10c9-160">Lorsque la transaction active est restaurée à l’aide d’une commande **Undo-Transaction** , la transaction d’origine redevient active.</span><span class="sxs-lookup"><span data-stu-id="c10c9-160">When the active transaction is rolled back by using an **Undo-Transaction** command, the original transaction becomes active again.</span></span>

<span data-ttu-id="c10c9-161">La commande **New-ItemProperty** , qui fait partie de la transaction d’origine, se termine sans erreur et la transaction d’origine peut être exécutée à l’aide de la commande **Complete-Transaction** .</span><span class="sxs-lookup"><span data-stu-id="c10c9-161">The **New-ItemProperty** command, which is part of the original transaction, finishes without error, and the original transaction can be completed by using the **Complete-Transaction** command.</span></span>
<span data-ttu-id="c10c9-162">Le Registre est par conséquent modifié.</span><span class="sxs-lookup"><span data-stu-id="c10c9-162">As a result, the registry is changed.</span></span>

### <span data-ttu-id="c10c9-163">Exemple 6 : exécuter des commandes qui ne font pas partie d’une transaction</span><span class="sxs-lookup"><span data-stu-id="c10c9-163">Example 6: Run commands that are not part of a transaction</span></span>

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

<span data-ttu-id="c10c9-164">Cet exemple montre que les commandes qui sont envoyées pendant qu’une transaction est en cours peuvent être incluses ou non dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-164">This example demonstrates that commands that are submitted while a transaction is in progress can be included in the transaction or not included.</span></span>
<span data-ttu-id="c10c9-165">Seules les commandes qui utilisent le paramètre *UseTransaction* font partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-165">Only commands that use the *UseTransaction* parameter are part of the transaction.</span></span>

<span data-ttu-id="c10c9-166">La première et la troisième commandes **New-Item** utilisent le paramètre *UseTransaction* .</span><span class="sxs-lookup"><span data-stu-id="c10c9-166">The first and third **New-Item** commands use the *UseTransaction* parameter.</span></span>
<span data-ttu-id="c10c9-167">Ces commandes font partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-167">These commands are part of the transaction.</span></span>
<span data-ttu-id="c10c9-168">Étant donné que la deuxième commande **New-Item** n’utilise pas le paramètre *UseTransaction* , elle ne fait pas partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-168">Because the second **New-Item** command does not use the *UseTransaction* parameter, it is not part of the transaction.</span></span>

<span data-ttu-id="c10c9-169">La première commande dir montre l’effet.</span><span class="sxs-lookup"><span data-stu-id="c10c9-169">The first dir command shows the effect.</span></span>
<span data-ttu-id="c10c9-170">La deuxième commande **New-Item** est exécutée immédiatement, mais la première et la troisième commandes **New-Item** ne sont pas effectives tant que la transaction n’est pas validée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-170">The second **New-Item** command is completed immediately, but the first and third **New-Item** commands are not effective until the transaction is committed.</span></span>

<span data-ttu-id="c10c9-171">La commande **Complete-Transaction** valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-171">The **Complete-Transaction** command commits the transaction.</span></span>
<span data-ttu-id="c10c9-172">Par conséquent, la deuxième commande dir indique que tous les nouveaux éléments sont ajoutés au registre.</span><span class="sxs-lookup"><span data-stu-id="c10c9-172">As a result, the second dir command shows that all of the new items are added to the registry.</span></span>

### <span data-ttu-id="c10c9-173">Exemple 7 : restaurer une transaction qui ne se termine pas dans un délai spécifié</span><span class="sxs-lookup"><span data-stu-id="c10c9-173">Example 7: Roll back a transaction that does not finish in a specified time</span></span>

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

<span data-ttu-id="c10c9-174">Cette commande utilise le paramètre *timeout* de **start-transaction** pour démarrer une transaction qui doit être effectuée dans les deux minutes.</span><span class="sxs-lookup"><span data-stu-id="c10c9-174">This command uses the *Timeout* parameter of **Start-Transaction** to start a transaction that must be completed within two minutes.</span></span>
<span data-ttu-id="c10c9-175">Si la transaction n’est pas terminée lorsque le délai d’attente expire, elle est automatiquement restaurée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-175">If the transaction is not finished when the time-out expires, it is rolled back automatically.</span></span>

<span data-ttu-id="c10c9-176">Lorsque le délai d’attente expire, vous n’êtes pas notifié, mais la propriété **Status** de l’objet transaction est définie sur valeur RolledBack et les commandes qui utilisent le paramètre *UseTransaction* échouent.</span><span class="sxs-lookup"><span data-stu-id="c10c9-176">When the time-out expires, you are not notified, but the **Status** property of the transaction object is set to RolledBack and commands that use the *UseTransaction* parameter fail.</span></span>

## <span data-ttu-id="c10c9-177">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c10c9-177">PARAMETERS</span></span>

### <span data-ttu-id="c10c9-178">-Indépendant</span><span class="sxs-lookup"><span data-stu-id="c10c9-178">-Independent</span></span>
<span data-ttu-id="c10c9-179">Indique que cette applet de commande démarre une transaction qui est indépendante de toutes les transactions en cours.</span><span class="sxs-lookup"><span data-stu-id="c10c9-179">Indicates that this cmdlet starts a transaction that is independent of any transactions in progress.</span></span>
<span data-ttu-id="c10c9-180">Par défaut, si vous utilisez **start-transaction** pendant qu’une autre transaction est en cours, un nouvel abonné est ajouté à la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="c10c9-180">By default, if you use **Start-Transaction** while another transaction is in progress, a new subscriber is added to the transaction in progress.</span></span>
<span data-ttu-id="c10c9-181">Ce paramètre prend uniquement effet lorsqu’une transaction est déjà en cours dans la session.</span><span class="sxs-lookup"><span data-stu-id="c10c9-181">This parameter has an effect only when a transaction is already in progress in the session.</span></span>

<span data-ttu-id="c10c9-182">Par défaut, si vous utilisez **start-transaction** pendant qu’une transaction est en cours, l’objet transaction existant est réutilisé et le nombre d’abonnés est incrémenté.</span><span class="sxs-lookup"><span data-stu-id="c10c9-182">By default, if you use **Start-Transaction** while a transaction is in progress, the existing transaction object is reused and the subscriber count is incremented.</span></span>
<span data-ttu-id="c10c9-183">L’effet est similaire à la jonction de la transaction d’origine.</span><span class="sxs-lookup"><span data-stu-id="c10c9-183">The effect is much like joining the original transaction.</span></span>
<span data-ttu-id="c10c9-184">Une commande Undo-Transaction restaure l’ensemble de la transaction.</span><span class="sxs-lookup"><span data-stu-id="c10c9-184">An Undo-Transaction command rolls back the whole the transaction.</span></span>
<span data-ttu-id="c10c9-185">Pour exécuter la transaction, vous devez entrer une commande Complete-Transaction pour chaque abonné.</span><span class="sxs-lookup"><span data-stu-id="c10c9-185">To complete the transaction, you must enter a Complete-Transaction command for each subscriber.</span></span>
<span data-ttu-id="c10c9-186">Comme la plupart des transactions qui sont simultanément en cours sont liées, la valeur par défaut est suffisante dans la majorité des cas.</span><span class="sxs-lookup"><span data-stu-id="c10c9-186">Because most transactions that are in progress at the same time are related, the default is sufficient for most uses.</span></span>

<span data-ttu-id="c10c9-187">Si vous spécifiez le paramètre *Independent* , cette applet de commande crée une nouvelle transaction qui peut être terminée ou annulée sans affecter la transaction d’origine.</span><span class="sxs-lookup"><span data-stu-id="c10c9-187">If you specify the *Independent* parameter, this cmdlet creates a new transaction that can be completed or undone without affecting the original transaction.</span></span>
<span data-ttu-id="c10c9-188">Comme une seule transaction peut être active à la fois, vous devez toutefois exécuter ou restaurer la nouvelle transaction avant de reprendre le travail sur la transaction d’origine.</span><span class="sxs-lookup"><span data-stu-id="c10c9-188">However, because only one transaction can be active at a time, you must complete or roll back the new transaction before resuming work on the original transaction.</span></span>

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

### <span data-ttu-id="c10c9-189">-RollbackPreference</span><span class="sxs-lookup"><span data-stu-id="c10c9-189">-RollbackPreference</span></span>
<span data-ttu-id="c10c9-190">Spécifie les conditions dans lesquelles une transaction est automatiquement restaurée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-190">Specifies the conditions under which a transaction is automatically rolled back.</span></span>
<span data-ttu-id="c10c9-191">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c10c9-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c10c9-192">Erreur.</span><span class="sxs-lookup"><span data-stu-id="c10c9-192">Error.</span></span>
<span data-ttu-id="c10c9-193">la transaction est automatiquement restaurée en cas d'erreur avec ou sans fin d'exécution.</span><span class="sxs-lookup"><span data-stu-id="c10c9-193">The transaction is rolled back automatically if a terminating or non-terminating error occurs.</span></span>
- <span data-ttu-id="c10c9-194">TerminatingError.</span><span class="sxs-lookup"><span data-stu-id="c10c9-194">TerminatingError.</span></span>
<span data-ttu-id="c10c9-195">la transaction est automatiquement restaurée en cas d'erreur avec fin d'exécution.</span><span class="sxs-lookup"><span data-stu-id="c10c9-195">The transaction is rolled back automatically if a terminating error occurs.</span></span>
- <span data-ttu-id="c10c9-196">Jamais.</span><span class="sxs-lookup"><span data-stu-id="c10c9-196">Never.</span></span>
<span data-ttu-id="c10c9-197">la transaction n'est jamais restaurée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c10c9-197">The transaction is never rolled back automatically.</span></span>

<span data-ttu-id="c10c9-198">La valeur par défaut est Error.</span><span class="sxs-lookup"><span data-stu-id="c10c9-198">The default value is Error.</span></span>

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

### <span data-ttu-id="c10c9-199">-Timeout</span><span class="sxs-lookup"><span data-stu-id="c10c9-199">-Timeout</span></span>
<span data-ttu-id="c10c9-200">Spécifie la durée maximale d’activité de la transaction (en minutes).</span><span class="sxs-lookup"><span data-stu-id="c10c9-200">Specifies the maximum time, in minutes, that the transaction is active.</span></span>
<span data-ttu-id="c10c9-201">Lorsque le délai d’attente expire, la transaction est automatiquement restaurée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-201">When the time-out expires, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="c10c9-202">Par défaut, aucun délai d’attente n’est défini pour les transactions qui sont démarrées au niveau de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c10c9-202">By default, there is no time-out for transactions that are started at the command line.</span></span>
<span data-ttu-id="c10c9-203">Lorsque les transactions sont démarrées par un script, le délai d’attente par défaut est de 30 minutes.</span><span class="sxs-lookup"><span data-stu-id="c10c9-203">When transactions are started by a script, the default time-out is 30 minutes.</span></span>

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

### <span data-ttu-id="c10c9-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c10c9-204">-Confirm</span></span>
<span data-ttu-id="c10c9-205">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c10c9-205">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c10c9-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c10c9-206">-WhatIf</span></span>
<span data-ttu-id="c10c9-207">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c10c9-207">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c10c9-208">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="c10c9-208">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c10c9-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c10c9-209">CommonParameters</span></span>
<span data-ttu-id="c10c9-210">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c10c9-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c10c9-211">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c10c9-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c10c9-212">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c10c9-212">INPUTS</span></span>

### <span data-ttu-id="c10c9-213">Aucun</span><span class="sxs-lookup"><span data-stu-id="c10c9-213">None</span></span>
<span data-ttu-id="c10c9-214">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c10c9-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c10c9-215">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c10c9-215">OUTPUTS</span></span>

### <span data-ttu-id="c10c9-216">Aucun</span><span class="sxs-lookup"><span data-stu-id="c10c9-216">None</span></span>
<span data-ttu-id="c10c9-217">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="c10c9-217">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c10c9-218">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c10c9-218">NOTES</span></span>

## <span data-ttu-id="c10c9-219">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c10c9-219">RELATED LINKS</span></span>

[<span data-ttu-id="c10c9-220">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="c10c9-220">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="c10c9-221">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="c10c9-221">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="c10c9-222">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="c10c9-222">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="c10c9-223">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="c10c9-223">Use-Transaction</span></span>](Use-Transaction.md)
