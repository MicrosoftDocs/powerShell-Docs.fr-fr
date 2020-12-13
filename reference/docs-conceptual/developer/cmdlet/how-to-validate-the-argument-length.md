---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour valider une longueur d’argument
description: Guide pratique pour valider une longueur d’argument
ms.openlocfilehash: 460aedbe6847033f976cb7bf70b6c77ac5a3a3c9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652633"
---
# <a name="how-to-validate-the-argument-length"></a>Guide pratique pour valider une longueur d’argument

Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier le nombre de caractères (longueur) de l’argument de paramètre avant l’exécution de l’applet de commande. Vous définissez cette règle de validation en déclarant l’attribut ValidateLength.

> [!NOTE]
> Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Pour valider la longueur de l’argument

- Ajoutez l’attribut Validate comme indiqué dans le code suivant. Cet exemple spécifie que la longueur de l’argument doit être comprise entre 0 et 10 caractères.

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[Déclaration de l’attribut ValidateLength](./validatelength-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
