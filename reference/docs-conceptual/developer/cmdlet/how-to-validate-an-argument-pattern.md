---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour valider un modèle d’argument
description: Guide pratique pour valider un modèle d’argument
ms.openlocfilehash: ab5777c918a53c0a3900f87c52e7f14f9cb9b726
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666907"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="d8a78-103">Guide pratique pour valider un modèle d’argument</span><span class="sxs-lookup"><span data-stu-id="d8a78-103">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="d8a78-104">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier le modèle de caractères de l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d8a78-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="d8a78-105">Vous définissez cette règle de validation en déclarant l’attribut ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="d8a78-105">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="d8a78-106">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="d8a78-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="d8a78-107">Pour valider un modèle d’argument</span><span class="sxs-lookup"><span data-stu-id="d8a78-107">To validate an argument pattern</span></span>

- <span data-ttu-id="d8a78-108">Ajoutez l’attribut Validate comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d8a78-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="d8a78-109">Cet exemple spécifie un modèle de quatre chiffres, où chaque chiffre a une valeur de 0 à 9.</span><span class="sxs-lookup"><span data-stu-id="d8a78-109">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

<span data-ttu-id="d8a78-110">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d8a78-110">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8a78-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8a78-111">See Also</span></span>

[<span data-ttu-id="d8a78-112">Déclaration de l’attribut ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="d8a78-112">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="d8a78-113">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8a78-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
