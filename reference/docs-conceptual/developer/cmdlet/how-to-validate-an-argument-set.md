---
title: Comment valider un jeu d’arguments | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateSet attribute, example
ms.openlocfilehash: 6173f1380583f5b27e2b188990a5ea041f447c57
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782002"
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
