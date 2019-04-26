---
title: Comment valider un nombre d’arguments | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067805"
---
# <a name="how-to-validate-an-argument-count"></a>Guide pratique pour valider un nombre d’arguments

Cet exemple montre comment spécifier une règle de validation que le runtime de Windows PowerShell peut utiliser pour vérifier le nombre d’arguments (nombre) qui accepte un paramètre avant l’exécution de l’applet de commande. Vous définissez cette règle de validation en déclarant l’attribut ValidateCount.

> [!NOTE]
> Pour plus d’informations sur la classe qui définit cet attribut, consultez [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Pour valider un nombre d’arguments

- Ajoutez l’attribut de validation comme indiqué dans le code suivant. Cet exemple spécifie que le paramètre accepte un argument ou jusqu'à trois arguments.

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

[Déclaration d’attribut de ValidateCount](./validatecount-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
