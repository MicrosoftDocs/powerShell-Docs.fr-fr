---
title: Guide de démarrage rapide de Windows PowerShell Host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: cc014487a680747ad59437052f79d4576154a1cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059675"
---
# <a name="windows-powershell-host-quickstart"></a>Hôte Windows PowerShell - Démarrage rapide

Pour héberger Windows PowerShell dans votre application, vous utilisez le [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe. Cette classe fournit des méthodes qui de créer un pipeline de commandes, puis exécutez ces commandes dans une instance d’exécution. Pour créer une application hôte, le plus simple consiste à utiliser l’instance d’exécution par défaut. L’instance d’exécution par défaut contient toutes les commandes Windows PowerShell core. Si vous souhaitez que votre application pour exposer uniquement un sous-ensemble des commandes Windows PowerShell, vous devez créer une instance d’exécution personnalisé.

## <a name="using-the-default-runspace"></a>À l’aide de l’instance d’exécution par défaut

Pour commencer, nous allons utiliser l’instance d’exécution par défaut et utiliser les méthodes de la [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe pour ajouter des commandes, des paramètres, des instructions et des scripts à un pipeline.

### <a name="addcommand"></a>AddCommand

Vous utilisez le [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) méthode de la [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe pour ajouter des commandes au pipeline. Par exemple, supposons que vous souhaitez obtenir la liste des processus en cours d’exécution sur l’ordinateur. La façon d’exécuter cette commande est la suivante.

1. Créer un [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) objet.

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

Si vous appelez le [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) méthode plusieurs fois avant d’appeler le [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) (méthode), le résultat de la première commande est dirigée vers le deuxième et ainsi de suite. Si vous ne souhaitez pas canalisez le résultat d’une commande à une commande précédente, ajoutez-le en appelant le [System.Management.Automation.Powershell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) à la place.

### <a name="addparameter"></a>AddParameter

L’exemple précédent exécute une commande unique sans aucun paramètre. Vous pouvez ajouter des paramètres à la commande à l’aide de la [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) (méthode), par exemple, le code suivant obtient une liste de tous les processus qui sont nommés `PowerShell` en cours d’exécution le machine.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Vous pouvez ajouter des paramètres supplémentaires en appelant [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) à plusieurs reprises.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

Vous pouvez également ajouter un dictionnaire de noms de paramètres et valeurs en appelant le [System.Management.Automation.PowerShell.AddParameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) (méthode).

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Vous pouvez simuler le traitement par lots à l’aide de la [System.Management.Automation.PowerShell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) (méthode), qui ajoute une instruction supplémentaire à la fin du pipeline, le code suivant obtient une liste des processus en cours avec le nom `PowerShell`, puis obtient la liste des services en cours d’exécution.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Vous pouvez exécuter un script existant en appelant le [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) (méthode). L’exemple suivant ajoute un script au pipeline et l’exécute. Cet exemple suppose un script nommé existe déjà `MyScript.ps1` dans un dossier nommé `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Il existe également une version de la [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) méthode qui accepte un paramètre booléen nommé `useLocalScope`. Si ce paramètre est défini sur `true`, puis le script est exécuté dans l’étendue locale. Le code suivant exécute le script dans l’étendue locale.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Création d’une instance d’exécution personnalisée

Tandis que l’instance d’exécution par défaut utilisé dans les exemples précédents charge de toutes les commandes Windows PowerShell core, vous pouvez créer une instance d’exécution personnalisée qui charge uniquement un sous-ensemble spécifié de toutes les commandes. Vous pouvez souhaiter procéder ainsi pour améliorer les performances (le chargement d’un plus grand nombre de commandes est un gain de performances), ou pour limiter la capacité de l’utilisateur à effectuer des opérations. Une instance d’exécution qui expose uniquement un nombre limité de commandes est appelée une instance d’exécution contrainte. Pour créer une instance d’exécution limitée, vous utilisez le [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) et [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.

### <a name="creating-an-initialsessionstate-object"></a>Création d’un objet InitialSessionState

Pour créer une instance d’exécution personnalisée, vous devez d’abord créer un [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet. Dans l’exemple suivant, nous utilisons le [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) pour créer une instance d’exécution après la création d’une valeur par défaut [System.Management.Automation.Runspaces.InitialSessionState ](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Restriction de l’instance d’exécution

Dans l’exemple précédent, nous avons créé une valeur par défaut [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet qui charge tous des principales intégré Windows PowerShell. Nous pouvons également avoir appelé la [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) méthode pour créer un objet InitialSessionState qui charge uniquement les commandes dans le Microsoft.PowerShell.Core composant logiciel enfichable. Pour créer une instance d’exécution plus limité, vous devez créer vide [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet en appelant le [ System.Management.Automation.Runspaces.InitialSessionState.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) (méthode), puis ajoutez des commandes à l’InitialSessionState.

À l’aide d’une instance d’exécution qui charge uniquement les commandes que vous spécifiez fournit des performances significativement accrues.

Vous utilisez les méthodes de la [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe pour définir des applets de commande pour l’état de session initiale. L’exemple suivant crée un état de session initiale vide, puis définit et ajoute le `Get-Command` et `Import-Module` commandes à l’état de session initiale. Nous avons créer une instance d’exécution limitée par cet état de session initial et que vous exécutez les commandes dans cette instance d’exécution.

Créer l’état de session initiale.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Définir et ajouter des commandes à l’état de session initiale.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Créez et ouvrez l’instance d’exécution.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Exécuter une commande et afficher le résultat.

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

Lors de l’exécution, la sortie de ce code se présentera comme suit.

```powershell
Get-Command
Import-Module
```
