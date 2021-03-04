---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour appeler des scripts dans une applet de commande
description: Guide pratique pour appeler des scripts dans une applet de commande
ms.openlocfilehash: 503ecb8913fe61ef3f5ec6fe969c22c2319a4f12
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685339"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="addf4-103">Guide pratique pour appeler des scripts dans une applet de commande</span><span class="sxs-lookup"><span data-stu-id="addf4-103">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="addf4-104">Cet exemple montre comment appeler un script fourni à une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="addf4-104">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="addf4-105">Le script est exécuté par l’applet de commande et ses résultats sont retournés à l’applet de commande sous la forme d’une collection d’objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) .</span><span class="sxs-lookup"><span data-stu-id="addf4-105">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="addf4-106">Pour appeler un bloc de script</span><span class="sxs-lookup"><span data-stu-id="addf4-106">To invoke a script block</span></span>

1. <span data-ttu-id="addf4-107">La commande vérifie qu’un bloc de script a été fourni à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="addf4-107">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="addf4-108">Si un bloc de script a été fourni, la commande appelle le bloc de script avec ses paramètres requis.</span><span class="sxs-lookup"><span data-stu-id="addf4-108">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="addf4-109">Ensuite, le script itère au sein de la collection retournée des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) et effectue les opérations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="addf4-109">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```csharp
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

## <a name="see-also"></a><span data-ttu-id="addf4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="addf4-110">See Also</span></span>

[<span data-ttu-id="addf4-111">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="addf4-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
