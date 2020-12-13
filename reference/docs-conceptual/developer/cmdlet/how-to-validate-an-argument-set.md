---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour valider un jeu d’arguments
description: Guide pratique pour valider un jeu d’arguments
ms.openlocfilehash: 50ec0a48277893584d896e14ad6aa843682a28cc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650372"
---
# <a name="how-to-validate-an-argument-set"></a>Guide pratique pour valider un jeu d’arguments

Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier l’argument de paramètre avant l’exécution de l’applet de commande. Cette règle de validation fournit un ensemble de valeurs valides pour l’argument de paramètre.

> [!NOTE]
> Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Pour valider un jeu d’arguments

- Ajoutez l’attribut ValidateSet comme indiqué dans le code suivant. Cet exemple spécifie un ensemble de trois valeurs possibles pour le `UserName` paramètre.

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Déclaration de l’attribut ValidateSet](./validateset-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
