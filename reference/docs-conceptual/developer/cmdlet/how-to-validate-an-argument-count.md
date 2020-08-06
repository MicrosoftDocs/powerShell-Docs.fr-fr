---
title: Comment valider un nombre d’arguments | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateCount attribute, example
ms.openlocfilehash: e7c0eb364a6975cec089b984c2100d476631a12d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782121"
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
