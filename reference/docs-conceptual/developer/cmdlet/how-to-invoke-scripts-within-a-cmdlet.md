---
title: Comment appeler des scripts dans une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364408"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="e8ffa-102">Guide pratique pour appeler des scripts dans une applet de commande</span><span class="sxs-lookup"><span data-stu-id="e8ffa-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="e8ffa-103">Cet exemple montre comment appeler un script fourni à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e8ffa-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="e8ffa-104">Le script est exécuté par l’applet de commande et ses résultats sont retournés à l’applet de commande sous la forme d’une collection d’objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) .</span><span class="sxs-lookup"><span data-stu-id="e8ffa-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="e8ffa-105">Pour appeler un bloc de script</span><span class="sxs-lookup"><span data-stu-id="e8ffa-105">To invoke a script block</span></span>

1. <span data-ttu-id="e8ffa-106">La commande vérifie qu’un bloc de script a été fourni à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e8ffa-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="e8ffa-107">Si un bloc de script a été fourni, la commande appelle le bloc de script avec ses paramètres requis.</span><span class="sxs-lookup"><span data-stu-id="e8ffa-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. <span data-ttu-id="e8ffa-108">Ensuite, le script itère au sein de la collection retournée des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) et effectue les opérations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e8ffa-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a><span data-ttu-id="e8ffa-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8ffa-109">See Also</span></span>

[<span data-ttu-id="e8ffa-110">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8ffa-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)