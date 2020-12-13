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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Guide pratique pour appeler des scripts dans une applet de commande

Cet exemple montre comment appeler un script fourni à une applet de commande. Le script est exécuté par l’applet de commande et ses résultats sont retournés à l’applet de commande sous la forme d’une collection d’objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) .

## <a name="to-invoke-a-script-block"></a>Pour appeler un bloc de script

1. La commande vérifie qu’un bloc de script a été fourni à l’applet de commande. Si un bloc de script a été fourni, la commande appelle le bloc de script avec ses paramètres requis.

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

2. Ensuite, le script itère au sein de la collection retournée des objets [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) et effectue les opérations nécessaires.

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

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
