---
title: L’appel d’une applet de commande à partir d’une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055901"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="c6e9e-102">Guide pratique pour appeler une applet de commande à partir d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6e9e-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="c6e9e-103">Cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande, qui vous permet d’ajouter les fonctionnalités de l’applet de commande appelée à l’applet de commande que vous développez.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="c6e9e-104">Dans cet exemple, le `Get-Process` applet de commande est appelée pour obtenir les processus qui sont exécutent sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="c6e9e-105">L’appel à la `Get-Process` applet de commande est équivalente à la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="c6e9e-106">Cette commande récupère tous les processus dont le nom commence par les caractères « a » à « t ».</span><span class="sxs-lookup"><span data-stu-id="c6e9e-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="c6e9e-107">Vous pouvez appeler uniquement ces applets de commande qui dérivent directement de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="c6e9e-108">Vous ne pouvez pas appeler une applet de commande qui dérive de la [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="c6e9e-109">Pour appeler une applet de commande à partir d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="c6e9e-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="c6e9e-110">Assurez-vous que l’assembly qui définit l’applet de commande à appeler est référencé et que le texte approprié `using` instruction est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="c6e9e-111">Dans cet exemple, les espaces de noms suivants sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="c6e9e-112">Dans la méthode de l’applet de commande de traitement d’entrée, créez une nouvelle instance de l’applet de commande à appeler.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="c6e9e-113">Dans cet exemple, un objet de type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) est créé en même temps que la chaîne qui contient les arguments qui sont utilisés lorsque l’applet de commande est appelée.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="c6e9e-114">Appelez le [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) méthode à appeler le `Get-Process` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="c6e9e-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6e9e-115">Example</span></span>

<span data-ttu-id="c6e9e-116">Dans cet exemple, le `Get-Process` applet de commande est appelée depuis le [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) méthode d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="c6e9e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6e9e-117">See Also</span></span>

[<span data-ttu-id="c6e9e-118">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6e9e-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
