---
title: Comment valider une plage d’arguments | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange attribute, example
ms.openlocfilehash: b48b1b87425add51e855c48ec700c78c3ae296c1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782070"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="8b52b-102">Guide pratique pour valider une plage d’argument</span><span class="sxs-lookup"><span data-stu-id="8b52b-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="8b52b-103">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier les valeurs minimale et maximale de l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8b52b-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="8b52b-104">Vous définissez cette règle de validation en déclarant l’attribut ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="8b52b-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="8b52b-105">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="8b52b-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="8b52b-106">Pour valider une plage d’arguments</span><span class="sxs-lookup"><span data-stu-id="8b52b-106">To validate an argument range</span></span>

- <span data-ttu-id="8b52b-107">Ajoutez l’attribut ValidateRange comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="8b52b-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="8b52b-108">Cet exemple spécifie une plage de 0 à 5 pour le `InputData` paramètre.</span><span class="sxs-lookup"><span data-stu-id="8b52b-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="8b52b-109">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8b52b-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b52b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b52b-110">See Also</span></span>

[<span data-ttu-id="8b52b-111">Déclaration de l’attribut ValidateRange</span><span class="sxs-lookup"><span data-stu-id="8b52b-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="8b52b-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b52b-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
