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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365538"
---
# <a name="how-to-support-transactions"></a>Guide pratique pour prendre en charge les transactions

Cet exemple montre les éléments de code de base qui ajoutent la prise en charge des transactions à une applet de commande.

> [!IMPORTANT]
> Pour plus d’informations sur la façon dont Windows PowerShell gère les transactions, consultez [à propos des transactions][about_Transactions].

## <a name="to-support-transactions"></a>Pour prendre en charge les transactions

1. Lorsque vous déclarez l’attribut d’applet de commande, spécifiez que l’applet de commande prend en charge les transactions.
   Lorsque l’applet de commande prend en charge les transactions, Windows PowerShell ajoute le paramètre `UseTransaction` à l’applet de commande lors de son exécution.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Dans l’une des méthodes de traitement d’entrée, ajoutez un bloc `if` pour déterminer si une transaction est disponible.
   Si l’instruction `if` correspond à `true`, les actions dans cette instruction peuvent être effectuées dans le contexte de la transaction actuelle.

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
