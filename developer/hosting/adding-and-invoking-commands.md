---
title: Ajout et l’appel des commandes | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083023"
---
# <a name="adding-and-invoking-commands"></a>Ajout et appel de commandes

Après avoir créé une instance d’exécution, vous pouvez ajouter des PowerShellcommands de Windows et les scripts à un pipeline et puis appelez le pipeline de manière synchrone ou asynchrone.

## <a name="creating-a-pipeline"></a>Création d’un pipeline

 Le [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe fournit plusieurs méthodes pour ajouter des commandes, des paramètres et des scripts au pipeline. Vous pouvez appeler le pipeline de façon synchrone en appelant une surcharge de la [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (méthode), ou de façon asynchrone en appelant une surcharge de la [ System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) , puis le [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (méthode).

### <a name="addcommand"></a>AddCommand

1. Créer un [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objet.

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

 Si vous appelez le [System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) méthode plusieurs fois avant d’appeler le [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (méthode), le résultat de la première commande est dirigée vers le deuxième et ainsi de suite. Si vous ne souhaitez pas canalisez le résultat d’une commande à une commande précédente, ajoutez-le en appelant le [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) à la place.

### <a name="addparameter"></a>AddParameter

 L’exemple précédent exécute une commande unique sans aucun paramètre. Vous pouvez ajouter des paramètres à la commande à l’aide de la [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) (méthode), par exemple, le code suivant obtient une liste de tous les processus qui sont nommés `PowerShell` en cours d’exécution le machine.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Vous pouvez ajouter des paramètres supplémentaires en appelant [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) à plusieurs reprises.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 Vous pouvez également ajouter un dictionnaire de noms de paramètres et valeurs en appelant le [System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) (méthode).

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 Vous pouvez simuler le traitement par lots à l’aide de la [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) (méthode), qui ajoute une instruction supplémentaire à la fin du pipeline, le code suivant obtient une liste des processus en cours avec le nom `PowerShell`, puis obtient la liste des services en cours d’exécution.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Vous pouvez exécuter un script existant en appelant le [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) (méthode). L’exemple suivant ajoute un script au pipeline et l’exécute. Cet exemple suppose un script nommé existe déjà `MyScript.ps1` dans un dossier nommé `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Il existe également une version de la [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) méthode qui accepte un paramètre booléen nommé `useLocalScope`. Si ce paramètre est défini sur `true`, puis le script est exécuté dans l’étendue locale. Le code suivant exécute le script dans l’étendue locale.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Appel de façon synchrone un pipeline

 Après avoir ajouté des éléments dans le pipeline, vous l’appelez. Pour appeler le pipeline de manière synchrone, vous appelez une surcharge de la [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (méthode). L’exemple suivant montre comment appeler de façon synchrone un pipeline.

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

### <a name="invoking-a-pipeline-asynchronously"></a>Appelle de façon asynchrone un pipeline

 Vous appelez un pipeline de façon asynchrone en appelant une surcharge de la [System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) pour créer un [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) objet, puis en appelant le [ System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (méthode).

 L’exemple suivant montre comment appeler un pipeline de façon asynchrone.

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
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
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
