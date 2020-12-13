---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour valider un nombre d’arguments
description: Guide pratique pour valider un nombre d’arguments
ms.openlocfilehash: 46a32d61138fb50bceea98171f76749c9d96734d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666941"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="8a142-103">Guide pratique pour valider un nombre d’arguments</span><span class="sxs-lookup"><span data-stu-id="8a142-103">How to Validate an Argument Count</span></span>

<span data-ttu-id="8a142-104">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier le nombre d’arguments (le nombre) qu’un paramètre accepte avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8a142-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="8a142-105">Vous définissez cette règle de validation en déclarant l’attribut ValidateCount.</span><span class="sxs-lookup"><span data-stu-id="8a142-105">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="8a142-106">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="8a142-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="8a142-107">Pour valider un nombre d’arguments</span><span class="sxs-lookup"><span data-stu-id="8a142-107">To validate an argument count</span></span>

- <span data-ttu-id="8a142-108">Ajoutez l’attribut Validate comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="8a142-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="8a142-109">Cet exemple spécifie que le paramètre acceptera un ou plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="8a142-109">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="8a142-110">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8a142-110">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8a142-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a142-111">See Also</span></span>

[<span data-ttu-id="8a142-112">Déclaration de l’attribut ValidateCount</span><span class="sxs-lookup"><span data-stu-id="8a142-112">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="8a142-113">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a142-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
