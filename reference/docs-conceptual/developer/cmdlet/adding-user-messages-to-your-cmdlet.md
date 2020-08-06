---
title: Ajout de messages utilisateur à votre applet de commande | Microsoft Docs
ms.date: 09/13/2016
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
ms.openlocfilehash: 9e324058401bc979d8ac8c23690ca86beaa67fd1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782461"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Ajout de messages utilisateur à votre applet de commande

Les applets de commande peuvent écrire plusieurs types de messages qui peuvent être affichés à l’utilisateur par le runtime Windows PowerShell. Ces messages incluent les types suivants :

- Messages détaillés qui contiennent des informations générales sur l’utilisateur.

- Déboguez les messages qui contiennent des informations de dépannage.

- Messages d’avertissement qui contiennent une notification indiquant que l’applet de commande est sur le lieu d’effectuer une opération qui peut avoir des résultats inattendus.

- Les messages du rapport de progression qui contiennent des informations sur la quantité de travail effectuée par l’applet de commande lors de l’exécution d’une opération qui prend beaucoup de temps.

Il n’existe aucune limite quant au nombre de messages que votre applet de commande peut écrire ou au type de messages que votre applet de commande écrit. Chaque message est écrit en effectuant un appel spécifique dans la méthode de traitement d’entrée de votre applet de commande.

## <a name="defining-the-cmdlet"></a>Définition de l’applet de commande

La première étape de la création des applets de commande consiste toujours à nommer l’applet de commande et à déclarer la classe .NET qui implémente l’applet de commande. Tout type d’applet de commande peut écrire des notifications utilisateur à partir de ses méthodes de traitement d’entrée. ainsi, en général, vous pouvez nommer cette applet de commande à l’aide de n’importe quel verbe qui indique les modifications système effectuées par l’applet de commande. Pour plus d’informations sur les verbes d’applet de commande approuvés, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.

L’applet de commande Stop-proc est conçue pour modifier le système. par conséquent, la Déclaration [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) pour la classe .net doit inclure le `SupportsShouldProcess` mot clé Attribute et avoir la valeur `true` .

Le code suivant est la définition de cette classe d’applet de commande Stop-proc. Pour plus d’informations sur cette définition, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Définition des paramètres pour la modification du système

L’applet de commande Stop-proc définit trois paramètres : `Name` , `Force` et `PassThru` . Pour plus d’informations sur la définition de ces paramètres, consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

Voici la déclaration du paramètre pour l’applet de commande Stop-proc.

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

## <a name="overriding-an-input-processing-method"></a>Substitution d’une méthode de traitement d’entrée

Votre applet de commande doit remplacer une méthode de traitement d’entrée, le plus souvent, [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)de commande. ProcessRecord. Cette applet de commande Stop-proc remplace la méthode de traitement d’entrée [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) de commande. ProcessRecord. Dans cette implémentation de l’applet de commande Stop-proc, des appels sont effectués pour écrire des messages détaillés, des messages de débogage et des messages d’avertissement.

> [!NOTE]
> Pour plus d’informations sur la façon dont cette méthode appelle les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , consultez [création d’une applet de commande qui modifie le système](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Écriture d’un message détaillé

La méthode [System. Management. Automation. applet de commande. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) est utilisée pour écrire des informations générales au niveau de l’utilisateur qui ne sont pas liées à des conditions d’erreur spécifiques. L’administrateur système peut ensuite utiliser ces informations pour continuer à traiter d’autres commandes. En outre, toutes les informations écrites à l’aide de cette méthode doivent être localisées en fonction des besoins.

Le code suivant de cette applet de commande Stop-proc montre deux appels à la méthode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Écriture d’un message de débogage

La méthode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) est utilisée pour écrire des messages de débogage qui peuvent être utilisés pour dépanner le fonctionnement de l’applet de commande. L’appel est effectué à partir d’une méthode de traitement d’entrée.

> [!NOTE]
> Windows PowerShell définit également un `Debug` paramètre qui présente des informations détaillées et de débogage. Si votre applet de commande prend en charge ce paramètre, il n’est pas nécessaire d’appeler [System. Management. Automation. applet de commande. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) dans le même code qui appelle [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)de commande. WriteVerbose.

Les deux sections de code suivantes de l’exemple d’applet de commande Stop-proc affichent les appels à la méthode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

Ce message de débogage est écrit juste avant l’appel de [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de commande. ShouldProcess.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Ce message de débogage est écrit juste avant l’appel de [System. Management. Automation. applet de commande. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell achemine automatiquement les appels [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) de commande. WriteDebug vers l’infrastructure de suivi et les applets de commande. Cela permet aux appels de méthode d’être suivis à l’application d’hébergement, à un fichier ou à un débogueur sans que vous ayez à effectuer d’autres tâches de développement dans l’applet de commande. L’entrée de ligne de commande suivante implémente une opération de suivi.

**PS> trace-expression Stop-proc-file proc. log-Command Stop-Process Notepad**

## <a name="writing-a-warning-message"></a>Écriture d’un message d’avertissement

La méthode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) est utilisée pour écrire un avertissement lorsque l’applet de commande est sur le paragraphe d’effectuer une opération qui peut avoir un résultat inattendu, par exemple en remplaçant un fichier en lecture seule.

Le code suivant de l’exemple d’applet de commande Stop-proc montre l’appel à la méthode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) à partir de la substitution de la méthode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Écriture d’un message de progression

[System. Management. Automation. applet de commande. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) est utilisé pour écrire des messages de progression lorsque l’exécution des opérations d’applet de commande prend un certain temps. Un appel à [System. Management. Automation. applet de commande. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passe un objet [System. Management. Automation. ProgressRecord](/dotnet/api/System.Management.Automation.ProgressRecord) qui est envoyé à l’application d’hébergement pour un rendu à l’utilisateur.

> [!NOTE]
> Cette applet de commande Stop-proc n’inclut pas d’appel à la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) de commande. WriteProgress.

Le code suivant est un exemple de message de progression écrit par une applet de commande qui tente de copier un élément.

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

Pour obtenir l’exemple de code C# complet, consultez [exemple StopProcessSample02](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Définir les types d’objets et la mise en forme

Windows PowerShell transmet des informations entre les applets de commande à l’aide d’objets .NET. Par conséquent, une applet de commande peut avoir besoin de définir son propre type, ou l’applet de commande peut avoir besoin d’étendre un type existant fourni par une autre applet de commande. Pour plus d’informations sur la définition de nouveaux types ou l’extension de types existants, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Génération de l’applet de commande

Après l’implémentation d’une applet de commande, celle-ci doit être inscrite auprès de Windows PowerShell par le biais d’un composant logiciel enfichable Windows PowerShell. Pour plus d’informations sur l’enregistrement des applets de commande, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test de l’applet de commande

Lorsque votre applet de commande a été inscrite auprès de Windows PowerShell, vous pouvez la tester en l’exécutant sur la ligne de commande. Nous allons tester l’exemple d’applet de commande Stop-proc. Pour plus d’informations sur l’utilisation des applets de commande à partir de la ligne de commande, consultez le [prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- L’entrée de ligne de commande suivante utilise Stop-proc pour arrêter le processus nommé « NOTEPAD », fournir des notifications détaillées et imprimer les informations de débogage.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

    La sortie suivante apparaît.

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

[Comment créer une applet de commande Windows PowerShell](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
