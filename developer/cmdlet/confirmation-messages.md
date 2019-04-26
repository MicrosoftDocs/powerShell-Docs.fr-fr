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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068366"
---
# <a name="confirmation-messages"></a><span data-ttu-id="6711b-102">Messages de confirmation</span><span class="sxs-lookup"><span data-stu-id="6711b-102">Confirmation Messages</span></span>

<span data-ttu-id="6711b-103">Voici les messages de confirmation différents qui peuvent être affichées selon les variantes de la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes qui sont appelées.</span><span class="sxs-lookup"><span data-stu-id="6711b-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6711b-104">Pour l’exemple de code qui montre comment demander des confirmations, consultez [comment des Confirmations de demande](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="6711b-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="6711b-105">Spécification de la ressource</span><span class="sxs-lookup"><span data-stu-id="6711b-105">Specifying the Resource</span></span>

<span data-ttu-id="6711b-106">Vous pouvez spécifier la ressource doit être modifiée en appelant le [System.Management.Automation.Cmdlet.Shouldprocess%2A ? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (méthode).</span><span class="sxs-lookup"><span data-stu-id="6711b-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="6711b-107">Dans ce cas, vous fournissez la ressource à l’aide de le `target` paramètre de la méthode et l’opération est ajouté par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6711b-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="6711b-108">Dans le message suivant, le texte « MyResource » est la ressource de l’action et l’opération est le nom de la commande qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="6711b-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="6711b-109">Si l’utilisateur sélectionne **Oui** ou **Oui pour tout** à la confirmation de la demande (comme indiqué dans l’exemple suivant), un appel à la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)méthode est effectuée, ce qui entraîne un deuxième message de confirmation s’affiche.</span><span class="sxs-lookup"><span data-stu-id="6711b-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="6711b-110">Spécification de l’opération et les ressources</span><span class="sxs-lookup"><span data-stu-id="6711b-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="6711b-111">Vous pouvez spécifier la ressource qui doit être modifié et l’opération que la commande va effectuer en appelant le [System.Management.Automation.Cmdlet.Shouldprocess%2A ? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) (méthode).</span><span class="sxs-lookup"><span data-stu-id="6711b-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="6711b-112">Dans ce cas, vous fournissez la ressource à l’aide de la `target` paramètre et l’opération à l’aide de le `target` paramètre.</span><span class="sxs-lookup"><span data-stu-id="6711b-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="6711b-113">Dans le message suivant, le texte « MyResource » est la ressource de l’action et « MyAction » est l’opération à effectuer.</span><span class="sxs-lookup"><span data-stu-id="6711b-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="6711b-114">Si l’utilisateur sélectionne **Oui** ou **Oui pour tout** le message précédent, un appel à la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthode est effectué, ce qui conduit un deuxième message de confirmation s’affiche.</span><span class="sxs-lookup"><span data-stu-id="6711b-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="6711b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6711b-115">See Also</span></span>

[<span data-ttu-id="6711b-116">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6711b-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
