---
title: Démarrage rapide de l’hôte Windows PowerShell | Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: fea6bd5ae49ecf552c583271ee9d869b1ccebae8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779401"
---
# <a name="windows-powershell-host-quickstart"></a>Hôte Windows PowerShell - Démarrage rapide

Pour héberger Windows PowerShell dans votre application, vous utilisez la classe [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .
Cette classe fournit des méthodes qui créent un pipeline de commandes, puis exécutent ces commandes dans une instance d’exécution.
La façon la plus simple de créer une application hôte consiste à utiliser l’instance d’exécution par défaut.
L’instance d’exécution par défaut contient toutes les commandes Windows PowerShell de base.
Si vous souhaitez que votre application expose uniquement un sous-ensemble des commandes Windows PowerShell, vous devez créer une instance d’exécution personnalisée.

## <a name="using-the-default-runspace"></a>Utilisation de l’instance d’exécution par défaut

Pour commencer, nous allons utiliser l’instance d’exécution par défaut et utiliser les méthodes de la classe [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) pour ajouter des commandes, des paramètres, des instructions et des scripts à un pipeline.

### <a name="addcommand"></a>AddCommand

Vous utilisez la méthode [System. Management. Automation. PowerShell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) pour ajouter des commandes au pipeline.
Par exemple, supposons que vous souhaitez obtenir la liste des processus en cours d’exécution sur l’ordinateur.
Pour exécuter cette commande, procédez comme suit.

1. Créez un objet [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .

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

Si vous appelez la méthode AddCommand plusieurs fois avant d’appeler la méthode [System. Management. Automation. PowerShell. Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , le résultat de la première commande est dirigé vers le deuxième, et ainsi de suite.
Si vous ne souhaitez pas diriger le résultat d’une commande précédente vers une commande, ajoutez-le en appelant [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) à la place.

### <a name="addparameter"></a>AddParameter

L’exemple précédent exécute une seule commande sans aucun paramètre.
Vous pouvez ajouter des paramètres à la commande à l’aide de la méthode [System. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) .
Par exemple, le code suivant obtient une liste de tous les processus nommés `PowerShell` en cours d’exécution sur l’ordinateur.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Vous pouvez ajouter des paramètres supplémentaires en appelant la méthode AddParameter de façon répétée.

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

Vous pouvez également ajouter un dictionnaire de noms et de valeurs de paramètres en appelant la méthode [System. Management. Automation. PowerShell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Vous pouvez simuler le traitement par lot à l’aide de la méthode [System. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , qui ajoute une instruction supplémentaire à la fin du pipeline.
Le code suivant obtient une liste des processus en cours d’exécution portant le nom `PowerShell` , puis obtient la liste des services en cours d’exécution.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Vous pouvez exécuter un script existant en appelant la méthode [System. Management. Automation. PowerShell. AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .
L’exemple suivant ajoute un script au pipeline et l’exécute.
Cet exemple suppose qu’il existe déjà un script nommé `MyScript.ps1` dans un dossier nommé `D:\PSScripts` .

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Il existe également une version de la méthode AddScript qui accepte un paramètre booléen nommé `useLocalScope` .
Si ce paramètre a la valeur `true` , le script est exécuté dans l’étendue locale.
Le code suivant exécute le script dans l’étendue locale.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Création d’une instance d’exécution personnalisée

Tandis que l’instance d’exécution par défaut utilisée dans les exemples précédents charge toutes les commandes Windows PowerShell de base, vous pouvez créer une instance d’exécution personnalisée qui charge uniquement un sous-ensemble spécifié de toutes les commandes.
Vous pouvez le faire pour améliorer les performances (le chargement d’un plus grand nombre de commandes est un gain de performances) ou pour limiter la capacité de l’utilisateur à effectuer des opérations.
Une instance d’exécution qui expose uniquement un nombre limité de commandes est appelée une instance d’exécution limitée.
Pour créer une instance d’exécution avec restriction, vous utilisez les classes [System. Management. Automation. instances d’exécution. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) et [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

### <a name="creating-an-initialsessionstate-object"></a>Création d’un objet InitialSessionState

Pour créer une instance d’exécution personnalisée, vous devez d’abord créer un objet [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .
Dans l’exemple suivant, nous utilisons [System. Management. Automation. instances d’exécution. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) pour créer une instance d’exécution après la création d’un objet InitialSessionState par défaut.

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

Dans l’exemple précédent, nous avons créé un objet [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) par défaut qui charge l’ensemble du noyau Windows PowerShell intégré.
Nous aurions pu également appeler la méthode [System.Management.Automation.Runspaces.InitialSessionState. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) pour créer un objet InitialSessionState qui chargera uniquement les commandes dans le composant logiciel enfichable Microsoft. PowerShell. Core.
Pour créer une instance d’exécution plus restreinte, vous devez créer un objet InitialSessionState vide en appelant la méthode [System.Management.Automation.Runspaces.InitialSessionState. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) , puis ajouter des commandes au InitialSessionState.

L’utilisation d’une instance d’exécution qui charge uniquement les commandes que vous spécifiez fournit des performances considérablement améliorées.

Vous utilisez les méthodes de la classe [System. Management. Automation. instances d’exécution. SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) pour définir des applets de commande pour l’état de session initial.
L’exemple suivant crée un état de session initial vide, puis définit et ajoute `Get-Command` les `Import-Module` commandes et à l’état de session initial.
Nous créons ensuite une instance d’exécution restreinte par cet état de session initial, puis nous exécutons les commandes dans cette instance d’exécution.

Créez l’état de session initial.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Définir et ajouter des commandes à l’état de session initial.

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

Exécutez une commande et affichez le résultat.

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

Une fois exécuté, le résultat de ce code se présente comme suit.

```powershell
Get-Command
Import-Module
```
