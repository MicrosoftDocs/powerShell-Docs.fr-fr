---
title: Comment valider un modèle d’argument | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidatePattern attribute, example
ms.openlocfilehash: 35104e786d4b809a711d97fea52ae0e348dd5ca3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782087"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="69451-102">Guide pratique pour valider un modèle d’argument</span><span class="sxs-lookup"><span data-stu-id="69451-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="69451-103">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier le modèle de caractères de l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="69451-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="69451-104">Vous définissez cette règle de validation en déclarant l’attribut ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="69451-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="69451-105">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="69451-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="69451-106">Pour valider un modèle d’argument</span><span class="sxs-lookup"><span data-stu-id="69451-106">To validate an argument pattern</span></span>

- <span data-ttu-id="69451-107">Ajoutez l’attribut Validate comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="69451-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="69451-108">Cet exemple spécifie un modèle de quatre chiffres, où chaque chiffre a une valeur de 0 à 9.</span><span class="sxs-lookup"><span data-stu-id="69451-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="69451-109">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="69451-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="69451-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69451-110">See Also</span></span>

[<span data-ttu-id="69451-111">Déclaration de l’attribut ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="69451-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="69451-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="69451-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
