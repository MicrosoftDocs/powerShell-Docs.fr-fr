---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour valider un modèle d’argument
description: Guide pratique pour valider un modèle d’argument
ms.openlocfilehash: ab5777c918a53c0a3900f87c52e7f14f9cb9b726
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666907"
---
# <a name="how-to-validate-an-argument-pattern"></a>Guide pratique pour valider un modèle d’argument

Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier le modèle de caractères de l’argument de paramètre avant l’exécution de l’applet de commande. Vous définissez cette règle de validation en déclarant l’attribut ValidatePattern.

> [!NOTE]
> Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Pour valider un modèle d’argument

- Ajoutez l’attribut Validate comme indiqué dans le code suivant. Cet exemple spécifie un modèle de quatre chiffres, où chaque chiffre a une valeur de 0 à 9.

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[Déclaration de l’attribut ValidatePattern](./validatepattern-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
