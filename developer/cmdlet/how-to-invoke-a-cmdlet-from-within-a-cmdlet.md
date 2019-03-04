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
ms.openlocfilehash: d4564b51b74422cdaec3878b227ffc6be7c97949
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855885"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Guide pratique pour appeler une applet de commande à partir d’une applet de commande

Cet exemple montre comment appeler une applet de commande à partir d’une autre applet de commande, qui vous permet d’ajouter les fonctionnalités de l’applet de commande appelée à l’applet de commande que vous développez. Dans cet exemple, le `Get-Process` applet de commande est appelée pour obtenir les processus qui sont exécutent sur l’ordinateur local. L’appel à la `Get-Process` applet de commande est équivalente à la commande suivante. Cette commande récupère tous les processus dont le nom commence par les caractères « a » à « t ».

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Vous pouvez appeler uniquement ces applets de commande qui dérivent directement de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Vous ne pouvez pas appeler une applet de commande qui dérive de la [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Pour appeler une applet de commande à partir d’une applet de commande

1. Assurez-vous que l’assembly qui définit l’applet de commande à appeler est référencé et que le texte approprié `using` instruction est ajoutée. Dans cet exemple, les espaces de noms suivants sont ajoutés.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. Dans la méthode de l’applet de commande de traitement d’entrée, créez une nouvelle instance de l’applet de commande à appeler. Dans cet exemple, un objet de type [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) est créé en même temps que la chaîne qui contient les arguments qui sont utilisés lorsque l’applet de commande est appelée.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Appelez le [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) méthode à appeler le `Get-Process` applet de commande.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Exemple

Dans cet exemple, le `Get-Process` applet de commande est appelée depuis le [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) méthode d’applet de commande.

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
