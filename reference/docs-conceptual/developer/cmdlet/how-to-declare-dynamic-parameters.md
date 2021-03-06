---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour déclarer des paramètres dynamiques
description: Guide pratique pour déclarer des paramètres dynamiques
ms.openlocfilehash: 0f5a8f249b414663aa9702a908ea5c8ca24755ff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667077"
---
# <a name="how-to-declare-dynamic-parameters"></a>Guide pratique pour déclarer des paramètres dynamiques

Cet exemple montre comment définir des paramètres dynamiques qui sont ajoutés à l’applet de commande au moment de l’exécution. Dans cet exemple, le `Department` paramètre est ajouté à l’applet de commande chaque fois que l’utilisateur spécifie le `Employee` paramètre de commutateur. Pour plus d’informations sur les paramètres dynamiques, consultez [paramètres dynamiques des applets](./cmdlet-dynamic-parameters.md)de commande.

## <a name="to-define-dynamic-parameters"></a>Pour définir des paramètres dynamiques

1. Dans la déclaration de classe de l’applet de commande, ajoutez l’interface [System. Management. Automation. Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) comme indiqué.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. Appelez la méthode [System. Management. Automation. Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) , qui retourne l’objet dans lequel les paramètres dynamiques sont définis. Dans cet exemple, la méthode est appelée lorsque le `Employee` paramètre est spécifié.

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

3. Déclarez une classe qui définit les paramètres dynamiques à ajouter. Vous pouvez utiliser les attributs que vous avez utilisés pour déclarer les paramètres d’applet de commande statiques afin de déclarer les paramètres dynamiques.

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

## <a name="example"></a>Exemple

Dans cet exemple, le `Department` paramètre est ajouté chaque fois que l’utilisateur spécifie le `Employee` paramètre. Le `Department` paramètre est un paramètre facultatif, et l’attribut ValidateSet est utilisé pour spécifier les arguments autorisés.

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

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System. Management. Automation. Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Paramètres dynamiques des applets de commande](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
