---
title: Comment valider un modèle de l’Argument | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067771"
---
# <a name="how-to-validate-an-argument-pattern"></a>Guide pratique pour valider un modèle d’argument

Cet exemple montre comment spécifier une règle de validation que le runtime de Windows PowerShell peut utiliser pour vérifier le modèle de caractère de l’argument de paramètre avant l’exécution de l’applet de commande. Vous définissez cette règle de validation en déclarant l’attribut ValidatePattern.

> [!NOTE]
> Pour plus d’informations sur la classe qui définit cet attribut, consultez [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Pour valider un modèle d’argument

- Ajoutez l’attribut de validation comme indiqué dans le code suivant. Cet exemple spécifie un modèle de quatre chiffres, où chaque chiffre a une valeur de 0 à 9.

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

[Déclaration d’attribut de ValidatePattern](./validatepattern-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
