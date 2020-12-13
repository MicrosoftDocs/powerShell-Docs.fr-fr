---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour valider une plage d’argument
description: Guide pratique pour valider une plage d’argument
ms.openlocfilehash: 1c1c53d43350a38beb2193200de3bd6b689366a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666924"
---
# <a name="how-to-validate-an-argument-range"></a>Guide pratique pour valider une plage d’argument

Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier les valeurs minimale et maximale de l’argument de paramètre avant l’exécution de l’applet de commande. Vous définissez cette règle de validation en déclarant l’attribut ValidateRange.

> [!NOTE]
> Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Pour valider une plage d’arguments

- Ajoutez l’attribut ValidateRange comme indiqué dans le code suivant. Cet exemple spécifie une plage de 0 à 5 pour le `InputData` paramètre.

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[Déclaration de l’attribut ValidateRange](./validaterange-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
