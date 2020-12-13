---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour valider une plage d’argument
description: Guide pratique pour valider une plage d’argument
ms.openlocfilehash: 1c1c53d43350a38beb2193200de3bd6b689366a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666924"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="6035e-103">Guide pratique pour valider une plage d’argument</span><span class="sxs-lookup"><span data-stu-id="6035e-103">How to Validate an Argument Range</span></span>

<span data-ttu-id="6035e-104">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier les valeurs minimale et maximale de l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6035e-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="6035e-105">Vous définissez cette règle de validation en déclarant l’attribut ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="6035e-105">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="6035e-106">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="6035e-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="6035e-107">Pour valider une plage d’arguments</span><span class="sxs-lookup"><span data-stu-id="6035e-107">To validate an argument range</span></span>

- <span data-ttu-id="6035e-108">Ajoutez l’attribut ValidateRange comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="6035e-108">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="6035e-109">Cet exemple spécifie une plage de 0 à 5 pour le `InputData` paramètre.</span><span class="sxs-lookup"><span data-stu-id="6035e-109">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="6035e-110">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6035e-110">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6035e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6035e-111">See Also</span></span>

[<span data-ttu-id="6035e-112">Déclaration de l’attribut ValidateRange</span><span class="sxs-lookup"><span data-stu-id="6035e-112">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="6035e-113">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6035e-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
