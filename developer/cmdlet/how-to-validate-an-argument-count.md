---
title: Comment valider un nombre d’arguments | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859135"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="bf119-102">Guide pratique pour valider un nombre d’arguments</span><span class="sxs-lookup"><span data-stu-id="bf119-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="bf119-103">Cet exemple montre comment spécifier une règle de validation que le runtime de Windows PowerShell peut utiliser pour vérifier le nombre d’arguments (nombre) qui accepte un paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bf119-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="bf119-104">Vous définissez cette règle de validation en déclarant l’attribut ValidateCount.</span><span class="sxs-lookup"><span data-stu-id="bf119-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="bf119-105">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="bf119-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="bf119-106">Pour valider un nombre d’arguments</span><span class="sxs-lookup"><span data-stu-id="bf119-106">To validate an argument count</span></span>

- <span data-ttu-id="bf119-107">Ajoutez l’attribut de validation comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="bf119-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="bf119-108">Cet exemple spécifie que le paramètre accepte un argument ou jusqu'à trois arguments.</span><span class="sxs-lookup"><span data-stu-id="bf119-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="bf119-109">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="bf119-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf119-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf119-110">See Also</span></span>

[<span data-ttu-id="bf119-111">Déclaration d’attribut de ValidateCount</span><span class="sxs-lookup"><span data-stu-id="bf119-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="bf119-112">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf119-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
