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
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="0bc2c-103">Guide pratique pour valider une longueur d’argument</span><span class="sxs-lookup"><span data-stu-id="0bc2c-103">How to Validate the Argument Length</span></span>

<span data-ttu-id="0bc2c-104">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier le nombre de caractères (longueur) de l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0bc2c-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="0bc2c-105">Vous définissez cette règle de validation en déclarant l’attribut ValidateLength.</span><span class="sxs-lookup"><span data-stu-id="0bc2c-105">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="0bc2c-106">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="0bc2c-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="0bc2c-107">Pour valider la longueur de l’argument</span><span class="sxs-lookup"><span data-stu-id="0bc2c-107">To validate the argument length</span></span>

- <span data-ttu-id="0bc2c-108">Ajoutez l’attribut Validate comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="0bc2c-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="0bc2c-109">Cet exemple spécifie que la longueur de l’argument doit être comprise entre 0 et 10 caractères.</span><span class="sxs-lookup"><span data-stu-id="0bc2c-109">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="0bc2c-110">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0bc2c-110">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bc2c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bc2c-111">See Also</span></span>

[<span data-ttu-id="0bc2c-112">Déclaration de l’attribut ValidateLength</span><span class="sxs-lookup"><span data-stu-id="0bc2c-112">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="0bc2c-113">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0bc2c-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
