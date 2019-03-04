---
title: Comment appeler des Scripts au sein d’une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 4b4d5645785b751eb1390e196f5b9437b4a1e13b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855835"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Guide pratique pour appeler des scripts dans une applet de commande

Cet exemple montre comment appeler un script qui est fourni à une applet de commande. Le script est exécuté par l’applet de commande et ses résultats sont retournés à l’applet de commande en tant que collection de [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objets.

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

2. Ensuite, le script effectue une itération via la collection retournée de [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objets et d’effectuer les opérations nécessaires.

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
