---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour appeler une applet de commande à partir d’une applet de commande
description: Guide pratique pour appeler une applet de commande à partir d’une applet de commande
ms.openlocfilehash: d137ac895f66000329de76a2c16a74b02c0e82ca
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667043"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Guide pratique pour appeler une applet de commande à partir d’une applet de commande

Cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande, ce qui vous permet d’ajouter la fonctionnalité de l’applet de commande appelée à l’applet de commande que vous développez. Dans cet exemple, l' `Get-Process` applet de commande est appelée pour récupérer les processus en cours d’exécution sur l’ordinateur local. L’appel à l' `Get-Process` applet de commande est équivalent à la commande suivante. Cette commande récupère tous les processus dont les noms commencent par les caractères « a » à « t ».

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Vous pouvez appeler uniquement les applets de commande qui dérivent directement de la classe [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet) de commande. Vous ne pouvez pas appeler une applet de commande qui dérive de la classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Pour appeler une applet de commande à partir d’une applet de commande

1. Assurez-vous que l’assembly qui définit l’applet de commande à appeler est référencé et que l' `using` instruction appropriée est ajoutée. Dans cet exemple, les espaces de noms suivants sont ajoutés.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. Dans la méthode de traitement d’entrée de l’applet de commande, créez une nouvelle instance de l’applet de commande à appeler. Dans cet exemple, un objet de type [Microsoft. PowerShell. Commands. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) est créé avec la chaîne qui contient les arguments utilisés lors de l’appel de l’applet de commande.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Appelez la méthode [System. Management. Automation. cmdlet. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) pour appeler l' `Get-Process` applet de commande.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Exemple

Dans cet exemple, l' `Get-Process` applet de commande est appelée à partir de la méthode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) d’une applet de commande.

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

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
