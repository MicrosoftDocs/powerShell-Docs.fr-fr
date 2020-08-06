---
title: Comment valider la longueur de l’argument | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateLength attribute, example
ms.openlocfilehash: aa0545def6d9628f6b41090a425f0c5af25f6ad7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784076"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="f8ddd-102">Guide pratique pour valider une longueur d’argument</span><span class="sxs-lookup"><span data-stu-id="f8ddd-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="f8ddd-103">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier le nombre de caractères (longueur) de l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f8ddd-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="f8ddd-104">Vous définissez cette règle de validation en déclarant l’attribut ValidateLength.</span><span class="sxs-lookup"><span data-stu-id="f8ddd-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="f8ddd-105">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="f8ddd-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="f8ddd-106">Pour valider la longueur de l’argument</span><span class="sxs-lookup"><span data-stu-id="f8ddd-106">To validate the argument length</span></span>

- <span data-ttu-id="f8ddd-107">Ajoutez l’attribut Validate comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="f8ddd-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="f8ddd-108">Cet exemple spécifie que la longueur de l’argument doit être comprise entre 0 et 10 caractères.</span><span class="sxs-lookup"><span data-stu-id="f8ddd-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="f8ddd-109">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f8ddd-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8ddd-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8ddd-110">See Also</span></span>

[<span data-ttu-id="f8ddd-111">Déclaration de l’attribut ValidateLength</span><span class="sxs-lookup"><span data-stu-id="f8ddd-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="f8ddd-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8ddd-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
