---
title: Comment valider une plage de l’Argument | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067788"
---
# <a name="how-to-validate-an-argument-range"></a>Guide pratique pour valider une plage d’argument

Cet exemple montre comment spécifier une règle de validation que le runtime de Windows PowerShell peut utiliser pour vérifier les valeurs minimales et maximales de l’argument de paramètre avant l’exécution de l’applet de commande. Vous définissez cette règle de validation en déclarant l’attribut ValidateRange.

> [!NOTE]
> Pour plus d’informations sur la classe qui définit cet attribut, consultez [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Pour valider une plage d’argument

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

[Déclaration d’attribut de ValidateRange](./validaterange-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
