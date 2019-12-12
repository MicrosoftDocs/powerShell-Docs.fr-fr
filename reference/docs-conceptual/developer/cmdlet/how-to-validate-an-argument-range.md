---
title: Comment valider une plage d’arguments | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365518"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="a53d7-102">Guide pratique pour valider une plage d’argument</span><span class="sxs-lookup"><span data-stu-id="a53d7-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="a53d7-103">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier les valeurs minimale et maximale de l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a53d7-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="a53d7-104">Vous définissez cette règle de validation en déclarant l’attribut ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="a53d7-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="a53d7-105">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="a53d7-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="a53d7-106">Pour valider une plage d’arguments</span><span class="sxs-lookup"><span data-stu-id="a53d7-106">To validate an argument range</span></span>

- <span data-ttu-id="a53d7-107">Ajoutez l’attribut ValidateRange comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="a53d7-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="a53d7-108">Cet exemple spécifie une plage de 0 à 5 pour le paramètre `InputData`.</span><span class="sxs-lookup"><span data-stu-id="a53d7-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="a53d7-109">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a53d7-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a53d7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a53d7-110">See Also</span></span>

[<span data-ttu-id="a53d7-111">Déclaration d’attribut ValidateRange</span><span class="sxs-lookup"><span data-stu-id="a53d7-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="a53d7-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a53d7-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
