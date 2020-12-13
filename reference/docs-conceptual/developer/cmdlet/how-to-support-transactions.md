---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour prendre en charge les transactions
description: Guide pratique pour prendre en charge les transactions
ms.openlocfilehash: 5691c246830dab9f4808801c04353ebfb2c3e981
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666958"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="b0640-103">Guide pratique pour prendre en charge les transactions</span><span class="sxs-lookup"><span data-stu-id="b0640-103">How to Support Transactions</span></span>

<span data-ttu-id="b0640-104">Cet exemple montre les éléments de code de base qui ajoutent la prise en charge des transactions à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0640-104">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b0640-105">Pour plus d’informations sur la façon dont Windows PowerShell gère les transactions, consultez [à propos des transactions][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="b0640-105">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="b0640-106">Pour prendre en charge les transactions</span><span class="sxs-lookup"><span data-stu-id="b0640-106">To support transactions</span></span>

1. <span data-ttu-id="b0640-107">Lorsque vous déclarez l’attribut d’applet de commande, spécifiez que l’applet de commande prend en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="b0640-107">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="b0640-108">Lorsque l’applet de commande prend en charge les transactions, Windows PowerShell ajoute le `UseTransaction` paramètre à l’applet de commande lors de son exécution.</span><span class="sxs-lookup"><span data-stu-id="b0640-108">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="b0640-109">Dans l’une des méthodes de traitement d’entrée, ajoutez un `if` bloc pour déterminer si une transaction est disponible.</span><span class="sxs-lookup"><span data-stu-id="b0640-109">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="b0640-110">Si l' `if` instruction correspond à `true` , les actions dans cette instruction peuvent être effectuées dans le contexte de la transaction actuelle.</span><span class="sxs-lookup"><span data-stu-id="b0640-110">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="b0640-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0640-111">See Also</span></span>

[<span data-ttu-id="b0640-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0640-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
