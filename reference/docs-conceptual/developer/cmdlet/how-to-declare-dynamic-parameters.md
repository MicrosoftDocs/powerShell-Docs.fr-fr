---
title: Comment déclarer des paramètres dynamiques | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364418"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="f3c32-102">Guide pratique pour déclarer des paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="f3c32-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="f3c32-103">Cet exemple montre comment définir des paramètres dynamiques qui sont ajoutés à l’applet de commande au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f3c32-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="f3c32-104">Dans cet exemple, le paramètre `Department` est ajouté à l’applet de commande chaque fois que l’utilisateur spécifie le paramètre de commutateur `Employee`.</span><span class="sxs-lookup"><span data-stu-id="f3c32-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="f3c32-105">Pour plus d’informations sur les paramètres dynamiques, consultez [paramètres dynamiques des applets](./cmdlet-dynamic-parameters.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="f3c32-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="f3c32-106">Pour définir des paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="f3c32-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="f3c32-107">Dans la déclaration de classe de l’applet de commande, ajoutez l’interface [System. Management. Automation. Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) comme indiqué.</span><span class="sxs-lookup"><span data-stu-id="f3c32-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="f3c32-108">Appelez la méthode [System. Management. Automation. Idynamicparameters. Getdynamicparameters \*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) , qui retourne l’objet dans lequel les paramètres dynamiques sont définis.</span><span class="sxs-lookup"><span data-stu-id="f3c32-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="f3c32-109">Dans cet exemple, la méthode est appelée lorsque le paramètre `Employee` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="f3c32-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. <span data-ttu-id="f3c32-110">Déclarez une classe qui définit les paramètres dynamiques à ajouter.</span><span class="sxs-lookup"><span data-stu-id="f3c32-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="f3c32-111">Vous pouvez utiliser les attributs que vous avez utilisés pour déclarer les paramètres d’applet de commande statiques afin de déclarer les paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="f3c32-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a><span data-ttu-id="f3c32-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3c32-112">Example</span></span>

<span data-ttu-id="f3c32-113">Dans cet exemple, le paramètre `Department` est ajouté chaque fois que l’utilisateur spécifie le paramètre `Employee`.</span><span class="sxs-lookup"><span data-stu-id="f3c32-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="f3c32-114">Le paramètre `Department` est un paramètre facultatif, et l’attribut ValidateSet est utilisé pour spécifier les arguments autorisés.</span><span class="sxs-lookup"><span data-stu-id="f3c32-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a><span data-ttu-id="f3c32-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3c32-115">See Also</span></span>

[<span data-ttu-id="f3c32-116">System. Management. Automation. RuntimeDefinedParameterDictionary</span><span class="sxs-lookup"><span data-stu-id="f3c32-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="f3c32-117">System. Management. Automation. Idynamicparameters. Getdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="f3c32-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="f3c32-118">Paramètres dynamiques des applets de commande</span><span class="sxs-lookup"><span data-stu-id="f3c32-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="f3c32-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f3c32-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)