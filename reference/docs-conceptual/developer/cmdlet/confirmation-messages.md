---
title: Messages de confirmation | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365728"
---
# <a name="confirmation-messages"></a><span data-ttu-id="c8acb-102">Messages de confirmation</span><span class="sxs-lookup"><span data-stu-id="c8acb-102">Confirmation Messages</span></span>

<span data-ttu-id="c8acb-103">Voici différents messages de confirmation qui peuvent être affichés en fonction des variantes des méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) qui sont appelées.</span><span class="sxs-lookup"><span data-stu-id="c8acb-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8acb-104">Pour obtenir un exemple de code qui montre comment demander des confirmations, consultez [Comment demander des confirmations](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="c8acb-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="c8acb-105">Spécification de la ressource</span><span class="sxs-lookup"><span data-stu-id="c8acb-105">Specifying the Resource</span></span>

<span data-ttu-id="c8acb-106">Vous pouvez spécifier la ressource qui va être modifiée en appelant [System. Management. Automation. cmdlet. ShouldProcess% 2A ? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (méthode).</span><span class="sxs-lookup"><span data-stu-id="c8acb-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="c8acb-107">Dans ce cas, vous fournissez la ressource à l’aide du paramètre `target` de la méthode, et l’opération est ajoutée par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8acb-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="c8acb-108">Dans le message suivant, le texte « MyResource » est la ressource sur laquelle l’opération est effectuée et l’opération est le nom de la commande qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="c8acb-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="c8acb-109">Si l’utilisateur sélectionne **Oui** ou **Oui pour l’ensemble** de la demande de confirmation (comme indiqué dans l’exemple suivant), un appel à la méthode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) est effectué, ce qui entraîne l’affichage d’un deuxième message de confirmation.</span><span class="sxs-lookup"><span data-stu-id="c8acb-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="c8acb-110">Spécification de l’opération et de la ressource</span><span class="sxs-lookup"><span data-stu-id="c8acb-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="c8acb-111">Vous pouvez spécifier la ressource qui va être modifiée et l’opération que la commande va effectuer en appelant [System. Management. Automation. cmdlet. ShouldProcess% 2A ? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (méthode).</span><span class="sxs-lookup"><span data-stu-id="c8acb-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="c8acb-112">Dans ce cas, vous fournissez la ressource à l’aide du paramètre `target` et de l’opération à l’aide du paramètre `target`.</span><span class="sxs-lookup"><span data-stu-id="c8acb-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="c8acb-113">Dans le message suivant, le texte « MyResource » est la ressource traitée et « MyAction » est l’opération à effectuer.</span><span class="sxs-lookup"><span data-stu-id="c8acb-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="c8acb-114">Si l’utilisateur sélectionne **Oui** ou **Oui pour tout** le message précédent, un appel à la méthode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) est effectué, ce qui entraîne l’affichage d’un deuxième message de confirmation.</span><span class="sxs-lookup"><span data-stu-id="c8acb-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="c8acb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8acb-115">See Also</span></span>

[<span data-ttu-id="c8acb-116">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8acb-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
