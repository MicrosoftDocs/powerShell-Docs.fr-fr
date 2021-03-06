---
ms.date: 09/13/2016
ms.topic: reference
title: Ajout et appel de commandes
description: Ajout et appel de commandes
ms.openlocfilehash: f539172eaf119fe5774e158c77a00276c8ba9e0a
ms.sourcegitcommit: 880b00218708724a76503000c9eca181f4e00891
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2021
ms.locfileid: "99049423"
---
# <a name="adding-and-invoking-commands"></a>Ajout et appel de commandes

Après avoir créé une instance d’exécution, vous pouvez ajouter des PowerShellcommands et des scripts Windows à un pipeline, puis appeler le pipeline de manière synchrone ou asynchrone.

## <a name="creating-a-pipeline"></a>Création d’un pipeline

La classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) fournit plusieurs méthodes permettant d’ajouter des commandes, des paramètres et des scripts au pipeline. Vous pouvez appeler le pipeline de façon synchrone en appelant une surcharge de la méthode [System. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , ou de façon asynchrone en appelant une surcharge de [System. Management. Automation. PowerShell. BeginInvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) , puis la méthode [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

### <a name="addcommand"></a>AddCommand

1. Créez un objet [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Ajoutez la commande que vous souhaitez exécuter.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Appelez la commande.

   ```csharp
   ps.Invoke();
   ```

Si vous appelez la méthode [System. Management. Automation. PowerShell. AddCommand *](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) plusieurs fois avant d’appeler la méthode [System. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , le résultat de la première commande est dirigé vers le deuxième, et ainsi de suite. Si vous ne souhaitez pas diriger le résultat d’une commande précédente vers une commande, ajoutez-le en appelant [System. Management. Automation. PowerShell. Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) à la place.

### <a name="addparameter"></a>AddParameter

 L’exemple précédent exécute une seule commande sans aucun paramètre. Vous pouvez ajouter des paramètres à la commande à l’aide de la méthode [System. Management. Automation. PSCommand. AddParameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) . par exemple, le code suivant obtient une liste de tous les processus nommés `PowerShell` en cours d’exécution sur l’ordinateur.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Vous pouvez ajouter des paramètres supplémentaires en appelant [System. Management. Automation. PSCommand. AddParameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) à plusieurs reprises.

```csharp
PowerShell.Create().AddCommand("Get-Command")
                   .AddParameter("Name", "Get-VM")
                   .AddParameter("Module", "Hyper-V")
                   .Invoke();
```

Vous pouvez également ajouter un dictionnaire de noms et de valeurs de paramètres en appelant la méthode [System. Management. Automation. PowerShell. AddParameters *](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "Get-VM");

parameters.Add("Module", "Hyper-V");
PowerShell.Create().AddCommand("Get-Command")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Vous pouvez simuler le traitement par lot à l’aide de la méthode [System. Management. Automation. PowerShell. Addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , qui ajoute une instruction supplémentaire à la fin du pipeline. le code suivant obtient une liste des processus en cours d’exécution avec le nom `PowerShell` , puis obtient la liste des services en cours d’exécution.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Vous pouvez exécuter un script existant en appelant la méthode [System. Management. Automation. PowerShell. addscript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) . L’exemple suivant ajoute un script au pipeline et l’exécute. Cet exemple suppose qu’il existe déjà un script nommé `MyScript.ps1` dans un dossier nommé `D:\PSScripts` .

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(File.ReadAllText(@"D:\PSScripts\MyScript.ps1")).Invoke();
```

Il existe également une version de la méthode [System. Management. Automation. PowerShell. addscript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) qui accepte un paramètre booléen nommé `useLocalScope` . Si ce paramètre a la valeur `true` , le script est exécuté dans l’étendue locale. Le code suivant exécute le script dans l’étendue locale.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(File.ReadAllText(@"D:\PSScripts\MyScript.ps1"), true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Appel d’un pipeline de façon synchrone

Une fois que vous avez ajouté des éléments au pipeline, vous l’appelez. Pour appeler le pipeline de façon synchrone, vous appelez une surcharge de la méthode [System. Management. Automation. PowerShell. Invoke *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) . L’exemple suivant montre comment appeler de manière synchrone un pipeline.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>Appel d’un pipeline de manière asynchrone

Vous appelez un pipeline de manière asynchrone en appelant une surcharge de [System. Management. Automation. PowerShell. BeginInvoke *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) pour créer un objet [IAsyncResult](/dotnet/api/system.iasyncresult) , puis en appelant la méthode [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

 L’exemple suivant montre comment appeler un pipeline de manière asynchrone.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult asyncpl = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(asyncpl))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>Voir aussi

 [Création d’un InitialSessionState](./creating-an-initialsessionstate.md)

 [Création d’une instance d’exécution contrainte](./creating-a-constrained-runspace.md)
