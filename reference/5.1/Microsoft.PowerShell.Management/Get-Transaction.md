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
# <span data-ttu-id="44f73-103">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="44f73-103">Get-Transaction</span></span>

## <span data-ttu-id="44f73-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="44f73-104">SYNOPSIS</span></span>
<span data-ttu-id="44f73-105">Obtient la transaction actuelle (active).</span><span class="sxs-lookup"><span data-stu-id="44f73-105">Gets the current (active) transaction.</span></span>

## <span data-ttu-id="44f73-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="44f73-106">SYNTAX</span></span>

```
Get-Transaction [<CommonParameters>]
```

## <span data-ttu-id="44f73-107">Description</span><span class="sxs-lookup"><span data-stu-id="44f73-107">DESCRIPTION</span></span>
<span data-ttu-id="44f73-108">L’applet de commande **obtenir-transaction** obtient un objet qui représente la transaction actuelle dans la session.</span><span class="sxs-lookup"><span data-stu-id="44f73-108">The **Get-Transaction** cmdlet gets an object that represents the current transaction in the session.</span></span>

<span data-ttu-id="44f73-109">Cette applet de commande ne retourne jamais plusieurs objets, car une seule transaction est active à la fois.</span><span class="sxs-lookup"><span data-stu-id="44f73-109">This cmdlet never returns more than one object, because only one transaction is active at a time.</span></span>
<span data-ttu-id="44f73-110">Si vous démarrez une ou plusieurs transactions indépendantes (à l’aide du paramètre Independent de start-transaction), la transaction démarrée le plus récemment est active, et c’est la transaction que l’opération d' **extraction de transaction** a retournée.</span><span class="sxs-lookup"><span data-stu-id="44f73-110">If you start one or more independent transactions (by using the Independent parameter of Start-Transaction), the most recently started transaction is active, and that is the transaction that **Get-Transaction** returns.</span></span>

<span data-ttu-id="44f73-111">Lorsque toutes les transactions actives ont été restaurées ou validées, cette applet de commande affiche la transaction qui a été active en dernier dans la session.</span><span class="sxs-lookup"><span data-stu-id="44f73-111">When all active transactions have either been rolled back or committed, this cmdlet shows the transaction that was most recently active in the session.</span></span>

<span data-ttu-id="44f73-112">Cette applet de commande est l’un des ensembles d’applets de commande qui prennent en charge la fonctionnalité des transactions dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44f73-112">This cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="44f73-113">Pour plus d'informations, consultez about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="44f73-113">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="44f73-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="44f73-114">EXAMPLES</span></span>

### <span data-ttu-id="44f73-115">Exemple 1 : récupération de la transaction en cours</span><span class="sxs-lookup"><span data-stu-id="44f73-115">Example 1: Get the current transaction</span></span>

```
PS C:\> Start-Transaction
PS C:\> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="44f73-116">Cette commande utilise l'applet de commande Get-Transaction pour obtenir la transaction actuelle.</span><span class="sxs-lookup"><span data-stu-id="44f73-116">This command uses the Get-Transaction cmdlet to get the current transaction.</span></span>

### <span data-ttu-id="44f73-117">Exemple 2 : afficher les propriétés et les méthodes de l’objet transaction</span><span class="sxs-lookup"><span data-stu-id="44f73-117">Example 2: Show the properties and methods of the transaction object</span></span>

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

<span data-ttu-id="44f73-118">Cette commande utilise l'applet de commande Get-Member pour afficher les propriétés et les méthodes de l'objet transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-118">This command uses the Get-Member cmdlet to show the properties and methods of the transaction object.</span></span>

### <span data-ttu-id="44f73-119">Exemple 3 : afficher les valeurs de propriété d’une transaction restaurée</span><span class="sxs-lookup"><span data-stu-id="44f73-119">Example 3: Show the property values of a rolled back transaction</span></span>

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

<span data-ttu-id="44f73-120">Cette commande affiche les valeurs de propriété d'un objet transaction d'une transaction restaurée.</span><span class="sxs-lookup"><span data-stu-id="44f73-120">This command shows the property values of a transaction object for a transaction that has been rolled back.</span></span>

### <span data-ttu-id="44f73-121">Exemple 4 : afficher les valeurs de propriété d’une transaction validée</span><span class="sxs-lookup"><span data-stu-id="44f73-121">Example 4: Show the property values of a committed transaction</span></span>

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

<span data-ttu-id="44f73-122">Cette commande affiche les valeurs de propriété d'un objet transaction d'une transaction validée.</span><span class="sxs-lookup"><span data-stu-id="44f73-122">This command shows the property values of a transaction object for a transaction that has been committed.</span></span>

### <span data-ttu-id="44f73-123">Exemple 5 : démarrer une transaction pendant qu’une autre est en cours</span><span class="sxs-lookup"><span data-stu-id="44f73-123">Example 5: Start a transaction while another is in progress</span></span>

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

<span data-ttu-id="44f73-124">Cet exemple illustre le démarrage d'une transaction pendant qu'une autre transaction est en cours et ses effets sur l'objet transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-124">This example shows the effect on the transaction object of starting a transaction while another transaction is in progress.</span></span>
<span data-ttu-id="44f73-125">En général, cela se produit lorsqu'un script qui exécute une transaction inclut une fonction ou appelle un script qui contient une autre transaction complète.</span><span class="sxs-lookup"><span data-stu-id="44f73-125">Typically, this happens when a script that runs a transaction includes a function or calls a script that contains another complete transaction.</span></span>

<span data-ttu-id="44f73-126">À moins que la deuxième commande **start-transaction** inclue le paramètre *Independent* , **start-transaction** ne crée pas de nouvelle transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-126">Unless the second **Start-Transaction** command includes the *Independent* parameter, **Start-Transaction** does not create a new transaction.</span></span>
<span data-ttu-id="44f73-127">Au lieu de cela, elle ajoute un deuxième abonné à la transaction d'origine.</span><span class="sxs-lookup"><span data-stu-id="44f73-127">Instead, it adds a second subscriber to the original transaction.</span></span>

<span data-ttu-id="44f73-128">La première commande **start-transaction** démarre la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-128">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="44f73-129">Une commande New-Item avec le paramètre *UseTransaction* fait partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-129">A New-Item command with the *UseTransaction* parameter is part of the transaction.</span></span>

<span data-ttu-id="44f73-130">Une deuxième commande **start-transaction** ajoute un abonné à la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-130">A second **Start-Transaction** command adds a subscriber to the transaction.</span></span>
<span data-ttu-id="44f73-131">La commande New-Item suivante fait également partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-131">The next New-Item command is also part of the transaction.</span></span>

<span data-ttu-id="44f73-132">La première commande d' **extraction de transaction** affiche la transaction multi-abonnés.</span><span class="sxs-lookup"><span data-stu-id="44f73-132">The first **Get-Transaction** command shows the multi-subscriber transaction.</span></span>
<span data-ttu-id="44f73-133">Notez que le nombre d'abonnés a la valeur 2.</span><span class="sxs-lookup"><span data-stu-id="44f73-133">Notice that the subscriber count is 2.</span></span>

<span data-ttu-id="44f73-134">La première commande Complete-Transaction ne valide pas la transaction, mais elle réduit le nombre d'abonnés à 1.</span><span class="sxs-lookup"><span data-stu-id="44f73-134">The first Complete-Transaction command does not commit the transaction, but it reduces the subscriber count to 1.</span></span>

<span data-ttu-id="44f73-135">La deuxième commande **Complete-Transaction** valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-135">The second **Complete-Transaction** command commits the transaction.</span></span>

### <span data-ttu-id="44f73-136">Exemple 6 : démarrer une transaction indépendante pendant qu’une autre est en cours</span><span class="sxs-lookup"><span data-stu-id="44f73-136">Example 6: Start an independent transaction while another is in progress</span></span>

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

<span data-ttu-id="44f73-137">Cet exemple illustre le démarrage d'une transaction indépendante pendant qu'une autre transaction est en cours et ses effets sur l'objet transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-137">This example shows the effect on the transaction object of starting an independent transaction while another transaction is in progress.</span></span>

<span data-ttu-id="44f73-138">La première commande **start-transaction** démarre la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-138">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="44f73-139">Une commande **New-Item** avec le paramètre *UseTransaction* fait partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-139">A **New-Item** command with the *UseTransaction* parameter is part of the transaction.</span></span>

<span data-ttu-id="44f73-140">Une deuxième commande **start-transaction** ajoute un abonné à la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-140">A second **Start-Transaction** command adds a subscriber to the transaction.</span></span>
<span data-ttu-id="44f73-141">La commande **New-Item** suivante fait également partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-141">The next **New-Item** command is also part of the transaction.</span></span>

<span data-ttu-id="44f73-142">La première commande d' **extraction de transaction** affiche la transaction multi-abonnés.</span><span class="sxs-lookup"><span data-stu-id="44f73-142">The first **Get-Transaction** command shows the multi-subscriber transaction.</span></span>
<span data-ttu-id="44f73-143">Notez que le nombre d'abonnés a la valeur 2.</span><span class="sxs-lookup"><span data-stu-id="44f73-143">Note that the subscriber count is 2.</span></span>

<span data-ttu-id="44f73-144">La commande **Complete-Transaction** réduit le nombre d’abonnés à 1, mais elle ne valide pas la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-144">The **Complete-Transaction** command reduces the subscriber count to 1, but it does not commit the transaction.</span></span>

<span data-ttu-id="44f73-145">La deuxième commande **Complete-Transaction** valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="44f73-145">The second **Complete-Transaction** command commits the transaction.</span></span>

## <span data-ttu-id="44f73-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="44f73-146">PARAMETERS</span></span>

### <span data-ttu-id="44f73-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="44f73-147">CommonParameters</span></span>
<span data-ttu-id="44f73-148">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="44f73-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="44f73-149">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="44f73-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="44f73-150">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="44f73-150">INPUTS</span></span>

### <span data-ttu-id="44f73-151">Aucun</span><span class="sxs-lookup"><span data-stu-id="44f73-151">None</span></span>
<span data-ttu-id="44f73-152">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="44f73-152">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="44f73-153">SORTIES</span><span class="sxs-lookup"><span data-stu-id="44f73-153">OUTPUTS</span></span>

### <span data-ttu-id="44f73-154">System. Management. Automation. PSTransaction</span><span class="sxs-lookup"><span data-stu-id="44f73-154">System.Management.Automation.PSTransaction</span></span>
<span data-ttu-id="44f73-155">Cette applet de commande retourne un objet qui représente la transaction actuelle.</span><span class="sxs-lookup"><span data-stu-id="44f73-155">This cmdlet returns an object that represents the current transaction.</span></span>

## <span data-ttu-id="44f73-156">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="44f73-156">NOTES</span></span>

## <span data-ttu-id="44f73-157">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="44f73-157">RELATED LINKS</span></span>

[<span data-ttu-id="44f73-158">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="44f73-158">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="44f73-159">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="44f73-159">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="44f73-160">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="44f73-160">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="44f73-161">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="44f73-161">Use-Transaction</span></span>](Use-Transaction.md)

[<span data-ttu-id="44f73-162">New-Item</span><span class="sxs-lookup"><span data-stu-id="44f73-162">New-Item</span></span>](New-Item.md)
