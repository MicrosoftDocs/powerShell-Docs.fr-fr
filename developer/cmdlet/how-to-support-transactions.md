---
title: Comment prendre en charge des Transactions | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857115"
---
# <a name="how-to-support-transactions"></a>Guide pratique pour prendre en charge les transactions

Cet exemple montre les éléments de code de base qui ajoutent la prise en charge des transactions pour une applet de commande.

> [!IMPORTANT]
> Pour plus d’informations sur la façon dont Windows PowerShell gère les transactions, consultez [sur les Transactions][about_Transactions].

## <a name="to-support-transactions"></a>Pour prendre en charge des transactions

1. Lorsque vous déclarez l’attribut de l’applet de commande, spécifiez que l’applet de commande prend en charge les transactions.
   Lors de l’applet de commande prend en charge les transactions, Windows PowerShell ajoute le `UseTransaction` paramètre à l’applet de commande lorsqu’elle est exécutée.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Parmi les méthodes de traitement d’entrée, ajoutez un `if` bloc pour déterminer si une transaction est disponible.
   Si le `if` instruction correspond à `true`, les actions au sein de cette instruction peuvent être effectuées dans le contexte de la transaction actuelle.

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
