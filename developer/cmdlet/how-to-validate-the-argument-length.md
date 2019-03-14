---
title: Comment valider la longueur de l’Argument | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857125"
---
# <a name="how-to-validate-the-argument-length"></a>Guide pratique pour valider une longueur d’argument

Cet exemple montre comment spécifier une règle de validation que le runtime de Windows PowerShell peut utiliser pour vérifier le nombre de caractères (longueur) de l’argument de paramètre avant l’exécution de l’applet de commande. Vous définissez cette règle de validation en déclarant l’attribut ValidateLength.

> [!NOTE]
> Pour plus d’informations sur la classe qui définit cet attribut, consultez [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Pour valider la longueur d’argument

- Ajoutez l’attribut de validation comme indiqué dans le code suivant. Cet exemple spécifie que la longueur de l’argument doit avoir une longueur de 0 à 10 caractères.

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

[Déclaration d’attribut de ValidateLength](./validatelength-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)