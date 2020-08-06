---
title: Comment valider un nombre d’arguments | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateCount attribute, example
ms.openlocfilehash: e7c0eb364a6975cec089b984c2100d476631a12d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782121"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="d30da-102">Guide pratique pour valider un nombre d’arguments</span><span class="sxs-lookup"><span data-stu-id="d30da-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="d30da-103">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier le nombre d’arguments (le nombre) qu’un paramètre accepte avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d30da-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="d30da-104">Vous définissez cette règle de validation en déclarant l’attribut ValidateCount.</span><span class="sxs-lookup"><span data-stu-id="d30da-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="d30da-105">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="d30da-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="d30da-106">Pour valider un nombre d’arguments</span><span class="sxs-lookup"><span data-stu-id="d30da-106">To validate an argument count</span></span>

- <span data-ttu-id="d30da-107">Ajoutez l’attribut Validate comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d30da-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="d30da-108">Cet exemple spécifie que le paramètre acceptera un ou plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="d30da-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="d30da-109">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d30da-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d30da-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d30da-110">See Also</span></span>

[<span data-ttu-id="d30da-111">Déclaration de l’attribut ValidateCount</span><span class="sxs-lookup"><span data-stu-id="d30da-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="d30da-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d30da-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
