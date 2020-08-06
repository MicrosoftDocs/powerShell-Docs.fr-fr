---
title: Comment valider un jeu d’arguments | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateSet attribute, example
ms.openlocfilehash: 6173f1380583f5b27e2b188990a5ea041f447c57
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782002"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="6b07d-102">Guide pratique pour valider un jeu d’arguments</span><span class="sxs-lookup"><span data-stu-id="6b07d-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="6b07d-103">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6b07d-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="6b07d-104">Cette règle de validation fournit un ensemble de valeurs valides pour l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="6b07d-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="6b07d-105">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="6b07d-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="6b07d-106">Pour valider un jeu d’arguments</span><span class="sxs-lookup"><span data-stu-id="6b07d-106">To validate an argument set</span></span>

- <span data-ttu-id="6b07d-107">Ajoutez l’attribut ValidateSet comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="6b07d-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="6b07d-108">Cet exemple spécifie un ensemble de trois valeurs possibles pour le `UserName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="6b07d-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

<span data-ttu-id="6b07d-109">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b07d-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6b07d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b07d-110">See Also</span></span>

[<span data-ttu-id="6b07d-111">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="6b07d-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="6b07d-112">Déclaration de l’attribut ValidateSet</span><span class="sxs-lookup"><span data-stu-id="6b07d-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="6b07d-113">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b07d-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
