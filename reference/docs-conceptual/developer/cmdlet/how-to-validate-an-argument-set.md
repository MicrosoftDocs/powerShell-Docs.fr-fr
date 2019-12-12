---
title: Comment valider un jeu d’arguments | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365508"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="df359-102">Guide pratique pour valider un jeu d’arguments</span><span class="sxs-lookup"><span data-stu-id="df359-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="df359-103">Cet exemple montre comment spécifier une règle de validation que le runtime Windows PowerShell peut utiliser pour vérifier l’argument de paramètre avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="df359-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="df359-104">Cette règle de validation fournit un ensemble de valeurs valides pour l’argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="df359-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="df359-105">Pour plus d’informations sur la classe qui définit cet attribut, consultez [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="df359-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="df359-106">Pour valider un jeu d’arguments</span><span class="sxs-lookup"><span data-stu-id="df359-106">To validate an argument set</span></span>

- <span data-ttu-id="df359-107">Ajoutez l’attribut ValidateSet comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="df359-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="df359-108">Cet exemple spécifie un ensemble de trois valeurs possibles pour le paramètre `UserName`.</span><span class="sxs-lookup"><span data-stu-id="df359-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="df359-109">Pour plus d’informations sur la façon de déclarer cet attribut, consultez [déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="df359-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df359-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df359-110">See Also</span></span>

[<span data-ttu-id="df359-111">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="df359-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="df359-112">Déclaration d’attribut ValidateSet</span><span class="sxs-lookup"><span data-stu-id="df359-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="df359-113">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="df359-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
