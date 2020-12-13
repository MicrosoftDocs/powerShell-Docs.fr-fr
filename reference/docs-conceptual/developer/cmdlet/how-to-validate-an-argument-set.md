---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour valider un jeu d’arguments
description: Guide pratique pour valider un jeu d’arguments
ms.openlocfilehash: 50ec0a48277893584d896e14ad6aa843682a28cc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650372"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="dfc3e-103">Guide pratique pour valider un jeu d’arguments</span><span class="sxs-lookup"><span data-stu-id="dfc3e-103">How to Validate an Argument Set</span></span>

<span data-ttu-id="dfc3e-104">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dfc3e-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="dfc3e-105">Cette règle de validation fournit un ensemble de valeurs valides pour l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="dfc3e-105">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="dfc3e-106">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="dfc3e-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="dfc3e-107">Pour valider un jeu d’arguments</span><span class="sxs-lookup"><span data-stu-id="dfc3e-107">To validate an argument set</span></span>

- <span data-ttu-id="dfc3e-108">Ajoutez l’attribut ValidateSet comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="dfc3e-108">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="dfc3e-109">Cet exemple spécifie un ensemble de trois valeurs possibles pour le `UserName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="dfc3e-109">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="dfc3e-110">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="dfc3e-110">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfc3e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfc3e-111">See Also</span></span>

[<span data-ttu-id="dfc3e-112">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="dfc3e-112">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="dfc3e-113">Déclaration de l’attribut ValidateSet</span><span class="sxs-lookup"><span data-stu-id="dfc3e-113">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="dfc3e-114">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dfc3e-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
