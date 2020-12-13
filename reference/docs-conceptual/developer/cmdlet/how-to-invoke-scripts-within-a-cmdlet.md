---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour appeler des scripts dans une applet de commande
description: Guide pratique pour appeler des scripts dans une applet de commande
ms.openlocfilehash: f4a43a1e1240854e57deac5721e1e070c1a45a51
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667026"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="5a8cb-103">Guide pratique pour appeler des scripts dans une applet de commande</span><span class="sxs-lookup"><span data-stu-id="5a8cb-103">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="5a8cb-104">Cet exemple montre comment appeler un script fourni à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5a8cb-104">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="5a8cb-105">Le script est exécuté par l’applet de commande et ses résultats sont retournés à l’applet de commande sous la forme d’une collection d’objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) .</span><span class="sxs-lookup"><span data-stu-id="5a8cb-105">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="5a8cb-106">Pour appeler un bloc de script</span><span class="sxs-lookup"><span data-stu-id="5a8cb-106">To invoke a script block</span></span>

1. <span data-ttu-id="5a8cb-107">La commande vérifie qu’un bloc de script a été fourni à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5a8cb-107">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="5a8cb-108">Si un bloc de script a été fourni, la commande appelle le bloc de script avec ses paramètres requis.</span><span class="sxs-lookup"><span data-stu-id="5a8cb-108">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="5a8cb-109">Ensuite, le script itère au sein de la collection retournée des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) et effectue les opérations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="5a8cb-109">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5a8cb-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a8cb-110">See Also</span></span>

[<span data-ttu-id="5a8cb-111">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a8cb-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
