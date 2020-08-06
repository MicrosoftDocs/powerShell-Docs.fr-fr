---
title: Comment valider un modèle d’argument | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidatePattern attribute, example
ms.openlocfilehash: 35104e786d4b809a711d97fea52ae0e348dd5ca3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782087"
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
