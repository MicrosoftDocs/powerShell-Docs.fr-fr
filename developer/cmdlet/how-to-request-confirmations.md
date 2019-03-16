---
title: Comment demander des Confirmations | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058817"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="8079e-102">Guide pratique pour demander des confirmations</span><span class="sxs-lookup"><span data-stu-id="8079e-102">How to Request Confirmations</span></span>

<span data-ttu-id="8079e-103">Cet exemple montre comment appeler le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes pour demander des confirmations à partir de la utilisateur avant d’effectuer une action.</span><span class="sxs-lookup"><span data-stu-id="8079e-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8079e-104">Pour plus d’informations sur la façon dont Windows PowerShell gère ces demandes, consultez [demande une Confirmation](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="8079e-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="8079e-105">Vous demande confirmation</span><span class="sxs-lookup"><span data-stu-id="8079e-105">To request confirmation</span></span>

1. <span data-ttu-id="8079e-106">Vérifiez que le `SupportsShouldProcess` paramètre de l’attribut de l’applet de commande est défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="8079e-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="8079e-107">(Pour les fonctions ce paramètre est de l’attribut CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="8079e-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="8079e-108">Ajouter un `Force` paramètre à votre applet de commande afin que l’utilisateur peut remplacer une demande de confirmation.</span><span class="sxs-lookup"><span data-stu-id="8079e-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="8079e-109">Ajouter un `if` instruction qui utilise la valeur de retour de la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) méthode pour déterminer si le [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="8079e-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="8079e-110">Ajoutez une deuxième `if` instruction qui utilise la valeur de retour de la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (méthode) et la valeur de la `Force` paramètre pour déterminer si l’opération doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="8079e-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="8079e-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="8079e-111">Example</span></span>

<span data-ttu-id="8079e-112">Dans l’exemple de code suivant, le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) les méthodes sont appelées dans le remplacement de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).</span><span class="sxs-lookup"><span data-stu-id="8079e-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="8079e-113">Toutefois, vous pouvez également appeler ces méthodes à partir de l’autre entrée de méthodes de traitement.</span><span class="sxs-lookup"><span data-stu-id="8079e-113">However, you can also call these methods from the other input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="8079e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8079e-114">See Also</span></span>

[<span data-ttu-id="8079e-115">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8079e-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
