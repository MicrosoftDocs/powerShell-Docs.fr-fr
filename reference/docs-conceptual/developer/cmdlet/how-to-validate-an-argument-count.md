---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour valider un nombre d’arguments
description: Guide pratique pour valider un nombre d’arguments
ms.openlocfilehash: 46a32d61138fb50bceea98171f76749c9d96734d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666941"
---
# <a name="how-to-validate-an-argument-count"></a>Guide pratique pour valider un nombre d’arguments

Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier le nombre d’arguments (le nombre) qu’un paramètre accepte avant l’exécution de l’applet de commande. Vous définissez cette règle de validation en déclarant l’attribut ValidateCount.

> [!NOTE]
> Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Pour valider un nombre d’arguments

- Ajoutez l’attribut Validate comme indiqué dans le code suivant. Cet exemple spécifie que le paramètre acceptera un ou plusieurs arguments.

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[Déclaration de l’attribut ValidateCount](./validatecount-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
