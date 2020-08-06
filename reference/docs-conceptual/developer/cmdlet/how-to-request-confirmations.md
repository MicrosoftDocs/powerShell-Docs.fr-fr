---
title: Comment demander des confirmations | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebe928724f1b750afc11c1e3c1207375f4ec8e42
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784093"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="79dc1-102">Guide pratique pour demander des confirmations</span><span class="sxs-lookup"><span data-stu-id="79dc1-102">How to Request Confirmations</span></span>

<span data-ttu-id="79dc1-103">Cet exemple montre comment appeler les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) pour demander des confirmations à l’utilisateur avant qu’une action soit effectuée.</span><span class="sxs-lookup"><span data-stu-id="79dc1-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79dc1-104">Pour plus d’informations sur la façon dont Windows PowerShell gère ces requêtes, consultez [demande de confirmation](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="79dc1-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="79dc1-105">Pour demander une confirmation</span><span class="sxs-lookup"><span data-stu-id="79dc1-105">To request confirmation</span></span>

1. <span data-ttu-id="79dc1-106">Assurez-vous que le `SupportsShouldProcess` paramètre de l’attribut d’applet de commande a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="79dc1-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="79dc1-107">(Pour functions, il s’agit d’un paramètre de l’attribut CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="79dc1-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="79dc1-108">Ajoutez un `Force` paramètre à votre applet de commande pour permettre à l’utilisateur de remplacer une demande de confirmation.</span><span class="sxs-lookup"><span data-stu-id="79dc1-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="79dc1-109">Ajoutez une `if` instruction qui utilise la valeur de retour de la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pour déterminer si la méthode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) est appelée.</span><span class="sxs-lookup"><span data-stu-id="79dc1-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="79dc1-110">Ajoutez une deuxième `if` instruction qui utilise la valeur de retour de la méthode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) et la valeur du `Force` paramètre pour déterminer si l’opération doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="79dc1-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="79dc1-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="79dc1-111">Example</span></span>

<span data-ttu-id="79dc1-112">Dans l’exemple de code suivant, les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) sont appelées à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="79dc1-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="79dc1-113">Toutefois, vous pouvez également appeler ces méthodes à partir des autres méthodes de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="79dc1-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="79dc1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79dc1-114">See Also</span></span>

[<span data-ttu-id="79dc1-115">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="79dc1-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
