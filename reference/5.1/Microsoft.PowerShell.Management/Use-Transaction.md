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
# <span data-ttu-id="1d3a4-103">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="1d3a4-103">Use-Transaction</span></span>

## <span data-ttu-id="1d3a4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1d3a4-104">SYNOPSIS</span></span>
<span data-ttu-id="1d3a4-105">Ajoute le bloc de script à la transaction active.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-105">Adds the script block to the active transaction.</span></span>

## <span data-ttu-id="1d3a4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1d3a4-106">SYNTAX</span></span>

```
Use-Transaction [-TransactedScript] <ScriptBlock> [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="1d3a4-107">Description</span><span class="sxs-lookup"><span data-stu-id="1d3a4-107">DESCRIPTION</span></span>
<span data-ttu-id="1d3a4-108">L’applet de commande **use-transaction** ajoute un bloc de script à une transaction active.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-108">The **Use-Transaction** cmdlet adds a script block to an active transaction.</span></span>
<span data-ttu-id="1d3a4-109">Cela vous permet d’effectuer des scripts transactionnels à l’aide d’objets de l’infrastructure Microsoft .NET de transactions.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-109">This enables you to do transacted scripting by using transaction-enabled Microsoft .NET Framework objects.</span></span>
<span data-ttu-id="1d3a4-110">Le bloc de script ne peut contenir que des objets .NET Framework prenant en charge les transactions (instances de la classe Microsoft.PowerShell.Commands.Management.TransactedString, par exemple).</span><span class="sxs-lookup"><span data-stu-id="1d3a4-110">The script block can contain only transaction-enabled .NET Framework objects, such as instances of the Microsoft.PowerShell.Commands.Management.TransactedString class.</span></span>

<span data-ttu-id="1d3a4-111">Le paramètre *UseTransaction* , qui est facultatif pour la plupart des applets de commande, est requis lorsque vous utilisez cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-111">The *UseTransaction* parameter, which is optional for most cmdlets, is required when you use this cmdlet.</span></span>

<span data-ttu-id="1d3a4-112">**Use-transaction** est l’un des ensembles d’applets de commande qui prennent en charge la fonctionnalité des transactions dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-112">**Use-Transaction** is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="1d3a4-113">Pour plus d'informations, consultez about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-113">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="1d3a4-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1d3a4-114">EXAMPLES</span></span>

### <span data-ttu-id="1d3a4-115">Exemple 1 : générer un script à l’aide d’un objet de transaction</span><span class="sxs-lookup"><span data-stu-id="1d3a4-115">Example 1: Script by using a transaction-enabled object</span></span>

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

<span data-ttu-id="1d3a4-116">Cet exemple montre comment utiliser **use-transaction** pour écrire des scripts sur un objet de .NET Framework à transaction activée.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-116">This example shows how to use **Use-Transaction** to script against a transaction-enabled .NET Framework object.</span></span>
<span data-ttu-id="1d3a4-117">Dans ce cas, l’objet est un objet **TransactedString** .</span><span class="sxs-lookup"><span data-stu-id="1d3a4-117">In this case, the object is a **TransactedString** object.</span></span>

<span data-ttu-id="1d3a4-118">La première commande utilise l’applet de commande Start-Transaction pour démarrer une transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-118">The first command uses the Start-Transaction cmdlet to start a transaction.</span></span>

<span data-ttu-id="1d3a4-119">La deuxième commande utilise la commande New-Object pour créer un objet **TransactedString** .</span><span class="sxs-lookup"><span data-stu-id="1d3a4-119">The second command uses the New-Object command to create a **TransactedString** object.</span></span>
<span data-ttu-id="1d3a4-120">Elle stocke l’objet dans la variable $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-120">It stores the object in the $TransactedString variable.</span></span>

<span data-ttu-id="1d3a4-121">Les troisième et quatrième commandes utilisent la méthode **Append** de l’objet **TransactedString** pour ajouter du texte à la valeur de $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-121">The third and fourth commands both use the **Append** method of the **TransactedString** object to add text to the value of $TransactedString.</span></span>
<span data-ttu-id="1d3a4-122">Une commande fait partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-122">One command is part of the transaction.</span></span>
<span data-ttu-id="1d3a4-123">L’autre commande n’est pas.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-123">The other command is not.</span></span>

<span data-ttu-id="1d3a4-124">La troisième commande utilise la méthode **Append** de la chaîne traitée pour ajouter Hello à la valeur de $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-124">The third command uses the **Append** method of the transacted string to add Hello to the value of $TransactedString.</span></span>
<span data-ttu-id="1d3a4-125">Comme la commande ne fait pas partie de la transaction, la modification est immédiatement appliquée.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-125">Because the command is not part of the transaction, the change is applied immediately.</span></span>

<span data-ttu-id="1d3a4-126">La quatrième commande utilise **use-transaction** pour ajouter du texte à la chaîne dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-126">The fourth command uses **Use-Transaction** to add text to the string in the transaction.</span></span>
<span data-ttu-id="1d3a4-127">La commande utilise la méthode **Append** pour ajouter « , World » à la valeur de $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-127">The command uses the **Append** method to add ", World" to the value of $TransactedString.</span></span>
<span data-ttu-id="1d3a4-128">La commande est placée entre accolades ( {} ) pour en faire un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-128">The command is enclosed in braces ( {} ) to make it a script block.</span></span>
<span data-ttu-id="1d3a4-129">Le paramètre *UseTransaction* est obligatoire dans cette commande.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-129">The *UseTransaction* parameter is required in this command.</span></span>

<span data-ttu-id="1d3a4-130">Les cinquième et sixième commandes utilisent la méthode **ToString** de l’objet **TransactedString** pour afficher la valeur de **TransactedString** sous la forme d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-130">The fifth and sixth commands use the **ToString** method of the **TransactedString** object to display the value of the **TransactedString** as a string.</span></span>
<span data-ttu-id="1d3a4-131">Là encore, une commande fait partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-131">Again, one command is part of the transaction.</span></span>
<span data-ttu-id="1d3a4-132">L’autre transaction n’est pas.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-132">The other transaction is not.</span></span>

<span data-ttu-id="1d3a4-133">La cinquième commande utilise la méthode **ToString** pour afficher la valeur actuelle de la variable $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-133">The fifth command uses the **ToString** method to display the current value of the $TransactedString variable.</span></span>
<span data-ttu-id="1d3a4-134">Comme elle ne fait pas partie de la transaction, elle n’affiche que l’état actuel de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-134">Because it is not part of the transaction, it displays only the current state of the string.</span></span>

<span data-ttu-id="1d3a4-135">La sixième commande utilise **use-transaction** pour exécuter la même commande dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-135">The sixth command uses **Use-Transaction** to run the same command in the transaction.</span></span>
<span data-ttu-id="1d3a4-136">Étant donné que la commande fait partie de la transaction, elle affiche la valeur actuelle de la chaîne dans la transaction, comme un aperçu des modifications apportées à la transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-136">Because the command is part of the transaction, it displays the current value of the string in the transaction, much like a preview of the transaction changes.</span></span>

<span data-ttu-id="1d3a4-137">La septième commande utilise l’applet de commande Complete-Transaction pour valider la transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-137">The seventh command uses the Complete-Transaction cmdlet to commit the transaction.</span></span>

<span data-ttu-id="1d3a4-138">La dernière commande utilise la méthode **ToString** pour afficher la valeur résultante de la variable sous la forme d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-138">The final command uses the **ToString** method to display the resulting value of the variable as a string.</span></span>

### <span data-ttu-id="1d3a4-139">Exemple 2 : restaurer une transaction</span><span class="sxs-lookup"><span data-stu-id="1d3a4-139">Example 2: Roll back a transaction</span></span>

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> Undo-Transaction
PS C:\> $transactedString.ToString()
Hello
```

<span data-ttu-id="1d3a4-140">Cet exemple montre l’effet de la restauration d’une transaction qui comprend des commandes **use-transaction** .</span><span class="sxs-lookup"><span data-stu-id="1d3a4-140">This example shows the effect of rolling back a transaction that includes **Use-Transaction** commands.</span></span>
<span data-ttu-id="1d3a4-141">Comme pour toutes les commandes d’une transaction, lorsque la transaction est restaurée, les modifications basées sur les transactions sont ignorées et les données restent inchangées.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-141">Like all commands in a transaction, when the transaction is rolled back, the transacted changes are discarded and the data is unchanged.</span></span>

<span data-ttu-id="1d3a4-142">La première commande utilise **start-transaction** pour démarrer une transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-142">The first command uses **Start-Transaction** to start a transaction.</span></span>

<span data-ttu-id="1d3a4-143">La deuxième commande utilise **New-Object** pour créer un objet **TransactedString** .</span><span class="sxs-lookup"><span data-stu-id="1d3a4-143">The second command uses **New-Object** to create a **TransactedString** object.</span></span>
<span data-ttu-id="1d3a4-144">Elle stocke l’objet dans la variable $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-144">It stores the object in the $TransactedString variable.</span></span>

<span data-ttu-id="1d3a4-145">La troisième commande, qui ne fait pas partie de la transaction, utilise la méthode **Append** pour ajouter « Hello » à la valeur de $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-145">The third command, which is not part of the transaction, uses the **Append** method to add "Hello" to the value of $TransactedString.</span></span>

<span data-ttu-id="1d3a4-146">La quatrième commande utilise **use-transaction** pour exécuter une autre commande qui utilise la méthode **Append** dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-146">The fourth command uses **Use-Transaction** to run another command that uses the **Append** method in the transaction.</span></span>
<span data-ttu-id="1d3a4-147">La commande utilise la méthode **Append** pour ajouter « , World » à la valeur de $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-147">The command uses the **Append** method to add ", World" to the value of $TransactedString.</span></span>

<span data-ttu-id="1d3a4-148">La cinquième commande utilise l’applet de commande Undo-Transaction pour restaurer la transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-148">The fifth command uses the Undo-Transaction cmdlet to roll back the transaction.</span></span>
<span data-ttu-id="1d3a4-149">Par conséquent, toutes les commandes exécutées dans la transaction sont inversées.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-149">As a result, all commands performed in the transaction are reversed.</span></span>

<span data-ttu-id="1d3a4-150">La dernière commande utilise la méthode **ToString** pour afficher la valeur résultante de $TransactedString sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-150">The final command uses the **ToString** method to display the resulting value of $TransactedString as a string.</span></span>
<span data-ttu-id="1d3a4-151">Les résultats indiquent que seules les modifications apportées en dehors de la transaction ont été appliquées à l’objet.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-151">The results show that only the changes that were made outside the transaction were applied to the object.</span></span>

## <span data-ttu-id="1d3a4-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1d3a4-152">PARAMETERS</span></span>

### <span data-ttu-id="1d3a4-153">-TransactedScript</span><span class="sxs-lookup"><span data-stu-id="1d3a4-153">-TransactedScript</span></span>
<span data-ttu-id="1d3a4-154">Spécifie le bloc de script qui est exécuté dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-154">Specifies the script block that is run in the transaction.</span></span>
<span data-ttu-id="1d3a4-155">Entrez un bloc de script valide entre accolades ( { } ).</span><span class="sxs-lookup"><span data-stu-id="1d3a4-155">Enter any valid script block enclosed in braces ( { } ).</span></span>
<span data-ttu-id="1d3a4-156">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-156">This parameter is required.</span></span>

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

### <span data-ttu-id="1d3a4-157">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="1d3a4-157">-UseTransaction</span></span>
<span data-ttu-id="1d3a4-158">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-158">Includes the command in the active transaction.</span></span>
<span data-ttu-id="1d3a4-159">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-159">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="1d3a4-160">Pour plus d’informations, consultez about_transactions.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-160">For more information, see about_transactions.</span></span>

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

### <span data-ttu-id="1d3a4-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1d3a4-161">CommonParameters</span></span>
<span data-ttu-id="1d3a4-162">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1d3a4-163">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1d3a4-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1d3a4-164">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1d3a4-164">INPUTS</span></span>

### <span data-ttu-id="1d3a4-165">Aucun</span><span class="sxs-lookup"><span data-stu-id="1d3a4-165">None</span></span>
<span data-ttu-id="1d3a4-166">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-166">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1d3a4-167">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1d3a4-167">OUTPUTS</span></span>

### <span data-ttu-id="1d3a4-168">PSObject</span><span class="sxs-lookup"><span data-stu-id="1d3a4-168">PSObject</span></span>
<span data-ttu-id="1d3a4-169">Cette applet de commande retourne le résultat de la transaction.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-169">This cmdlet returns the result of the transaction.</span></span>

## <span data-ttu-id="1d3a4-170">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1d3a4-170">NOTES</span></span>

* <span data-ttu-id="1d3a4-171">Le paramètre *UseTransaction* comprend la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-171">The *UseTransaction* parameter includes the command in the active transaction.</span></span> <span data-ttu-id="1d3a4-172">Étant donné que l’applet de commande **use-transaction** est toujours utilisée dans les transactions, ce paramètre est requis pour rendre l’utilisation de la commande **use-transaction** effective.</span><span class="sxs-lookup"><span data-stu-id="1d3a4-172">Because the **Use-Transaction** cmdlet is always used in transactions, this parameter is required to make any **Use-Transaction** command effective.</span></span>

*

## <span data-ttu-id="1d3a4-173">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1d3a4-173">RELATED LINKS</span></span>

[<span data-ttu-id="1d3a4-174">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="1d3a4-174">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="1d3a4-175">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="1d3a4-175">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="1d3a4-176">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="1d3a4-176">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="1d3a4-177">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="1d3a4-177">Undo-Transaction</span></span>](Undo-Transaction.md)
