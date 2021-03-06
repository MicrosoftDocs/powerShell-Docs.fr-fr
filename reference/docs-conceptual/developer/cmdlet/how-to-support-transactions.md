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
# <a name="how-to-support-transactions"></a>Guide pratique pour prendre en charge les transactions

Cet exemple montre les éléments de code de base qui ajoutent la prise en charge des transactions à une applet de commande.

> [!IMPORTANT]
> Pour plus d’informations sur la façon dont Windows PowerShell gère les transactions, consultez [à propos des transactions][about_Transactions].

## <a name="to-support-transactions"></a>Pour prendre en charge les transactions

1. Lorsque vous déclarez l’attribut d’applet de commande, spécifiez que l’applet de commande prend en charge les transactions.
   Lorsque l’applet de commande prend en charge les transactions, Windows PowerShell ajoute le `UseTransaction` paramètre à l’applet de commande lors de son exécution.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Dans l’une des méthodes de traitement d’entrée, ajoutez un `if` bloc pour déterminer si une transaction est disponible.
   Si l' `if` instruction correspond à `true` , les actions dans cette instruction peuvent être effectuées dans le contexte de la transaction actuelle.

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
