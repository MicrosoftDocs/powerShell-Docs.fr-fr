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
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="0f519-102">Guide pratique pour valider une longueur d’argument</span><span class="sxs-lookup"><span data-stu-id="0f519-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="0f519-103">Cet exemple montre comment spécifier une règle de validation que le runtime de Windows PowerShell peut utiliser pour vérifier le nombre de caractères (longueur) de l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0f519-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="0f519-104">Vous définissez cette règle de validation en déclarant l’attribut ValidateLength.</span><span class="sxs-lookup"><span data-stu-id="0f519-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="0f519-105">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="0f519-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="0f519-106">Pour valider la longueur d’argument</span><span class="sxs-lookup"><span data-stu-id="0f519-106">To validate the argument length</span></span>

- <span data-ttu-id="0f519-107">Ajoutez l’attribut de validation comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="0f519-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="0f519-108">Cet exemple spécifie que la longueur de l’argument doit avoir une longueur de 0 à 10 caractères.</span><span class="sxs-lookup"><span data-stu-id="0f519-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="0f519-109">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0f519-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f519-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f519-110">See Also</span></span>

[<span data-ttu-id="0f519-111">Déclaration d’attribut de ValidateLength</span><span class="sxs-lookup"><span data-stu-id="0f519-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="0f519-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f519-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
