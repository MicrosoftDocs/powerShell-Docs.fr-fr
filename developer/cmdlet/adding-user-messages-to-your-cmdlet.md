---
title: Ajout de Messages de l’utilisateur à votre applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 5b3a5f5d5d02c7d5a3c1d622ec1a3740739c694f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068774"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Ajout de messages utilisateur à votre applet de commande

Applets de commande peut écrire plusieurs types de messages qui peuvent être affichées à l’utilisateur par le runtime de Windows PowerShell. Ces messages incluent les types suivants :

- Messages détaillés qui contiennent des informations utilisateur générales.

- Les messages qui contiennent des informations de résolution des problèmes de débogage.

- Messages d’avertissement qui contiennent une notification indiquant que l’applet de commande est sur le point d’effectuer une opération qui peut avoir des résultats inattendus.

- Rapport de progression des messages qui contiennent des informations sur la quantité utiliser l’applet de commande est terminée lorsque vous effectuez une opération qui prend beaucoup de temps.

Il n’existe aucune limite au nombre de messages que votre applet de commande peut écrire ou le type de message qui écrit votre applet de commande. Chaque message est écrit en effectuant un appel spécifique à partir de dans l’entrée de la méthode de votre applet de commande de traitement.

## <a name="the-stopproc-cmdlet"></a>L’applet de commande StopProc

Rubriques de cette section sont les suivantes :

- [Définition de l’applet de commande](#Defining-the-Cmdlet)

- [Définition des paramètres pour la Modification du système](#Defining-Parameters-for-System-Modification)

- [Substitution d’une méthode de traitement des entrées](#Overriding-an-Input-Processing-Method)

- [Écriture d’un Message détaillé](#Writing-a-Verbose-Message)

- [Écriture d’un Message de débogage](#Writing-a-Debug-Message)

- [Écriture d’un Message d’avertissement](#Writing-a-Warning-Message)

- [Écriture d’un Message de progression](#Writing-a-Progress-Message)

- [Exemple de code](#Code-Sample)

- [Définir les Types d’objets et la mise en forme](#Define-Object-Types-and-Formatting)

- [Création de l’applet de commande](#Building-the-Cmdlet)

- [Test de l’applet de commande](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Définition de l’applet de commande

La première étape de création de l’applet de commande est toujours l’applet de commande d’affectation de noms et déclaration de la classe .NET qui implémente l’applet de commande. Toute sorte de l’applet de commande peut écrire des notifications à l’utilisateur à partir de son entrée méthodes ; de traitement Par conséquent, en règle générale, vous pouvez nommer cette applet de commande à l’aide de n’importe quel verbe qui indique les modifications du système de l’applet de commande effectue. Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).

L’applet de commande Stop-Process est conçu pour modifier le système ; Par conséquent, le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) déclaration pour la classe .NET doit inclure le `SupportsShouldProcess` mot clé d’attribut et la valeur `true`.

Le code suivant est la définition de cette classe d’applet de commande Stop-Process. Pour plus d’informations sur cette définition, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Définition des paramètres pour la Modification du système

L’applet de commande Stop-Process définit trois paramètres : `Name`, `Force`, et `PassThru`. Pour plus d’informations sur la définition de ces paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

Voici la déclaration de paramètre pour l’applet de commande Stop-Process.

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement des entrées

Votre applet de commande doit substituer une méthode de traitement des entrées, il sera plus souvent [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Cette applet de commande Stop-Process remplace le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode de traitement d’entrée. Dans cette implémentation de l’applet de commande Stop-Process, les appels sont effectués pour écrire les messages documentés, les messages de débogage et les messages d’avertissement.

> [!NOTE]
> Pour plus d’informations sur la façon dont cette méthode appelle la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes, consultez [Création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Écriture d’un Message détaillé

Le [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) méthode est utilisée pour écrire des informations générales au niveau de l’utilisateur qui ne sont pas liées aux conditions d’erreur spécifique. L’administrateur système peut ensuite utiliser ces informations pour continuer à traiter d’autres commandes. En outre, toute information enregistrée à l’aide de cette méthode doit être localisée en fonction des besoins.

Le code suivant à partir de cette applet de commande Stop-Process présente deux appels à la [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) méthode à partir de la substitution de la [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Écriture d’un Message de débogage

Le [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) méthode est utilisée pour écrire des messages de débogage qui peuvent être utilisées pour résoudre les problèmes de l’opération de l’applet de commande. L’appel est effectué à partir d’une méthode de traitement des entrées.

> [!NOTE]
> Windows PowerShell définit également un `Debug` paramètre qui présente à la fois détaillé et les informations de débogage. Si votre applet de commande prend en charge ce paramètre, il n’a pas besoin d’appeler [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) dans le même code qui appelle [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

Les deux sections de code à partir de l’applet de commande Stop-Process exemple suivantes montrent des appels à la [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) méthode à partir de la substitution de la [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).

Ce message de débogage est écrite immédiatement avant [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) est appelée.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Ce message de débogage est écrite immédiatement avant [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) est appelée.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell achemine automatiquement les [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) appels à l’infrastructure de suivi et les applets de commande. Ainsi, les appels de méthode à suivre pour l’application d’hébergement, un fichier ou un débogueur sans devoir effectuer tout travail de développement supplémentaire au sein de l’applet de commande. L’entrée de ligne de commande suivante implémente une opération de suivi.

**PS > expression de trace stop-Process-fichier proc.log-le bloc-notes de commande stop-Process**

## <a name="writing-a-warning-message"></a>Écriture d’un Message d’avertissement

Le [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) méthode est utilisée pour écrire un avertissement lorsque l’applet de commande est sur le point d’effectuer une opération qui peut avoir un résultat d’inattendu, par exemple, en remplaçant un fichier en lecture seule.

Le code suivant à partir de l’applet de commande Stop-Process exemple illustre l’appel à la [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) méthode à partir de la substitution de la [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Écriture d’un Message de progression

Le [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) est utilisé pour écrire des messages de progression lorsque les opérations de l’applet de commande prennent un certain temps. Un appel à [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) transmet un [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) objet qui est envoyé à l’application d’hébergement pour le rendu à l’utilisateur.

> [!NOTE]
> Cette applet de commande Stop-Process n’inclut pas d’un appel à la [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) (méthode).

Le code suivant est un exemple d’un message de progression écrit par une applet de commande qui tente de copier un élément.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Exemple de code

Pour l’ensemble C# exemple de code, consultez [StopProcessSample02 exemple](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Définir les Types d’objets et la mise en forme

Windows PowerShell passe les informations entre les applets de commande à l’aide d’objets .NET. Par conséquent, une applet de commande devez définir son propre type, ou l’applet de commande peut étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou en étendant les types existants, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Création de l’applet de commande

Après l’implémentation d’une applet de commande, il doit être enregistré avec Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’inscription des applets de commande, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite avec Windows PowerShell, vous pouvez le tester en l’exécutant sur la ligne de commande. Testons l’applet de commande Stop-Process exemple. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- L’entrée de ligne de commande suivante utilise Stop-Process pour arrêter le processus nommé « NOTEPAD », fournissent des notifications détaillées et imprimer les informations de débogage.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

La sortie suivante s’affiche.

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a>Voir aussi

[Créer une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md)

[Comment créer une applet de commande Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Extension des Types d’objets et mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
