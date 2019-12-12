---
title: Comment prendre en charge les transactions | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365538"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="c5466-102">Guide pratique pour prendre en charge les transactions</span><span class="sxs-lookup"><span data-stu-id="c5466-102">How to Support Transactions</span></span>

<span data-ttu-id="c5466-103">Cet exemple montre les éléments de code de base qui ajoutent la prise en charge des transactions à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c5466-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5466-104">Pour plus d’informations sur la façon dont Windows PowerShell gère les transactions, consultez [à propos des transactions][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="c5466-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="c5466-105">Pour prendre en charge les transactions</span><span class="sxs-lookup"><span data-stu-id="c5466-105">To support transactions</span></span>

1. <span data-ttu-id="c5466-106">Lorsque vous déclarez l’attribut d’applet de commande, spécifiez que l’applet de commande prend en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="c5466-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="c5466-107">Lorsque l’applet de commande prend en charge les transactions, Windows PowerShell ajoute le paramètre `UseTransaction` à l’applet de commande lors de son exécution.</span><span class="sxs-lookup"><span data-stu-id="c5466-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="c5466-108">Dans l’une des méthodes de traitement d’entrée, ajoutez un bloc `if` pour déterminer si une transaction est disponible.</span><span class="sxs-lookup"><span data-stu-id="c5466-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="c5466-109">Si l’instruction `if` est résolue en `true`, les actions dans cette instruction peuvent être effectuées dans le contexte de la transaction actuelle.</span><span class="sxs-lookup"><span data-stu-id="c5466-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="c5466-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5466-110">See Also</span></span>

[<span data-ttu-id="c5466-111">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5466-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
